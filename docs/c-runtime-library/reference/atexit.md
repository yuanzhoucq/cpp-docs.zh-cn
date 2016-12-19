---
title: "atexit | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "atexit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "atexit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "atexit 函数"
  - "处理, at exit"
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atexit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在退出时处理指定的函数。  
  
## 语法  
  
```  
int atexit(  
   void (__cdecl *func )( void )  
);  
```  
  
#### 参数  
 `func`  
 被调用的函数。  
  
## 返回值  
 如果成功 `atexit` 返回 0，如果发生错误，返回一个非零值，。  
  
## 备注  
 当程序正常终止时，`atexit` 函数传递 \(`func`\) 的地址来调用。  成功调用 `atexit` 的函数注册，执行后后进先出函数 \(LIFO\) 的顺序。  函数传递给 `atexit` 不能带参数。  `atexit` 和 `_onexit` 使用堆保留函数注册。  因此，注册可以函数的数目由堆内存只限制。  
  
 在 `atexit` 函数的代码中不应包含任何依赖于刚被卸载的 DLL ，当调用 `atexit` 函数时。  
  
 若要生成一个符合 ANSI 的应用程序，请使用 ANSI 标准 `atexit` 函数 \(而不是相同的 `_onexit` 函数。\)  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`atexit`|\<stdlib.h\>|  
  
## 示例  
 当调用 `atexit` 时，此程序推入四个执行函数到栈上。  在程序退出，这些程序执行后进先出顺序。  
  
```  
// crt_atexit.c  
#include <stdlib.h>  
#include <stdio.h>  
  
void fn1( void ), fn2( void ), fn3( void ), fn4( void );  
  
int main( void )  
{  
   atexit( fn1 );  
   atexit( fn2 );  
   atexit( fn3 );  
   atexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
void fn1()  
{  
   printf( "next.\n" );  
}  
  
void fn2()  
{  
   printf( "executed " );  
}  
  
void fn3()  
{  
   printf( "is " );  
}  
  
void fn4()  
{  
   printf( "This " );  
}  
```  
  
  **这首先执行。**  
**这接下来执行。**   
## .NET Framework 等效项  
 [System::Diagnostics::Process::Exited](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit、\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)