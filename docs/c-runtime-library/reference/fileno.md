---
title: "_fileno | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fileno"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_fileno"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文件句柄 [C++], 从流中获取"
  - "fileno 函数"
  - "_fileno 函数"
  - "流, 获取文件句柄"
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _fileno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取与流有关的文件描述符。  
  
## 语法  
  
```  
int _fileno(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE`结构的指针。  
  
## 返回值  
 `_fileno` 返回文件描述符号。  无错误返回。  如果 `stream` 没有指定一个开启的文件，则结果是未定义的。  如果流为 `NULL`，\_`fileno` 将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果执行允许继续，这个函数返回 \-1并设定`errno` 到 `EINVAL` 。  
  
 有关这些属性和其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
> [!NOTE]
>  如果 `stdout` 或 `stderr` 与输出流没有联系 \(例如，在没有控制台窗口的 Windows 应用程序\)，文件说明符返回的是 \-2。  在以前版本，返回的文件说明符为 \-1。  此更改允许应用程序从错误中区分此条件。  
  
## 备注  
 `_fileno` 程序返回与当前 `stream`有联系的文件说明符。  该程序被实现既作为一个函数也作为一个宏。  有关选择和实现信息，请参见 [在函数和宏中选择](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_fileno`|\<stdio.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fileno.c  
// This program uses _fileno to obtain  
// the file descriptor for some standard C streams.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );  
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );  
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );  
}  
```  
  
  **stdin 的文件说明符为是 0**  
**StdOut的文件说明符为 1**  
**stderr 的文件说明符为 2**   
## .NET Framework 等效项  
 [System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_fdopen、\_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [\_filelength、\_filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)