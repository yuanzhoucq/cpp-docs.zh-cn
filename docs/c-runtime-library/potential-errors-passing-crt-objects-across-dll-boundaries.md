---
title: "跨 DLL 边界传递 CRT 对象时可能的错误 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "DLL 冲突 [C++]"
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 跨 DLL 边界传递 CRT 对象时可能的错误
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当您传递 C\# 时 \(CRT\) 运行时对象 \(如文件句柄、区域设置和环境变量拖入或拖出 DLL \(跨 DLL 边界的函数调用之外\)，可能发生意外，则 调入 DLL 的文件，使用 CRT 库的不同的副本。  
  
 相关问题发生，当您分配内存 \(显式使用 `new` 或 `malloc`或隐式用 `strdup`，`strstreambuf::str`，依此类推\) 时传递在将的版本 DLL 边界的指针。  如果 DLL及其用户使用 CRT 库的不同副本，这可能会导致内存存取冲突或堆栈损坏。  
  
 在调试诸如之类，对此问题的另一种症状可能属于输出窗口中的错误：  
  
 HEAP\[\]: 指定的地址无效 RtlValidateHeap \(\#，\#\)。  
  
## 原因  
 CRT 库的每个副本都具有一个不同的状态。  同样，CRT 对象 如文件句柄，环境变量，并且设置区域分配给这些对象或设置 CRT 的仅复制是有效的。  当 DLL 及其用户使用 CRT 库的不同时复制，在另一侧无法通过跨 DLL 边界的对象预期方式会选取这些 CRT 和正确。  
  
 此外，CRT 库，因为的每个副本都具有它自己堆管理器中，将存在其中一个 CRT 库中并将跨 CRT 库的其他副本上发布的 DLL 边界的指针为堆损坏的一个可能的原因。  
  
 如果您设计的 DLL，以便跨边界传递对象 CRT 或分配内存并期望它在释放 DLL 外，则限制 DLL 用户使用 CRT 库的同一副本与 DLL。  只有当两种链接。CRT DLL 的版本相同，其 DLL 和用户使用 CRT 库的相同副本。  这可能是个问题，则与 DLL 的 Visual C\+\+ 5.0 混合由 Visual C\+\+ 4.1 之前生成或生成的应用程序。  由于 Visual C\+\+ 4.1 使用的 CRT 库的 DLL 版本。msvcrt40.dll，并且 Visual 对象使用的版本是 msvcrt.dll 5.0，不能生成应用程序使用 CRT 库的同一副本。这些 DLL。  
  
 但是，也存在例外情况。  在美国英语版本和 Windows 2000 操作本地化版本，如msvcrt40.dll \(版本 4.20\) 转发器在德国、法国、捷克版本中提供。  结果即使与 DLL 链接，msvcrt40.dll，其用户msvcrt.dll仍使用 CRT 库的相同副本，因为所有对 msvcrt40.dll 转到 msvcrt.dll。  
  
 但是 msvcrt40.dll 此转发器版本不可用在 Windows 2000 某些本地化版本，如日语和朝鲜语，中文支持。  因而，如果应用程序面向以下操作系统，需要为获取不依赖于 DLL msvcrt40.dll 的已升级的版本或修改应用程序不依赖于使用 CRT 库的相同副本。  如果您开发的 DLL，这意味着重新生成它使用 Visual C\+\+ 4.2 或更高版本。  如果这是第三方 DLL，需要与升级的供应商联系。  
  
 请注意此转发器 DLL 版本 msvcrt40.dll \(版本 4.20\) 无法重新发布。  
  
## 示例  
  
### 说明  
 此示例传递跨 DLL 边界的文件句柄。  
  
 DLL 和 .exe 文件使用 \/MD 生成，因此，它们共享 CRT 的一个副本。  
  
 如果您重新生成使用 \/MT，以便使用 CRT 的单独副本，运行生成的 test1Main.exe 导致访问冲突。  
  
### 代码  
  
```  
// test1Dll.cpp  
// compile with: /MD /LD  
#include <stdio.h>  
__declspec(dllexport) void writeFile(FILE *stream)  
{  
   char   s[] = "this is a string\n";  
   fprintf( stream, "%s", s );  
   fclose( stream );  
}  
```  
  
### 代码  
  
```  
// test1Main.cpp  
// compile with: /MD test1dll.lib  
#include <stdio.h>  
#include <process.h>  
void writeFile(FILE *stream);  
  
int main(void)  
{  
   FILE  * stream;  
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );  
   writeFile(stream);  
   system( "type fprintf.out" );  
}  
```  
  
### Output  
  
```  
this is a string  
```  
  
## 示例  
  
### 说明  
 此示例传递跨 DLL 边界的环境变量。  
  
### 代码  
  
```  
// test2Dll.cpp  
// compile with: /MT /LD  
#include <stdio.h>  
#include <stdlib.h>  
  
__declspec(dllexport) void readEnv()  
{  
   char *libvar;  
   size_t libvarsize;  
  
   /* Get the value of the MYLIB environment variable. */   
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );  
  
   if( libvar != NULL )  
      printf( "New MYLIB variable is: %s\n", libvar);  
   else  
      printf( "MYLIB has not been set.\n");  
   free( libvar );  
}  
```  
  
### 代码  
  
```  
// test2Main.cpp  
// compile with: /MT /link test2dll.lib  
#include <stdlib.h>  
#include <stdio.h>  
  
void readEnv();  
  
int main( void )  
{  
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );  
   readEnv();  
}  
```  
  
### Output  
  
```  
MYLIB has not been set.  
```  
  
 如果 DLL 和 .exe 文件生成与 \/MD，以便只使用 CRT 的复制，程序运行成功并且产生以下输出：  
  
```  
New MYLIB variable is: c:\mylib;c:\yourlib  
```  
  
## 请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)