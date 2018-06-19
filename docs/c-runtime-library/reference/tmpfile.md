---
title: tmpfile | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ebcad2a25af2f2acb0056d882c4191f1a51293d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409064"
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

**Tmpfile**函数将创建临时文件，将指针返回到该流。 在根目录中创建了临时文件。 若要在目录（而非根）中创建临时文件，请将 [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 或 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 与 [fopen](fopen-wfopen.md) 结合使用。

如果无法打开该文件， **tmpfile**返回**NULL**指针。 时关闭该文件，则程序终止通常情况下，或当时，将自动删除此临时文件 **_rmtmp**称为，前提是当前工作目录不会更改。 在打开临时文件**w + b** （二进制读/写） 模式。

如果多个 TMP_MAX 尝试，则可能发生失败 （请参阅 STDIO。H） 使用调用**tmpfile**。

## <a name="requirements"></a>要求

|例程|必需的标头|
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
