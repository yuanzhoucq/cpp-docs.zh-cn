---
title: "ftell、_ftelli64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ftelli64"
  - "ftell"
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
  - "_ftelli64"
  - "ftell"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftelli64 函数"
  - "文件指针 [C++]"
  - "文件指针 [C++], 获取当前位置"
  - "ftell 函数"
  - "ftelli64 函数"
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# ftell、_ftelli64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Gets the current position of a file pointer.  
  
## 语法  
  
```  
long ftell(   
   FILE *stream   
);  
__int64 _ftelli64(   
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 Target `FILE` structure.  
  
## 返回值  
 `ftell` and `_ftelli64` return the current file position.  The value returned by `ftell` and `_ftelli64` may not reflect the physical byte offset for streams opened in text mode, because text mode causes carriage return–linefeed translation.  Use `ftell` with `fseek`or`_ftelli64`with`_fseeki64` to return to file locations correctly.  On error, `ftell`and`_ftelli64` invoke the invalid parameter handler, as described in [参数验证](../../c-runtime-library/parameter-validation.md).  If execution is allowed to continue, these functions return –1L and set `errno` to one of two constants, defined in ERRNO.H.  The `EBADF` constant means the `stream` argument is not a valid file pointer value or does not refer to an open file.  `EINVAL` means an invalid `stream` argument was passed to the function.  On devices incapable of seeking \(such as terminals and printers\), or when `stream` does not refer to an open file, the return value is undefined.  
  
 有关这些内容的详细信息以及其他返回代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 The `ftell` and `_ftelli64`functions retrieve the current position of the file pointer \(if any\) associated with `stream`*.*The position is expressed as an offset relative to the beginning of the stream.  
  
 Note that when a file is opened for appending data, the current file position is determined by the last I\/O operation, not by where the next write would occur.  For example, if a file is opened for an append and the last operation was a read, the file position is the point where the next read operation would start, not where the next write would start.\(When a file is opened for appending, the file position is moved to end of file before any write operation.\)If no I\/O operation has yet occurred on a file opened for appending, the file position is the beginning of the file.  
  
 In text mode, CTRL\+Z is interpreted as an end\-of\-file character on input.  In files opened for reading\/writing, `fopen` and all related routines check for a CTRL\+Z at the end of the file and remove it if possible.  这是因为使用 `ftell` 和 `fseek`的结合或`_ftelli64` 和 `_fseeki64`的结合，在以 CTRL\+Z 结尾的文件中移动时，可能导致 `ftell` 或 `_ftelli64` 在文件末尾错误运行。  
  
 该函数在运行期间锁定调用线程，因此线程安全的。  有关非固定版本，请参见 `_ftell_nolock`。  
  
## 要求  
  
|功能|必需的标头|可选标头|  
|--------|-----------|----------|  
|`ftell`|\<stdio.h\>|\<errno.h\>|  
|`_ftelli64`|\<stdio.h\>|\<errno.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_ftell.c  
// This program opens a file named CRT_FTELL.C  
// for reading and tries to read 100 characters. It  
// then uses ftell to determine the position of the  
// file pointer and displays this position.  
  
#include <stdio.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long position;  
   char list[100];  
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )  
   {  
      // Move the pointer by reading data:   
      fread( list, sizeof( char ), 100, stream );  
      // Get position after read:   
      position = ftell( stream );  
      printf( "Position after trying to read 100 bytes: %ld\n",  
              position );  
      fclose( stream );  
   }  
}  
```  
  
  **Position after trying to read 100 bytes: 100**   
## .NET Framework 等效项  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)   
 [fseek、\_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_lseek、\_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)