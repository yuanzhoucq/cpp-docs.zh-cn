---
title: "_read | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_read"
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
  - "_read"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_read 函数"
  - "数据 [C++], 读取"
  - "数据 [CRT]"
  - "文件 [C++], 读取"
  - "read 函数"
  - "读取数据 [C++]"
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _read
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Reads data from a file.  
  
## 语法  
  
```  
  
      int _read(  
   int fd,  
   void *buffer,  
   unsigned int count   
);  
```  
  
#### 参数  
 `fd`  
 File descriptor referring to the open file.  
  
 *buffer*  
 数据的存储位置。  
  
 *count*  
 Maximum number of bytes.  
  
## 返回值  
 \_**read** returns the number of bytes read, which might be less than *count* if there are fewer than *count* bytes left in the file or if the file was opened in text mode, in which case each carriage return–line feed \(CR\-LF\) pair is replaced with a single linefeed character.  Only the single linefeed character is counted in the return value.  The replacement does not affect the file pointer.  
  
 If the function tries to read at end of file, it returns 0.  If `fd` is invalid, the file is not open for reading, or the file is locked, the invalid parameter handler is invoked, as described in [参数验证](../../c-runtime-library/parameter-validation.md).  如果允许执行继续，则该函数返回\-1,并将`errno` 设置为 `EBADF`。  
  
 如果*buffer*是**NULL**，则调用无效参数处理程序。  If execution is allowed to continue, the function returns \-1 and `errno` is set to `EINVAL`.  
  
 For more information about this and other return codes, see [\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## 备注  
 The `_read` function reads a maximum of *count* bytes into *buffer* from the file associated with `fd`.  The read operation begins at the current position of the file pointer associated with the given file.  After the read operation, the file pointer points to the next unread character.  
  
 If the file was opened in text mode, the read terminates when `_read` encounters a CTRL\+Z character, which is treated as an end\-of\-file indicator.  Use [\_lseek](../../c-runtime-library/reference/lseek-lseeki64.md) to clear the end\-of\-file indicator.  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_read`|\<io.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_read.c  
/* This program opens a file named crt_read.txt  
 * and tries to read 60,000 bytes from  
 * that file using _read. It then displays the  
 * actual number of bytes read.  
 */  
  
#include <fcntl.h>      /* Needed only for _O_RDWR definition */  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
char buffer[60000];  
  
int main( void )  
{  
   int fh;  
   unsigned int nbytes = 60000, bytesread;  
  
   /* Open file for input: */  
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
      perror( "open failed on input file" );  
      exit( 1 );  
   }  
  
   /* Read in input: */  
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )  
      perror( "Problem reading file" );  
   else  
      printf( "Read %u bytes from file\n", bytesread );  
  
   _close( fh );  
}  
```  
  
## Input: crt\_read.txt  
  
```  
Line one.  
Line two.  
```  
  
## Output  
  
```  
Read 19 bytes from file  
```  
  
## 请参阅  
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_write](../../c-runtime-library/reference/write.md)