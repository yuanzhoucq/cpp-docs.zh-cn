---
title: _getw
ms.date: 11/04/2016
api_name:
- _getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: ad03c92ce90542ecae13609ee228ad094f64fc07
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954879"
---
# <a name="_getw"></a>_getw

从流中获取整数。

## <a name="syntax"></a>语法

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>参数

*stream*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

**_getw**返回读取的整数值。 **EOF**的返回值指示错误或文件尾。 但是，因为**EOF**值也是合法的整数值，请使用**feof**或**ferror**来验证文件尾或错误条件。 如果*stream*为**NULL**，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并且该函数将返回**EOF**。

## <a name="remarks"></a>备注

**_Getw**函数从与*流*关联的文件中读取**int**类型的下一个二进制值，并递增关联的文件指针（如果有）以指向下一个未读字符。 **_getw**不假定流中项的任何特殊对齐方式。 由于 int 类型的**int**类型的大小和**int**类型中的字节顺序在不同系统之间不同，因此可能会出现与 **_getw**有关的问题。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_getw.c
// This program uses _getw to read a word
// from a stream, then performs an error check.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   int i;

   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )
      printf( "Couldn't open file\n" );
   else
   {
      // Read a word from the stream:
      i = _getw( stream );

      // If there is an error...
      if( ferror( stream ) )
      {
         printf( "_getw failed\n" );
         clearerr_s( stream );
      }
      else
         printf( "First data word in file: 0x%.4x\n", i );
      fclose( stream );
   }
}
```

### <a name="input-crt_getwtxt"></a>输入：crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
