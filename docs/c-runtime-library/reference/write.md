---
title: _write
ms.date: 4/2/2020
api_name:
- _write
- _o__write
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a616df570d266c335337d897da59a2a0ec69b40e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367395"
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

*Fd*<br/>
可向其中写入数据的文件的文件描述符。

*缓冲区*<br/>
要写入的数据。

*count*<br/>
字节数。

## <a name="return-value"></a>返回值

如果成功 **，_write**返回写入的字节数。 如果磁盘上的剩余实际空间小于函数尝试写入磁盘的缓冲区大小 **，_write**失败，并且不会将缓冲区的任何内容刷新到磁盘。 返回值 -1 表示错误。 如果传递的参数无效，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数返回 **-1，errno**设置为三个值之一 **：EBADF，** 这意味着文件描述符无效或文件未打开以进行写入;**ENOSPC**，这意味着设备上没有足够的空间用于操作;或**EINVAL**，这意味着*缓冲区*是空指针，或者*字节的奇*数被传递到 Unicode 模式下的文件。

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果在文本模式下打开文件，则每个换行符将替换为输出中的回车换行对。 替换不会影响返回值。

在 Unicode 转换模式下打开文件时，例如， 如果使用 **_open**或 **_sopen**以及包含 **_O_WTEXT、_O_U16TEXT**或 **_O_U8TEXT**的模式参数打开 **_O_WTEXT** *fd，* 或者如果使用**fopen**和包含 ccs_UNICODE、ccs_UTF-16LE 或**ccs_UTF-8**的模式更改为 Unicode 转换 **_setmode**模式的模式，则*缓冲区*将解释为指向包含**UTF-16** **wchar_t数组的**指针。 **ccs=UNICODE** **ccs=UTF-16LE** 尝试在此模式下写入奇数个字节会导致参数验证错误。

## <a name="remarks"></a>备注

**_write**函数将*缓冲区的计数*字节写入*buffer*与*fd*关联的文件中。 写入操作从与给定文件相关联的文件指针（如果有）的当前位置开始执行。 如果文件处于打开状态以供追加，则该操作从该文件的当前末尾位置开始执行。 写入操作后，文件指针将因写入的字节数而增加。

写入文本模式下打开的文件时 **，_write**将 CTRL_Z 字符视为文件的逻辑结尾。 写入设备时 **，_write**将缓冲区中的 CTRL_Z 字符视为输出终止符。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_write**|\<io.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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
            // An unrelated error occurred
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

[低电平 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
