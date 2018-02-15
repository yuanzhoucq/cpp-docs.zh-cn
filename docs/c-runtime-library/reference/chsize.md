---
title: "_chsize | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _chsize
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _chsize
dev_langs:
- C++
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b975f4a1191acc2a02d1edcae861c033d280d98
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="chsize"></a>_chsize
更改文件大小。 提供此函数的一个更安全的版本；请参阅 [_chsize_s](../../c-runtime-library/reference/chsize-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
int _chsize(   
   int fd,  
   long size   
);  
```  
  
#### <a name="parameters"></a>参数  
 `fd`  
 引用打开的文件的文件描述符。  
  
 `size`  
 文件的新长度（以字节为单位）。  
  
## <a name="return-value"></a>返回值  
 如果已成功更改文件大小，则 `_chsize` 返回值 0。 返回值-1 指示错误：`errno`设置为`EACCES`如果指定的文件锁定对访问权限，为`EBADF`如果指定的文件是只读的或描述符无效，`ENOSPC`如果没有剩余空间上的设备或`EINVAL`如果`size`小于零。  
  
 有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_chsize` 函数扩展或截断与 `fd` 关联的文件，以达到 `size` 所指定的长度。 必须在允许写入的模式下打开文件。 如果扩展该文件，将追加 Null 字符 ('\0')。 如果文件被截断，则从缩短的文件的末尾到文件原始长度的所有数据都将丢失。  
  
 此函数验证其参数。 如果 `size` 小于零或 `fd` 是无效的文件描述符，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_chsize`|\<io.h>|\<errno.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
File length before: 0  
Size successfully changed  
File length after:  329678  
```  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_sopen、_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)