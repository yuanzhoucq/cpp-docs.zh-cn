---
title: "_write | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _write
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
apitype: DLLExport
f1_keywords:
- _write
dev_langs:
- C++
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d035a6b0941e7fa916e9306e5ef4f420d4e066d5
ms.lasthandoff: 02/24/2017

---
# <a name="write"></a>_write
将数据写入文件。  
  
## <a name="syntax"></a>语法  
  
```  
int _write(  
   int fd,  
   const void *buffer,  
   unsigned int count   
);  
```  
  
#### <a name="parameters"></a>参数  
 `fd`  
 可向其中写入数据的文件的文件描述符。  
  
 `buffer`  
 要写入的数据。  
  
 `count`  
 字节数。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `_write` 将返回实际写入的字节数。 如果磁盘上剩余的实际空间小于函数尝试写入到磁盘的缓冲区的大小，则 `_write` 将失败，并且无法将缓冲区中的任何内容刷新到磁盘中。 返回值 –1 指示错误。 如果传递的参数无效，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回 -1 并将 `errno` 设置为以下三个值之一：`EBADF`，该值表示文件描述符无效或文件未处于打开状态以供写入；`ENOSPC`，该值表示设备上的剩余空间不足，无法进行操作；或 `EINVAL`，该值表示 `buffer` 是空指针或已传递 `count` 个奇数字节以便在 Unicode 模式下将其写入到文件中。  
  
 有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果在文本模式下打开该文件，则会在输出中将每个换行符字符替换为回车符 – 换行符对。 此替换不会影响返回值。  
  
 当在 Unicode 转换模式下打开该文件时（例如，当使用 `_open` 或 `_sopen` 和包含 `_O_WTEXT`、`_O_U16TEXT` 或 `_O_U8TEXT` 的模式参数打开 `fd`，或使用 `fopen` 和包含 `ccs=UNICODE`、`ccs=UTF-16LE` 或 `ccs=UTF-8` 的模式参数打开它，或使用 `_setmode` 将该模式更改为 Unicode 转换模式时），会将 `buffer` 解释为指向包含 **UTF-16** 数据的 `wchar_t` 数组的指针。 尝试在此模式下写入奇数个字节会导致参数验证错误。  
  
## <a name="remarks"></a>备注  
 `_write` 函数将 `count` 个字节从 `buffer` 写入到与 `fd` 相关联的文件中。 写入操作从与给定文件相关联的文件指针（如果有）的当前位置开始执行。 如果文件处于打开状态以供追加，则该操作从该文件的当前末尾位置开始执行。 执行写入操作后，文件指针以实际写入的字节数为增量进行递增。  
  
 当写入到在文本模式下打开的文件中时，`_write` 会将 CTRL+Z 字符视为逻辑的文件末尾。 写入到设备时，`_write` 将缓冲区中的 CTRL+Z 字符视为输出终止符。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_write`|\<io.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt__write.c  
//   
// This program opens a file for output and uses _write to write  
// some bytes to the file.  
  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <errno.h>  
#include <share.h>  
  
char buffer[] = "This is a test of '_write' function";  
  
int main( void )  
{  
   int         fileHandle = 0;  
   unsigned    bytesWritten = 0;  
  
   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,  
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )  
      return -1;  
  
   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )  
   {  
      switch(errno)  
      {  
         case EBADF:  
            perror("Bad file descriptor!");  
            break;  
         case ENOSPC:  
            perror("No space left on device!");  
            break;  
         case EINVAL:  
            perror("Invalid parameter: buffer was NULL!");  
            break;  
         default:  
            // An unrelated error occured   
            perror("Unexpected error!");  
      }  
   }  
   else  
   {  
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );  
   }  
   _close( fileHandle );  
}  
```  
  
```Output  
Wrote 36 bytes to file.  
```  
  
## <a name="see-also"></a>另请参阅  
 [低级别 I/O](../../c-runtime-library/low-level-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_read](../../c-runtime-library/reference/read.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)
