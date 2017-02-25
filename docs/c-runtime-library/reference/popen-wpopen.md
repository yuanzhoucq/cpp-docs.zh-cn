---
title: "_popen、_wpopen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_popen"
  - "_wpopen"
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
  - "tpopen"
  - "popen"
  - "wpopen"
  - "_popen"
  - "_wpopen"
  - "_tpopen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_popen 函数"
  - "_tpopen 函数"
  - "_wpopen 函数"
  - "管道, 创建"
  - "popen 函数"
  - "tpopen 函数"
  - "wpopen 函数"
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _popen、_wpopen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建一个管道并执行命令。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
  
      FILE *_popen(  
const char *command,  
const char *mode   
);  
FILE *_wpopen(  
const wchar_t *command,  
const wchar_t *mode   
);  
```  
  
#### 参数  
 *命令*  
 要执行的命令。  
  
 *mode*  
 返回流的模式。  
  
## 返回值  
 返回与已创建的管道的一端关联的流。  管道的另一端与给定的命令的标准输入或标准输出关联。  函数返回**NULL**错误。  如果错误是无效参数，例如，如果 *命令* 或 *模式* 是空指针或 *模式* 不是有效的模式，`errno` 设置为 `EINVAL`。  参见有效模式的"备注"部分。  
  
 有关这些内容以及其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_popen` 函数创建一个管道，并异步执行一个有指定字符串 *command*的命令处理器的给定的副本。  字符串 *模式* 指定请求的访问类型，如下所示。  
  
 **"r"**  
 使用返回的流，调用进程可以读取给定的命令的标准输出。  
  
 **“w”**  
 使用返回的流，调用进程可以写入给定的命令的标准输入。  
  
 **"b"**  
 在二进制模式下打开。  
  
 **"t"**  
 在文本模式下打开。  
  
> [!NOTE]
>  如果在窗口程序中使用，`_popen` 函数返回会导致程序停止无限期地响应的无效文件指针。  `_popen` 在控制台应用程序中正常工作。  若要创建重定向输入和输出的 Windows 应用程序，请参见 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)]的 [创建重定向的输入和输出的子进程](http://msdn.microsoft.com/library/windows/desktop/ms682499)。  
  
 `_wpopen` 是 `_popen` 的宽字符版本；`_wpopen` 的 *路径*参数是宽字符字符串。  否则`_wpopen` 和 `_popen` 行为相同。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tpopen`|`_popen`|`_popen`|`_wpopen`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_popen`|\<stdio.h\>|  
|`_wpopen`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_popen.c  
/* This program uses _popen and _pclose to receive a   
 * stream of text from a system process.  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
  
   char   psBuffer[128];  
   FILE   *pPipe;  
  
        /* Run DIR so that it writes its output to a pipe. Open this  
         * pipe with read text attribute so that we can read it   
         * like a text file.   
         */  
  
   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )  
      exit( 1 );  
  
   /* Read pipe until end of file, or an error occurs. */  
  
   while(fgets(psBuffer, 128, pPipe))  
   {  
      printf(psBuffer);  
   }  
  
   /* Close pipe and print return value of pPipe. */  
   if (feof( pPipe))  
   {  
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );  
   }  
   else  
   {  
     printf( "Error: Failed to read the pipe to the end.\n");  
   }  
}  
```  
  
## 示例输出  
 此输出假定，当前目录中只有一个文件有.c文件扩展名。  
  
```  
 Volume in drive C is CDRIVE  
 Volume Serial Number is 0E17-1702  
  
 Directory of D:\proj\console\test1  
  
07/17/98  07:26p                   780 popen.c  
               1 File(s)            780 bytes  
                             86,597,632 bytes free  
  
Process returned 0  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_pclose](../../c-runtime-library/reference/pclose.md)   
 [\_pipe](../../c-runtime-library/reference/pipe.md)