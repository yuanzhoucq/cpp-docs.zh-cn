---
title: tmpfile
ms.date: 11/04/2016
apiname:
- tmpfile
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
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: 98afcb7a3e04a96a1b08bc1b975634153e550839
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530320"
---
# <a name="tmpfile"></a>tmpfile

创建临时文件。 此函数已弃用，因为已提供更为安全的版本；请参阅 [tmpfile_s](tmpfile-s.md)。

## <a name="syntax"></a>语法

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>返回值

如果成功， **tmpfile**返回流指针。 否则，它将返回**NULL**指针。

## <a name="remarks"></a>备注

**Tmpfile**函数创建临时文件，并返回一个指向该流。 在根目录中创建了临时文件。 若要在目录（而非根）中创建临时文件，请将 [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 或 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 与 [fopen](fopen-wfopen.md) 结合使用。

如果无法打开该文件， **tmpfile**返回**NULL**指针。 通常情况下，或当终止时关闭该文件时，会自动删除此临时文件 **_rmtmp**调用，假定当前工作目录不会更改。 在打开临时文件时**w + b** （二进制读/写） 模式。

如果您尝试执行超过 TMP_MAX，可能会出现故障 （请参阅 STDIO。使用 H） 调用**tmpfile**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

> [!NOTE]
> 此示例需要在 Windows Vista 上运行的管理员特权。

```C
// crt_tmpfile.c
// compile with: /W3
// This program uses tmpfile to create a
// temporary file, then deletes this file with _rmtmp.
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int  i;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      if( (stream = tmpfile()) == NULL ) // C4996
      // Note: tmpfile is deprecated; consider using tmpfile_s instead
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
