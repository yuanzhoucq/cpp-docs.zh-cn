---
title: _chsize
ms.date: 4/2/2020
api_name:
- _chsize
- _o__chsize
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
- _chsize
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
ms.openlocfilehash: bb2d72e40796a1dd2253361626042486490c77d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350059"
---
# <a name="_chsize"></a>_chsize

更改文件大小。 提供此函数的一个更安全的版本；请参阅 [_chsize_s](chsize-s.md)。

## <a name="syntax"></a>语法

```C
int _chsize(
   int fd,
   long size
);
```

### <a name="parameters"></a>参数

*Fd*<br/>
引用打开的文件的文件描述符。

*大小*<br/>
文件的新长度（以字节为单位）。

## <a name="return-value"></a>返回值

如果文件大小已成功更改 **，_chsize**返回值 0。 返回值 -1 表示错误：如果指定的文件为只读文件或指定文件被锁定反对访问，则错误设置为 EACCES;如果描述符**无效，则**将**errno**设置为 EACCES;如果描述符无效，则将 errno 设置为 EACCES;如果设备上没有空间，则将 errno 设置为**EACCES;** 如果*大小*小于零，则**EINVAL 设置为 EINVAL。** **EBADF**

有关这些代码和其他返回代码的详细信息[，请参阅_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>备注

**_chsize**函数将与*fd*关联的文件扩展或截截到*大小*指定的长度。 必须在允许写入的模式下打开文件。 如果扩展该文件，将追加 Null 字符 ('\0')。 如果文件被截断，则从缩短的文件的末尾到文件原始长度的所有数据都将丢失。

此函数验证其参数。 如果*大小*小于零或*fd*是一个坏的文件描述符，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_chsize**|\<io.h>|\<errno.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
