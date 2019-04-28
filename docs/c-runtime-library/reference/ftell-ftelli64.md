---
title: ftell、_ftelli64
ms.date: 11/04/2016
apiname:
- _ftelli64
- ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: cc76ad0776ae82637b95d32cdc6254d3c40da5b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332777"
---
# <a name="ftell-ftelli64"></a>ftell、_ftelli64

获取文件指针的当前位置。

## <a name="syntax"></a>语法

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*stream*<br/>
目标**文件**结构。

## <a name="return-value"></a>返回值

**ftell**并 **_ftelli64**返回当前文件位置。 返回的值**ftell**并 **_ftelli64**因为文本模式下会将回车-换行转换可能不会反映在文本模式下打开的流的物理字节偏移量。 使用**ftell**与[fseek](fseek-fseeki64.md)或 **_ftelli64**与[_fseeki64](fseek-fseeki64.md)正确返回到文件位置。 出现错误时， **ftell**并 **_ftelli64**将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回-1l 并集中**errno** ERRNO 中定义的两个常量之一。H. **EBADF**常量意味着*流*参数不是有效的文件指针值，或者未引用打开的文件。 **EINVAL**意味着无效*流*自变量传递给函数。 无法查找 （例如终端和打印机） 的设备上时，或者当*流*未引用打开的文件，则返回值是未定义。

有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Ftell**并 **_ftelli64**函数将检索与关联的文件指针 （如果有） 的当前位置*流*。 位置表示为相对于流开头的偏移量。

请注意，当文件打开以追加数据时，当前文件位置由最后的 I/O 操作确定，而不是由发生下一个写入位置确定。 例如，如果打开文件进行追加，并且最后一次操作是读取，则文件位置将是下一个读取操作的开始点，而不是下一个写入的开始点。 （在打开文件进行追加时，文件位置会在执行任何写操作前移动到文件的末尾。）如果在为进行追加而打开的文件中尚未发生任何 I/O 操作，则文件位置是文件的开头。

在文本模式中，CTRL+Z 将在输入时解释为文件尾字符。 打开以进行读取/写入的文件中**fopen**和所有相关的例程检查文件末尾的 CTRL + Z，并尽可能将其删除。 这是因为使用的组合**ftell**并[fseek](fseek-fseeki64.md)或 **_ftelli64**并[_fseeki64](fseek-fseeki64.md)，以结尾的文件中移动CTRL + Z 可能会导致**ftell**或 **_ftelli64**文件末尾附近运行不当。

此函数在执行期间会锁定调用线程，因此是线程安全的。 有关非锁定版本，请参阅 **_ftell_nolock**。

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek、_fseeki64](fseek-fseeki64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
