---
title: "fseek、_fseeki64 | Microsoft Docs"
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
  - "_fseeki64"
  - "fseek"
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
  - "fseek"
  - "_fseeki64"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fseeki64 函数"
  - "文件指针 [C++]"
  - "文件指针 [C++], 移动"
  - "fseek 函数"
  - "fseeki64 函数"
  - "查找文件指针"
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fseek、_fseeki64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Moves the file pointer to a specified location.  
  
## 语法  
  
```  
int fseek(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `offset`  
 Number of bytes from `origin`.  
  
 `origin`  
 Initial position.  
  
## 返回值  
 If successful, `fseek` and `_fseeki64` returns 0.  否则，它返回一个非零值。  On devices incapable of seeking, the return value is undefined.  If `stream` is a null pointer, or if `origin` is not one of allowed values described below, `fseek` and `_fseeki64` invoke the invalid parameter handler, as described in [参数验证](../../c-runtime-library/parameter-validation.md).  如果允许执行继续，则这些功能将 `EINVAL` 设置为 `errno` 并返回 \-1。  
  
## 备注  
 The `fseek` and `_fseeki64` functions moves the file pointer \(if any\) associated with `stream` to a new location that is `offset` bytes from `origin`*.*The next operation on the stream takes place at the new location.  On a stream open for update, the next operation can be either a read or a write.  The argument origin must be one of the following constants, defined in STDIO.H:  
  
 `SEEK_CUR`  
 Current position of file pointer.  
  
 `SEEK_END`  
 文件尾。  
  
 `SEEK_SET`  
 Beginning of file.  
  
 You can use `fseek` and `_fseeki64` to reposition the pointer anywhere in a file.  The pointer can also be positioned beyond the end of the file.  `fseek` and `_fseeki64`clears the end\-of\-file indicator and negates the effect of any prior `ungetc` calls against `stream`.  
  
 When a file is opened for appending data, the current file position is determined by the last I\/O operation, not by where the next write would occur.  If no I\/O operation has yet occurred on a file opened for appending, the file position is the start of the file.  
  
 For streams opened in text mode, `fseek` and `_fseeki64`have limited use, because carriage return–linefeed translations can cause `fseek` and `_fseeki64`to produce unexpected results.  The only `fseek` and `_fseeki64`operations guaranteed to work on streams opened in text mode are:  
  
-   Seeking with an offset of 0 relative to any of the origin values.  
  
-   Seeking from the beginning of the file with an offset value returned from a call to `ftell` when using `fseek`or `_ftelli64`when using`_fseeki64`.  
  
 Also in text mode, CTRL\+Z is interpreted as an end\-of\-file character on input.  In files opened for reading\/writing, `fopen` and all related routines check for a CTRL\+Z at the end of the file and remove it if possible.  这是因为使用 `fseek` 和 `ftell`或`_fseeki64` 和`_ftelli64`的结合, 在以 CTRL\+Z 结尾的文件中移动时，可能导致 `fseek` 或 `_fseeki64` 在文件末尾错误运行。  
  
 当打开 CRT 启动与字节顺序标记 \(BOM\) 的文件时，文件指针指向\(BOM\)尾 \(即在文件的实际内容的开头\)。  If you have to `fseek` to the beginning of the file, use `ftell` to get the initial position and `fseek` to it rather than to position 0.  
  
 This function locks out other threads during execution and is therefore thread\-safe.  有关非固定版本，请参见 [\_fseek\_nolock、\_fseeki64\_nolock](../../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fseek`|\<stdio.h\>|  
|`_fseeki64`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fseek.c  
// This program opens the file FSEEK.OUT and  
// moves the pointer to the file's beginning.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[81];  
   int  result;  
  
   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )  
   {  
      printf( "The file fseek.out was not opened\n" );  
      return -1;  
   }  
   fprintf( stream, "The fseek begins here: "  
                    "This is the file 'fseek.out'.\n" );  
   result = fseek( stream, 23L, SEEK_SET);  
   if( result )  
      perror( "Fseek failed" );  
   else  
   {  
      printf( "File pointer is set to middle of first line.\n" );  
      fgets( line, 80, stream );  
      printf( "%s", line );  
    }  
   fclose( stream );  
}  
```  
  
  **File pointer is set to middle of first line.**  
**This is the file 'fseek.out'.**   
## .NET Framework 等效项  
  
-   [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
-   [System::IO::FileStream::Seek](https://msdn.microsoft.com/en-us/library/system.io.filestream.seek.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [ftell、\_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [\_lseek、\_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)