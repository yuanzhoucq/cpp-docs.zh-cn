---
title: _fcvt
ms.date: 4/2/2020
api_name:
- _fcvt
- _o__fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: a017ed58b962520793d5b10b088793dbc9b8a83d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347428"
---
# <a name="_fcvt"></a>_fcvt

将浮点数转换为字符串。 提供此函数的更安全的版本；请参阅 [_fcvt_s](fcvt-s.md)。

## <a name="syntax"></a>语法

```C
char *_fcvt(
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
小数点后面的数字位数。

*12 月*<br/>
指向存储的小数点位置的指针。

*标志*<br/>
指向存储的符号指示符的指针。

## <a name="return-value"></a>返回值

**_fcvt**返回指向数字字符串的指针，在错误时**返回 NULL。**

## <a name="remarks"></a>备注

**_fcvt**函数将浮点数转换为 null 端接字符串。 *值*参数是要转换的浮点数。 **_fcvt**将*值*的数字存储为字符串并附加空字符 （"\0"）。 *计数*参数指定在小数点之后要存储的数字数。 多余的数字四舍五入以*计数*地点。 如果精度数字少于*计数*数字，则字符串将用零填充。

**_fcvt**返回的总数不会超过 **_CVTBUFSIZE。**

字符串中仅存储位数。 小数点的位置和*值*符号可以从调用后的*dec*和 sign 获得。 *dec*参数指向整数值;此整数值给出小数点相对于字符串开头的位置。 零或负整数值表示小数点位于第一个数字的左侧。 参数*符号*指向指示*值*符号的整数。 如果*值*为正，则整数设置为 0，如果*值*为负值，则将设置为非零数。

**_ecvt**和 **_fcvt**的区别在于对*计数*参数的解释。 **_ecvt**将*计数*解释为输出字符串中的总位数，而 **_fcvt**将*计数*解释为小数点之后的位数。

**_ecvt**和 **_fcvt**使用单个静态分配的缓冲区进行转换。 对每个例程的每次调用都会破坏上一次调用的结果。

此函数验证其参数。 如果*de*或*符号*为**NULL**，或者*计数*为 0，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则**errno**设置为**EINVAL**并返回**NULL。**

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fcvt.c
// compile with: /W3
// This program converts the constant
// 3.1415926535 to a string and sets the pointer
// buffer to point to that string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int  decimal, sign;
   char *buffer;
   double source = 3.1415926535;

   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996
   // Note: _fcvt is deprecated; consider using _fcvt_s instead
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",
            source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0
```

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
