---
title: _write
ms.date: 11/04/2016
api_name:
- _write
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: 2c483df8e07b9496a0a22c1a1ebccf2b40d129cb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944859"
---
# <a name="_write"></a>_write

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

如果成功，则 **_write**返回写入的字节数。 如果磁盘上剩余的实际空间小于函数尝试写入磁盘的缓冲区的大小，则 **_write**将失败，并且不会将任何缓冲区的内容刷新到磁盘。 返回值-1 表示错误。 如果传递的参数无效，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则该函数将返回-1, 并将**errno**设置为以下三个值之一:**Ebadf (** , 这意味着文件描述符无效或文件未打开以进行写入;**ENOSPC**, 这意味着设备上没有足够的空间用于操作;或**EINVAL**, 这意味着*缓冲区*为空指针, 或在 Unicode 模式下传递到文件的奇数字节*数*。

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果在文本模式下打开该文件, 则会在输出中将每个换行符替换为回车换行符。 此替换不会影响返回值。

在 Unicode 转换模式下打开该文件时（例如，如果使用 **_open**或 **_sopen**打开*Fd* ，并使用包含 **_O_WTEXT**、 **_O_U16TEXT**或 **_O_U8TEXT**的模式参数打开，或者通过使用**fopen**和 mode 参数，其中包括**ccs = UNICODE**、 **ccs = utf-utf-16le**或**ccs = utf-8**，或者模式通过使用 **_setmode**更改为 UNICODE 转换模式时，*缓冲区*被解释为指向包含**utf-16**数据的**wchar_t**数组。 尝试在此模式下写入奇数个字节会导致参数验证错误。

## <a name="remarks"></a>备注

**_Write**函数将*缓冲区*中的*计数*字节写入与*fd*关联的文件中。 写入操作从与给定文件相关联的文件指针（如果有）的当前位置开始执行。 如果文件处于打开状态以供追加，则该操作从该文件的当前末尾位置开始执行。 写入操作完成后, 文件指针将按写入的字节数增加。

写入在文本模式下打开的文件时， **_write**会将 CTRL + Z 字符视为文件的逻辑端。 写入设备时， **_write**会将缓冲区中的 CTRL + Z 字符视为输出终止符。

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
