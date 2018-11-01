---
title: strtold、_strtold_l、 wcstold、_wcstold_l
ms.date: 04/05/2018
apiname:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
ms.openlocfilehash: fce60775ee1ef6def214e559779004d4de95453c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484573"
---
# <a name="strtold-strtoldl-wcstold-wcstoldl"></a>strtold、_strtold_l、 wcstold、_wcstold_l

将字符串转换为长双精度浮点值。

## <a name="syntax"></a>语法

```C
long double strtold(
   const char *strSource,
   char **endptr
);
long double _strtold_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
long double wcstold(
   const wchar_t *strSource,
   wchar_t **endptr
);
long double wcstold_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*strSource*<br/>
要转换的 null 终止的字符串。

*endptr*<br/>
指向停止扫描的字符的指针。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strtold**返回的值的浮点数值**长** **double**，只有当表示形式会导致溢出，这种情况下，该函数将返回 + /-**HUGE_VALL**。 符号**HUGE_VALL**不能表示的值相匹配。 **strtold**如果可以执行任何转换或发生下溢，则返回 0。

**wcstold**类似于返回值**strtold**。 对于这两个函数， **errno**设置为**ERANGE**如果出现溢出或下溢并调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

每个函数将输入的字符串转换*strSource*到**长** **double**。 **Strtold**函数停止读取字符串*strSource*在它无法识别为数字一部分的第一个字符。 这可能是终止 null 字符。 宽字符版本**strtold**是**wcstold**; 它*strSource*参数是宽字符字符串。 否则，这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

**LC_NUMERIC**的当前区域设置类别设置确定的中的基数字符识别*strSource*。 有关详细信息，请参阅 [setlocale、_wsetlocale](setlocale-wsetlocale.md)。 功能而无需 **_l**后缀使用当前区域设置;**_strtold_l**并 **_wcstold_l**相同 **_strtold**并 **_wcstold** ，只不过它们改用的区域设置的传入。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**NULL**，在所指向的位置存储指向停止扫描的字符的指针*endptr*。 如果可以不执行任何转换 （未找到任何有效的数字或指定了无效的基数） 的值*strSource*所指向的位置存储*endptr*。

**strtold**预期*strSource*以指向以下形式的字符串：

[*空格*] [*登录*] [*数字*] [。*位数*] [{**d** &#124; **D** &#124; **e** &#124; **E**} [*登录*]*数字*]

一个*空格*可能包含的空格和制表符，将被忽略;*符号*是加上 (**+**) 或减号 (**-**); 并*数字*是一个或多个十进制数字。 如果基数字符前没有任何数字，则基数字符后必须至少有一个数字。 十进制数字可以后跟一个指数，其中包含介绍性字母（**d**、**D**、**e** 或 **E**）和可选的带符号整数。 如果指数部分和基数字符都没有出现，则假定基数字符跟随字符串中的最后一个数字。 不符合此形式的第一个字符停止扫描。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtold**， **_strtold_l**|\<stdlib.h>|
|**wcstold**， **_wcstold_l**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strtold.c
// Build with: cl /W4 /Tc crt_strtold.c
// This program uses strtold to convert a
// string to a long double-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   long double x;

   string = "3.1415926535898This stopped it";
   x = strtold(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtold = %.13Lf\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.1415926535898This stopped it
   strtold = 3.1415926535898
   Stopped scan at: This stopped it

```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
