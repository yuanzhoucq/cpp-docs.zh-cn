---
title: strtoll、_strtoll_l、wcstoll、_wcstoll_l
ms.date: 11/04/2016
apiname:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
ms.openlocfilehash: 53ae4ab1d482478c50aa257acdc974569bfc05f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523165"
---
# <a name="strtoll-strtolll-wcstoll-wcstolll"></a>strtoll、_strtoll_l、wcstoll、_wcstoll_l

字符串转换为**长****长**值。

## <a name="syntax"></a>语法

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*strSource*<br/>
要转换的 null 终止的字符串。

*endptr*<br/>
指向停止扫描的字符的指针。

*base*<br/>
要使用的基数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strtoll**返回的字符串表示的值*strSource*，只有当表示形式会导致溢出，这种情况下，它将返回**与 LLONG_MAX**或**LLONG_MIN**。 如果无法执行任何转换，则函数返回 0。 **wcstoll**类似于返回值**strtoll**。

**与 LLONG_MAX**并**LLONG_MIN**限制中定义。H.

如果*strSource*是**NULL**或*基*为非零值且小于 2 或大于 36， **errno**设置为**EINVAL**.

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**Strtoll**函数转换*strSource*到**长****长**。 这两个函数停止读取字符串*strSource*在它们无法识别为数字一部分的第一个字符。 这可能是终止 null 字符，也可能会大于或等于第一个数字字符*基*。 **wcstoll**是宽字符版本**strtoll**; 它*strSource*参数是宽字符字符串。 否则，这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll**|**strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

区域设置的**LC_NUMERIC**类别设置确定中基数字符的识别*strSource*; 有关详细信息，请参阅[setlocale、 _wsetlocale](setlocale-wsetlocale.md)。 没有的函数 **_l**后缀使用当前区域设置;**_strtoll_l**并 **_wcstoll_l**是不带有该后缀的相应函数相同，只不过它们改用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**NULL**，在所指向的位置存储指向停止扫描的字符的指针*endptr*。 如果可以不执行任何转换 （未找到任何有效的数字或指定了无效的基数） 的值*strSource*所指向的位置存储*endptr*。

**strtoll**预期*strSource*以指向以下形式的字符串：

> [*空格*] [{**+** &#124; **-**}] [**0** [{ **x**&#124; **X** }]] [*数字*&#124; *字母*]  

一个*空格*可能包含的空格和制表符，将被忽略;*位数*是一个或多个十进制数字;*字母*中的一个或多个字母 a 到 z （或 A 到 Z）。 不符合此形式的第一个字符停止扫描。 如果*基*则用作数字的基数是 2 和 36，之间。 如果*基*为 0，所指向的字符串的初始字符*strSource*用于确定基数。 如果第一个字符为“0”，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 *base* 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果*基*为 0 和扫描的第一个字符为"0"，则假定八进制整数，且"8"或"9"字符停止扫描。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtoll**， **_strtoll_l**|\<stdlib.h>|
|**wcstoll**， **_wcstoll_l**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
