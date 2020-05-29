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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 273ad4990f78355029770e19e7cdcf36d7ba39bf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910079"
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
目标**文件**结构。

## <a name="return-value"></a>返回值

**ftell**和 **_ftelli64**返回当前文件位置。 **Ftell**和 **_ftelli64**返回的值可能不会反映在文本模式下打开的流的物理字节偏移量，因为文本模式会导致回车换行符转换。 将**ftell**与[fseek](fseek-fseeki64.md)或 **_ftelli64**结合使用以将[_fseeki64](fseek-fseeki64.md)正确返回到文件位置。 出现错误时， **ftell**和 **_ftelli64**将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回-1L，并将**errno**设置为 errno 中定义的两个常量之一。高. **Ebadf (** 常量表示*流*参数不是有效的文件指针值，或者未引用打开的文件。 **EINVAL**表示传递给函数的*流*参数无效。 在不能查找的设备上（例如终端和打印机），或当*stream*未引用打开的文件时，返回值为 undefined。

有关这些和其他返回代码的详细信息，请参阅[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>备注

**Ftell**和 **_ftelli64**函数检索与*stream*关联的文件指针（如果有）的当前位置。 位置表示为相对于流开头的偏移量。

请注意，当文件打开以追加数据时，当前文件位置由最后的 I/O 操作确定，而不是由发生下一个写入位置确定。 例如，如果打开文件进行追加，并且最后一次操作是读取，则文件位置将是下一个读取操作的开始点，而不是下一个写入的开始点。 （打开文件进行追加时，文件位置会在执行任何写入操作前移到文件尾。）如果在为追加打开的文件中尚未发生 i/o 操作，则文件位置是文件的开头。

在文本模式中，CTRL+Z 将在输入时解释为文件尾字符。 在打开以进行读取/写入的文件中， **fopen**和所有相关例程检查文件末尾的 CTRL + Z，并在可能的情况下将其删除。 这样做的原因是，使用**ftell**和[fseek](fseek-fseeki64.md)或 **_ftelli64**和[_Fseeki64](fseek-fseeki64.md)的组合在以 CTRL + Z 结尾的文件中移动时，可能导致**ftell**或 **_ftelli64**在文件结尾附近的行为不正确。

此函数在执行期间会锁定调用线程，因此是线程安全的。 有关非锁定版本，请参阅 **_ftell_nolock**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

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
