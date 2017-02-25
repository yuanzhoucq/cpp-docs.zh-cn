---
title: "_fullpath、_wfullpath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fullpath"
  - "_wfullpath"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wfullpath"
  - "fullpath"
  - "_wfullpath"
  - "_fullpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fullpath 函数"
  - "_wfullpath 函数"
  - "绝对路径"
  - "fullpath 函数"
  - "相对文件路径"
  - "wfullpath 函数"
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _fullpath、_wfullpath
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为指定的相对路径名创建绝对或完整路径名。  
  
## 语法  
  
```  
char *_fullpath(   
   char *absPath,  
   const char *relPath,  
   size_t maxLength   
);  
wchar_t *_wfullpath(   
   wchar_t *absPath,  
   const wchar_t *relPath,  
   size_t maxLength   
);  
```  
  
#### 参数  
 `absPath`  
 指向包含绝对或完整路径名的缓冲区的指针或空指针 。  
  
 `relPath`  
 相对路径名。  
  
 `maxLength`  
 绝对路径名缓冲区 \(`absPath`\) 的最大长度。  `_fullpath` 长度以字节为单位，但 `_wfullpath`以宽字符为单位 \(`wchar_t`\) 。  
  
## 返回值  
 这些函数每个返回指向包含绝对路径名 \(`absPath`\) 的缓冲区的指针。  如果出现错误 \(例如，在中，如果在 `relPath` 中传递的值包含无效或无法找到的驱动器号，或者，如果创建的绝对路径名 \(`absPath`\) 的长度大于 `maxLength`\)， 函数返回 `NULL`。  
  
## 备注  
 `_fullpath` 函数展开 `relPath` 的相对路径名为完全限定或绝对路径并在 `absPath`中存储此名称*。*如果 `absPath`是NULL，`malloc` 用于分配足够的长度的缓冲区存放路径名。  释放此缓冲区为调用方的职责。  相对路径名称指定从其他位置到当前位置的路径 \(如当前工作目录：“."\)。  绝对路径名是从文件系统根目录到指定位置的完整路径的相对路径名称的扩展。  与 `_makepath`不同，`_fullpath` 可以用于获取相对路径的绝对路径名 \(`relPath`\)，路径名包含".\/" 或 "..\/" 。  
  
 例如，使用C 运行时程序，应用程序必须包含例程声明的头文件。  每个包含声明的头文件引用文件的位置的相对路径 \(从应用程序的工作目录开始\):  
  
```  
#include <stdlib.h>  
```  
  
 文件的绝对路径 \(实际的文件系统位置\) 可能是：  
  
```  
\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h  
```  
  
 `_fullpath` 它们自动处理合适的多字节字符串参数，根据当前使用的多字节代码页识别多字节字符序列.  `_wfullpath` 是 `_fullpath`的宽字符版本；`_wfullpath`  的字符串参数是宽字符字符串。  `_wfullpath` 和 `_fullpath`  具有相同的行为，但 `_wfullpath`  不处理多字节字符字符串。  
  
 如果 `_DEBUG`  和 `_CRTDBG_MAP_ALLOC`  都被定义，调试内存分配时，对 `_fullpath` 和 `_wfullpath` 的调用被替换为 `_fullpath_dbg` 和 `_wfullpath_dbg` 的调用。  有关更多信息，请参见 [\_fullpath\_dbg，\_wfullpath\_dbg](../../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)。  
  
 如果 `maxlen` 小于或等于零，此函数调用无效参数处理程序，就如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `NULL`。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tfullpath`|`_fullpath`|`_fullpath`|`_wfullpath`|  
  
 如果 `absPath` 缓冲区是 `NULL`，`_fullpath` 将调用 [malloc](../../c-runtime-library/reference/malloc.md) 分配缓冲区并忽略 `maxLength` 参数。  释放此缓冲区为相应的调用方的职责 \(使用 [free](../../c-runtime-library/reference/free.md)\) 。  如果 `relPath` 参数指定磁盘驱动器，驱动器的当前目录将与路径合并。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fullpath`|\<stdlib.h\>|  
|`_wfullpath`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fullpath.c  
// This program demonstrates how _fullpath  
// creates a full path from a partial path.  
  
#include <stdio.h>  
#include <conio.h>  
#include <stdlib.h>  
#include <direct.h>  
  
void PrintFullPath( char * partialPath )  
{  
   char full[_MAX_PATH];  
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )  
      printf( "Full path is: %s\n", full );  
   else  
      printf( "Invalid path\n" );  
}  
  
int main( void )  
{  
   PrintFullPath( "test" );  
   PrintFullPath( "\\test" );  
   PrintFullPath( "..\\test" );  
}  
```  
  
  **完整路径为：C:\\Documents and Settings\\user\\My Documents\\test**  
**完整路径为：C:\\test**  
**完整路径为：C:\\Documents and settings\\user\\test**   
## .NET Framework 等效项  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdcwd、\_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [\_makepath、\_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [\_splitpath、\_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)