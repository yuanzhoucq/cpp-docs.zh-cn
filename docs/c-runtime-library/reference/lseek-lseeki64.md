---
title: "_lseek、_lseeki64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_lseeki64"
  - "_lseek"
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
  - "_lseeki64"
  - "_lseek"
  - "lseeki64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_lseek 函数"
  - "_lseeki64 函数"
  - "文件指针 [C++], 移动"
  - "lseek 函数"
  - "lseeki64 函数"
  - "查找文件指针"
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _lseek、_lseeki64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将文件指针移到指定位置。  
  
## 语法  
  
```  
  
      long _lseek(  
   int fd,  
   long offset,  
   int origin   
);  
__int64 _lseeki64(  
   int fd,  
   __int64 offset,  
   int origin   
);  
```  
  
#### 参数  
 `fd`  
 引用开启文件的描述符。  
  
 *偏移量*  
 *原始*字节数。  
  
 *原始*  
 初始位置。  
  
## 返回值  
 `_lseek` 返回字节偏移量，从开头文件的新位置。  `_lseeki64` 返回在 64 位整数的偏移量。  函数返回 –1L 指示错误。  如果传递的参数无效，例如一个坏文件说明符或 *原始* 值无效或 *偏移所* 指定的位置是，在文件的开头，无效参数调用处理程序之前，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些功能将 `errno` 设置为 `EBADF`，并返回 \-1L。  在设备上不能查找 \(如运行和打印机\)，返回值是不确定的。  
  
 有关这些属性和其他错误代码的详细信息，请参阅 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_lseek` 函数移动了文件指针与 `fd` 到偏离*原点**偏移量* 为字节的新位置。  文件的下一操作在新位置。  *原点* 参数必须是下列常数之一，在 Stdio.h 定义。  
  
 `SEEK_SET`  
 文件名的开头。  
  
 `SEEK_CUR`  
 文件指针的当前位置。  
  
 `SEEK_END`  
 文件尾。  
  
 可以使用 `_lseek` 重新定位指针在文件中的任意位置或除文件外的末尾。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_lseek`|\<io.h\>|  
|`_lseeki64`|\<io.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_lseek.c  
/* This program first opens a file named lseek.txt.  
 * It then uses _lseek to find the beginning of the file,  
 * to find the current position in the file, and to find  
 * the end of the file.  
 */  
  
#include <io.h>  
#include <fcntl.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
int main( void )  
{  
   int fh;  
   long pos;               /* Position of file pointer */  
   char buffer[10];  
  
   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );  
  
   /* Seek the beginning of the file: */  
   pos = _lseek( fh, 0L, SEEK_SET );  
   if( pos == -1L )  
      perror( "_lseek to beginning failed" );  
   else  
      printf( "Position for beginning of file seek = %ld\n", pos );  
  
   /* Move file pointer a little */  
    _read( fh, buffer, 10 );  
  
   /* Find current position: */  
   pos = _lseek( fh, 0L, SEEK_CUR );  
   if( pos == -1L )  
      perror( "_lseek to current position failed" );  
   else  
      printf( "Position for current position seek = %ld\n", pos );  
  
   /* Set the end of the file: */  
   pos = _lseek( fh, 0L, SEEK_END );  
   if( pos == -1L )  
      perror( "_lseek to end failed" );  
   else  
      printf( "Position for end of file seek = %ld\n", pos );  
  
   _close( fh );  
}  
```  
  
## Input: crt\_lseek.c\_input  
  
```  
Line one.  
Line two.  
Line three.  
Line four.  
Line five.  
```  
  
## Output  
  
```  
Position for beginning of file seek = 0  
Position for current position seek = 10  
Position for end of file seek = 57  
```  
  
## 请参阅  
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [fseek、\_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_tell、\_telli64](../../c-runtime-library/reference/tell-telli64.md)