---
title: "_tell、_telli64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_telli64"
  - "_tell"
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
  - "tell"
  - "telli64"
  - "_telli64"
  - "_tell"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tell 函数"
  - "_telli64 函数"
  - "文件指针 [C++]"
  - "文件指针 [C++], 获取"
  - "tell 函数"
  - "telli64 函数"
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _tell、_telli64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取文件指针点的位置。  
  
## 语法  
  
```  
long _tell(  
   int handle  
);  
__int64 _telli64(  
   int handle   
);  
```  
  
#### 参数  
 `handle`  
 引用打开文件的描述符。  
  
## 返回值  
 文件指针的当前位置。  在设备上不能查找，返回值是不确定的。  
  
 返回值 \-1L 指示一个错误。  如果 `handle` 是无效的文件说明符，此函数调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些功能将 `errno` 设置为 `EBADF`，并返回 \-1L.。  
  
 有关这个，其他和返回代码的更多信息，请参见 [\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_tell` 函数获取文件指针的当前位置 \(如果有\) 与 `handle` 参数。  视图传递，字节数开头文件。  对于 `_telli64` 函数，此值表示为一个 64 位整数。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_tell`, `_telli64`|\<io.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_tell.c  
// This program uses _tell to tell the  
// file pointer position after a file read.  
//  
  
#include <io.h>  
#include <stdio.h>  
#include <fcntl.h>  
#include <share.h>  
#include <string.h>  
  
int main( void )  
{  
   int  fh;  
   char buffer[500];  
  
   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )  
   {  
      char buff[50];  
      _strerror_s( buff, sizeof(buff), NULL );  
      printf( buff );  
      exit( -1 );  
   }  
  
   if( _read( fh, buffer, 500 ) > 0 )  
      printf( "Current file position is: %d\n", _tell( fh ) );  
   _close( fh );  
}  
```  
  
## Enter:crt\_tell.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Current file position is: 20  
```  
  
## 请参阅  
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [ftell、\_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [\_lseek、\_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)