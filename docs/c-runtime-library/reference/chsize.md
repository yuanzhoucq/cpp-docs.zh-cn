---
title: "_chsize | Microsoft Docs"
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
  - "_chsize"
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
  - "_chsize"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_chsize 函数"
  - "chsize 函数"
  - "文件 [C++], 更改大小"
  - "大小"
  - "大小, 更改文件"
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _chsize
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

更改文件的大小。  一种较为安全有效的版本；请参见[\_chsize\_s](../../c-runtime-library/reference/chsize-s.md)。  
  
## 语法  
  
```  
int _chsize(   
   int fd,  
   long size   
);  
```  
  
#### 参数  
 `fd`  
 引用开启文件的描述符。  
  
 `size`  
 文件的新长度（以字节为单位）。  
  
## 返回值  
 如果更改成功，文件大小，`_chsize`返回值 0。  返回 \-1 指示错误：如果指定的文件锁定访问，`errno`为`EACCES`，如果指定的文件改为只读或说明符无效，为`EBADF`，如果设备没有留出空间，为`ENOSPC`，或如果 `size` 小于零，为`EINVAL`。  
  
 有关这些内容的详细信息以及其他返回代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_chsize`函数扩展或截断文件与 `fd` 为 `size`的指定长度。  文件绑定中打开允许写入的模式。  null 字符 \(“\\ 0 "\) 追加，如果文件是扩展。  如果文件被截断，缩短从文件的结尾的所有数据。文件的原始长度的丢失。  
  
 此函数验证其参数。  如果 `size` 小于零或一个 `fd` 文件错误描述符，无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_chsize`|\<io.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_chsize.c  
// This program uses _filelength to report the size  
// of a file before and after modifying it with _chsize.  
  
#include <io.h>  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <share.h>  
  
int main( void )  
{  
   int fh, result;  
   unsigned int nbytes = BUFSIZ;  
  
   // Open a file   
   if( _sopen_s( &fh, "data", _O_RDWR | _O_CREAT, _SH_DENYNO,  
                 _S_IREAD | _S_IWRITE ) == 0 )  
   {  
      printf( "File length before: %ld\n", _filelength( fh ) );  
      if( ( result = _chsize( fh, 329678 ) ) == 0 )  
         printf( "Size successfully changed\n" );  
      else  
         printf( "Problem in changing the size\n" );  
      printf( "File length after:  %ld\n", _filelength( fh ) );  
      _close( fh );  
   }  
}  
```  
  
  **以前文件长度：0**  
**成功改变大小**  
**后文件长度：329678**   
## .NET Framework 等效项  
  
-   [System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)  
  
-   [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_sopen、\_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)