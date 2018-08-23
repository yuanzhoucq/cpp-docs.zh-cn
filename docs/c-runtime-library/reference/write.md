---
title: _write | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
- api-ms-win-crt-stdio-l1-1-0.dll
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 917309717d72048650d2b3975fefd74a1db50949
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2018
ms.locfileid: "42571833"
---
# <a name="write"></a>_write

将数据写入文件。

## <a name="syntax"></a>语法

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>参数

*fd*<br/>
可向其中写入数据的文件的文件描述符。

*buffer*<br/>
要写入的数据。

*count*<br/>
字节数。

## <a name="return-value"></a>返回值

如果成功， **_write**返回实际写入的字节数。 如果磁盘上剩余的实际空间小于函数尝试将写入到磁盘，缓冲区的大小 **_write**失败，并且不将任何缓冲区的内容刷新到磁盘。 返回值-1 指示错误。 如果传递的参数无效，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，该函数返回-1 和**errno**设置为三个值之一： **EBADF**，这意味着文件描述符无效或不打开文件进行写入;**ENOSPC**，这意味着没有足够的空间保留在设备上为该操作; 或**EINVAL**，这意味着*缓冲区*是 null 指针，或为奇数*计数*的字节传递要写入到在 Unicode 模式下的文件。

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果在文本模式下打开该文件，每个换行符字符替换为回车-换行对输出中。 此替换不会影响返回值。

在 Unicode 转换模式下打开文件时 — 例如，如果*fd*使用打开 **_open**或 **_sopen**和包括的模式参数 **_O_WTEXT**， **_O_U16TEXT**，或 **_O_U8TEXT**，或如果使用打开**fopen**以及包含的模式参数**ccs =UNICODE**， **ccs = UTF 16LE**，或**ccs = utf-8**，或如果将模式更改为 Unicode 转换模式使用 **_setmode**—*缓冲区*被解释为指向数组的指针**wchar_t** ，其中包含**utf-16**数据。 尝试在此模式下写入奇数个字节会导致参数验证错误。

## <a name="remarks"></a>备注

**_Write**函数写入*计数*个字节从*缓冲区*到与关联的文件*fd*。 写入操作从与给定文件相关联的文件指针（如果有）的当前位置开始执行。 如果文件处于打开状态以供追加，则该操作从该文件的当前末尾位置开始执行。 执行写入操作后，文件指针以实际写入的字节数为增量进行递增。

写入到在文本模式下打开的文件时 **_write** CTRL + Z 字符视为逻辑的文件结束。 写入到设备，当 **_write**将 CTRL + Z 字符视为输出终止符缓冲区中。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_write**|\<io.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
