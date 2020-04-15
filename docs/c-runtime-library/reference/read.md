---
title: _read
ms.date: 4/2/2020
api_name:
- _read
- _o__read
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
- _read
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
ms.openlocfilehash: db3726b85bb4ba7c8e9a691bef3fb063ec5709c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338135"
---
# <a name="_read"></a>_read

从文件读取数据。

## <a name="syntax"></a>语法

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>参数

*Fd*<br/>
引用打开的文件的文件说明符。

*缓冲区*<br/>
数据的存储位置。

*buffer_size*<br/>
要读取的最大字节数。

## <a name="return-value"></a>返回值

**_read**返回读取的字节数，如果文件中还剩少于*buffer_size*个字节，或者文件在文本模式下打开，则字节数可能小于*buffer_size。* 在文本模式下，每个回车换行对`\r\n`替换为单个行进给字符。 `\n` 只有单个换行符计入返回值。 此替换不影响文件指针。

如果函数尝试在文件末尾进行读取，则返回 0。 如果*fd*无效，则文件未打开以进行读取，或者文件被锁定，将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回 -1 并将**errno**设置到**EBADF**。

如果*缓冲区*为**NULL，** 或者如果*buffer_sizeINT_MAX* > **INT_MAX**，则调用无效的参数处理程序。 如果允许执行继续，则函数返回 **-1，errno**设置为**EINVAL**。

有关此代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_read**函数从与*fd*关联的文件中向*缓冲区*中读取最多*buffer_size*个字节。 读取操作从与给定文件相关联的文件指针的当前位置开始执行。 读取操作完成后，文件指针将指向下一个未读取的字符。

如果在文本模式下打开文件，则读取在 **_read**遇到 CTRL_Z 字符时终止，该字符被视为文件结尾指示器。 使用 [_lseek](lseek-lseeki64.md) 可清除文件尾指示符。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_read**|\<io.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
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
   int fh, bytesread;
   unsigned int nbytes = 60000;

   /* Open file for input: */
   if ( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ))
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if (( bytesread = _read( fh, buffer, nbytes )) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crt_readtxt"></a>输入：crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>输出

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>另请参阅

[低电平 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
