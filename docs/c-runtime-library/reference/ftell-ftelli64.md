---
title: ftell、_ftelli64
ms.date: 4/2/2020
api_name:
- _ftelli64
- ftell
- _o__ftelli64
- _o_ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: bfe79610161a7f4032517d9f7eaa0de50be18e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345612"
---
# <a name="ftell-_ftelli64"></a>ftell、_ftelli64

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

*流*<br/>
目标**文件结构**。

## <a name="return-value"></a>返回值

**ftell**和 **_ftelli64**返回当前文件位置。 **ftell**和 **_ftelli64**返回的值可能无法反映文本模式下打开的流的物理字节偏移量，因为文本模式会导致回车换行转换。 将**ftell**与[fseek](fseek-fseeki64.md)或 **_ftelli64**与[_fseeki64](fseek-fseeki64.md)正确返回到文件位置。 在错误时 **，ftell**和 **_ftelli64**调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将返回 -1L 并将**errno**设置为在 ERRNO 中定义的两个常量之一。H。 **EBADF**常量表示*流*参数不是有效的文件指针值，或者不引用打开的文件。 **EINVAL**表示无效*的流*参数已传递到函数。 在无法查找的设备（如终端和打印机）上，或者当*流*不引用打开的文件时，返回值未定义。

有关这些代码和其他返回代码的详细信息[，请参阅_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>备注

**ftell**和 **_ftelli64**函数检索与*流*关联的文件指针（如果有）的当前位置。 位置表示为相对于流开头的偏移量。

请注意，当文件打开以追加数据时，当前文件位置由最后的 I/O 操作确定，而不是由发生下一个写入位置确定。 例如，如果打开文件进行追加，并且最后一次操作是读取，则文件位置将是下一个读取操作的开始点，而不是下一个写入的开始点。 （打开文件进行追加时，文件位置将移动到文件末尾，然后再进行任何写入操作。如果打开用于追加的文件尚未发生 I/O 操作，则文件位置是文件的开头。

在文本模式中，CTRL+Z 将在输入时解释为文件尾字符。 在打开用于读取/写入的文件中 **，fopen**和所有相关例程检查文件末尾的 CTRL_Z，并尽可能将其删除。 这样做是因为使用**ftell**和[fseek](fseek-fseeki64.md)或 **_ftelli64**和[_fseeki64](fseek-fseeki64.md)的组合，在以 CTRL_Z 结尾的文件内移动可能会导致**ftell**或 **_ftelli64**在文件末尾附近行为不当。

此函数在执行期间会锁定调用线程，因此是线程安全的。 有关非锁定版本，请参阅 **_ftell_nolock**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|可选标头|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek、_fseeki64](fseek-fseeki64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
