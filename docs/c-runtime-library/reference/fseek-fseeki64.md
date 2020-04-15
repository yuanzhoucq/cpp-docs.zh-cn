---
title: fseek、_fseeki64
ms.date: 4/2/2020
api_name:
- _fseeki64
- fseek
- _o__fseeki64
- _o_fseek
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
ms.openlocfilehash: e8f6021a0b770f6b435653c190d5968f9ac50a57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345756"
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

*流*<br/>
指向**文件**结构的指针。

*偏移量*<br/>
*origin* 中的字节数。

*起源*<br/>
初始位置。

## <a name="return-value"></a>返回值

如果成功 **，fseek**和 **_fseeki64**返回 0。 否则，返回一个非零值。 在无法查找的设备上，返回值是未定义的。 如果*流*是空指针，或者如果*原点*不是下面描述的允许值之一 **，fseek**和 **_fseeki64**调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将**errno**设置为**EINVAL**并返回 -1。

## <a name="remarks"></a>备注

**fseek**和 **_fseeki64**函数将与*流*关联的文件指针（如果有）移动到从*原点**偏移*字节的新位置。 该流上的下一步操作发生在新位置。 在准备更新的流上，下一个操作可以是读取或写入。 参数*原点*必须是 STDIO 中定义的以下常量之一。H：

|原点值|含义|
|-|-|
| **SEEK_CUR** | 文件指针的当前位置。 |
| **SEEK_END** | 文件结尾。 |
| **SEEK_SET** | 文件开头。 |

您可以使用**fseek**和 **_fseeki64**重新定位文件中的任意位置的指针。 此外还可以在文件结尾外放置指针。 **fseek**和 **_fseeki64**清除文件结尾指示器，并否定任何以前的[不加点](ungetc-ungetwc.md)调用对*流*的影响。

当文件打开以追加数据时，当前文件位置由最后的 I/O 操作确定，而不是由发生下一个写入的位置确定。 如果在为追加而打开的文件中尚未发生 I/O 操作，则文件位置是文件开头。

对于在文本模式下打开的流 **，fseek**和 **_fseeki64**的使用有限，因为回车回馈线转换可能会导致**fseek**和 **_fseeki64**产生意外的结果。 保证在文本模式下打开的流上工作的唯**一 fseek**和 **_fseeki64**操作是：

- 使用相对于任何原始值的偏移 0 进行查找。

- 当使用**fseek** 或 [_ftelli64](ftell-ftelli64.md) 时，使用或从文件开头开始查找偏移量值。调用 [ftell](ftell-ftelli64.md)**_fseeki64**

此外，在文本模式中，CTRL+Z 将在输入时解释为文件结尾字符。 在打开用于读取/写入的文件中[，fopen](fopen-wfopen.md)和所有相关例程检查文件末尾的 CTRL_Z，并尽可能将其删除。 这样做是因为使用**fseek**和[ftell](ftell-ftelli64.md)或 **_fseeki64**和[_ftelli64](ftell-ftelli64.md)的组合，在以 CTRL_Z 结尾的文件内移动可能会导致**fseek**或 **_fseeki64**在文件末尾附近行为不当。

当 CRT 打开以字节顺序标记 (BOM) 开头的文件时，文件指针位于 BOM 后面（即，位于文件实际内容的开头）。 如果必须**fseek**到文件的开头，请使用[ftell](ftell-ftelli64.md)获取初始位置和**fseek**到它，而不是定位 0。

此函数在执行期间将锁定其他线程，因此是线程安全的。 有关非锁定版本，请参阅 [_fseek_nolock、_fseeki64_nolock](fseek-nolock-fseeki64-nolock.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[倒](rewind.md)<br/>
