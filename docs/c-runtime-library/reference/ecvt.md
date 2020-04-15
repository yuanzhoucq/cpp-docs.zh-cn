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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 5e1760d5c68e650f6fbf44866d4e368b9d6233b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348029"
---
# <a name="_ecvt"></a>_ecvt

将**双**数转换为字符串。 提供此函数的更安全的版本；请参阅 [_ecvt_s](ecvt-s.md)。

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

*count*<br/>
存储的数字位数。

*12 月*<br/>
存储的十进制点位置。

*标志*<br/>
转换后的数字的符号。

## <a name="return-value"></a>返回值

**_ecvt**返回指向数字字符串的指针;如果发生错误，**则为 NULL。**

## <a name="remarks"></a>备注

**_ecvt**函数将浮点数转换为字符串。 *值*参数是要转换的浮点数。 此函数将*值*的数字*存储*起来为字符串，并追加空字符 （"\0"）。 如果*值*中的位数超过*计数*，则低阶数字将四舍五入。 如果*数字少于计数*数字，则字符串将用零填充。

**_ecvt**返回的总数不会超过 **_CVTBUFSIZE。**

字符串中仅存储位数。 小数点的位置和*值*符号可以从调用后的*dec*和*sign*获得。 *dec*参数指向一个整数值，该值给出相对于字符串开头的小数点的位置。 0 或负整数值表示小数点位于第一个数字的左侧。 *符号*参数指向指示转换数字符号的整数。 如果整数值为 0，则数值为正值。 否认，数值为负值。

**_ecvt**和 **_fcvt**的区别在于对*计数*参数的解释。 **_ecvt**将*计数*解释为输出字符串中的总位数，而 **_fcvt**将*计数*解释为小数点之后的位数。

**_ecvt**和 **_fcvt**使用单个静态分配的缓冲区进行转换。 每次调用这些例程都会破坏上一次调用的结果。

此函数验证其参数。 如果*de*或*符号*为**NULL**，或者*计数*为 0，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则**errno**设置为**EINVAL**并返回**NULL。**

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

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
