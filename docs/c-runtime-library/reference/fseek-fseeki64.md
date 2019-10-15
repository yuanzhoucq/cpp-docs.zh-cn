---
title: fseek、_fseeki64
ms.date: 11/04/2016
api_name:
- _fseeki64
- fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: e3da603c3c7f1b083ddb7f7f9577adae9be5e4f1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956566"
---
# <a name="fseek-_fseeki64"></a>fseek、_fseeki64

将文件指针移到指定位置。

## <a name="syntax"></a>语法

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>参数

*stream*<br/>
指向**文件**结构的指针。

*offset*<br/>
*origin* 中的字节数。

*origin*<br/>
初始位置。

## <a name="return-value"></a>返回值

如果成功，则**fseek**和 **_fseeki64**返回0。 否则，返回一个非零值。 在无法查找的设备上，返回值是未定义的。 如果*stream*为空指针，或*源*不是下述允许的值之一，则**fseek**和 **_fseeki64**将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则这些函数会将**errno**设置为**EINVAL** , 并返回-1。

## <a name="remarks"></a>备注

**Fseek**和 **_fseeki64**函数将与*stream*关联的文件指针（如果有）移动到从源*偏移*字节的新*位置。* 该流上的下一步操作发生在新位置。 在准备更新的流上，下一个操作可以是读取或写入。 参数*源*必须是 stdio.h 中定义的以下常量之一。高

|原始值|含义|
|-|-|
| **SEEK_CUR** | 文件指针的当前位置。 |
| **SEEK_END** | 文件结尾。 |
| **SEEK_SET** | 文件开头。 |

可以使用**fseek**和 **_fseeki64**将指针重新定位到文件中的任何位置。 此外还可以在文件结尾外放置指针。 **fseek**和 **_fseeki64**清除文件尾指示符，并对任何之前针对*流*的[ungetc](ungetc-ungetwc.md)调用产生影响。

当文件打开以追加数据时，当前文件位置由最后的 I/O 操作确定，而不是由发生下一个写入的位置确定。 如果在为追加而打开的文件中尚未发生 I/O 操作，则文件位置是文件开头。

对于在文本模式下打开的流， **fseek**和 **_fseeki64**的使用有限，因为回车行转换可能会导致**fseek**和 **_fseeki64**产生意外的结果。 确保在文本模式下打开的流的唯一**fseek**和 **_fseeki64**操作是：

- 使用相对于任何原始值的偏移 0 进行查找。

- 当使用**fseek** 或 [_ftelli64](ftell-ftelli64.md) 时，使用或从文件开头开始查找偏移量值。调用 [ftell](ftell-ftelli64.md) **_fseeki64**

此外，在文本模式中，CTRL+Z 将在输入时解释为文件结尾字符。 在打开以进行读取/写入的文件中, [fopen](fopen-wfopen.md)和所有相关例程检查文件末尾的 CTRL + Z, 并在可能的情况下将其删除。 完成此操作的原因是，使用**fseek**和[ftell](ftell-ftelli64.md)或 **_fseeki64**和[_Ftelli64](ftell-ftelli64.md)的组合在以 CTRL + Z 结尾的文件中移动可能导致**fseek**或 **_fseeki64**在靠近文件.

当 CRT 打开以字节顺序标记 (BOM) 开头的文件时，文件指针位于 BOM 后面（即，位于文件实际内容的开头）。 如果必须**fseek**到文件的开头, 请使用[ftell](ftell-ftelli64.md)来获取初始位置并**fseek**到该位置, 而不是将其定位到0。

此函数在执行期间将锁定其他线程，因此是线程安全的。 有关非锁定版本，请参阅 [_fseek_nolock、_fseeki64_nolock](fseek-nolock-fseeki64-nolock.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen_wfopen](fopen-wfopen.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
