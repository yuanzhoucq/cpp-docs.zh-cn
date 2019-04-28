---
title: _ecvt
ms.date: 04/05/2018
apiname:
- _ecvt
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 36c9cb2e8cd9eb4dd67bb91e9e4dbd36d8d1fc8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288667"
---
# <a name="ecvt"></a>_ecvt

将转换**double**数字的字符串。 提供此函数的更安全的版本；请参阅 [_ecvt_s](ecvt-s.md)。

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

*值*<br/>
要转换的数字。

*count*<br/>
存储的数字位数。

*dec*<br/>
存储的十进制点位置。

*sign*<br/>
转换后的数字的符号。

## <a name="return-value"></a>返回值

**_ecvt**返回一个指向字符串的数字;**NULL**是否发生错误。

## <a name="remarks"></a>备注

**_Ecvt**函数将浮点数转换为字符字符串。 *值*参数是要转换的浮点数。 此函数最多存储*计数*位数*值*作为一个字符串，并追加 null 字符 (\0)。 如果中的数字个数*值*超过*计数*，低位数字舍入。 如果少于*计数*用零填充数字字符串。

返回的总位数 **_ecvt**将不会超过 **_CVTBUFSIZE**。

字符串中仅存储位数。 小数点和的符号的位置*值*可从此*dec*并*登录*后调用。 *Dec*参数指向整数值提供相对于字符串开头的小数点的位置。 0 或负整数值表示小数点位于第一个数字的左侧。 *登录*参数指向一个整数，指示转换后的数字的符号。 如果整数值为 0，则数值为正值。 否认，数值为负值。

之间的差异 **_ecvt**并 **_fcvt**中的解释*计数*参数。 **_ecvt**解释*计数*输出字符串中的位数总数而 **_fcvt**解释*计数*后的位数小数点。

**_ecvt**并 **_fcvt**使用单个静态分配的缓冲区用于转换。 每次调用这些例程都会破坏上一次调用的结果。

此函数验证其参数。 如果*dec*或*登录*是**NULL**，或者*计数*为 0，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**并**NULL**返回。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
