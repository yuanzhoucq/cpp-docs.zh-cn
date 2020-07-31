---
title: _ecvt
ms.date: 4/2/2020
api_name:
- _ecvt
- _o__ecvt
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 227010fde5dc5ec82fc13c724c8d5a2f43788a8f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234193"
---
# <a name="_ecvt"></a>_ecvt

将 **`double`** 数字转换为字符串。 提供此函数的更安全的版本；请参阅 [_ecvt_s](ecvt-s.md)。

## <a name="syntax"></a>语法

```C
char *_ecvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>参数

*value*<br/>
要转换的数字。

*计数*<br/>
存储的数字位数。

*十进制*<br/>
存储的十进制点位置。

*sign*<br/>
转换后的数字的符号。

## <a name="return-value"></a>返回值

**_ecvt**返回指向数字字符串的指针;如果发生错误，则**为 NULL** 。

## <a name="remarks"></a>备注

**_Ecvt**函数将浮点数转换为字符串。 *值*参数是要转换的浮点数。 此函数以字符串的形式存储*值*的*计数*位数，并追加一个 null 字符（"\ 0"）。 如果*值*中的数字位数超过*计数*，则会舍入低序位。 如果数字少于*计数*，则用零填充字符串。

**_Ecvt**返回的总位数不会超过 **_CVTBUFSIZE**。

字符串中仅存储位数。 在调用后，可以从*dec*和*符号*获取小数点的位置和*值*的符号。 *Dec*参数指向一个整数值，该整数值给定小数点相对于字符串开头的位置。 0 或负整数值表示小数点位于第一个数字的左侧。 *Sign*参数指向一个整数，该整数指示转换后的数字的符号。 如果整数值为 0，则数值为正值。 否认，数值为负值。

**_Ecvt**和 **_fcvt**之间的区别在于*count*参数的解释。 **_ecvt**将*计数*解释为输出字符串中的总数字位数，而 **_fcvt**将*count*解释为小数点后的位数。

**_ecvt**和 **_fcvt**使用单个静态分配的缓冲区进行转换。 每次调用这些例程都会破坏上一次调用的结果。

此函数验证其参数。 如果*dec*或*sign*为**NULL**，或者*count*为0，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**EINVAL** ，并返回**NULL** 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_ecvt.c
// compile with: /W3
// This program uses _ecvt to convert a
// floating-point number to a character string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int     decimal,   sign;
   char    *buffer;
   int     precision = 10;
   double  source = 3.1415926535;

   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996
   // Note: _ecvt is deprecated; consider using _ecvt_s instead
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",
           source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0
```

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
