---
title: _strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l
ms.date: 11/04/2016
apiname:
- _strtoi64
- _strtoi64_l
- _wcstoi64_l
- _wcstoi64
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
- _strtoi64
- strtoi64
- _stroi64_l
- _wcstoi64_l
- wcstoi64_l
- _wcstoi64
- wcstoi64
- strtoi64_l
helpviewer_keywords:
- _strtoi64 function
- _wcstoi64 function
- _strtoi64_l function
- string conversion, to integers
- _wcstoi64_l function
- strtoi64_l function
- wcstoi64 function
- strtoi64 function
- wcstoi64_l function
ms.assetid: ea2abc50-7bfe-420e-a46b-703c3153593a
ms.openlocfilehash: a8097a31ebbc56281008f14da58671d5b2e4e8b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490774"
---
# <a name="strtoi64-wcstoi64-strtoi64l-wcstoi64l"></a>_strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l

将字符串转换为 **__int64**值。

## <a name="syntax"></a>语法

```C
__int64 _strtoi64(
   const char *strSource,
   char **endptr,
   int base
);
__int64 _wcstoi64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
__int64 _strtoi64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
__int64 _wcstoi64_l(
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

**_strtoi64**返回字符串中表示的值*strSource*，只有当表示形式会导致溢出时，在其中它返回 **_I64_MAX**或 **_I64_MIN**。 如果无法执行任何转换，函数将返回 0。 **_wcstoi64**类似于返回值**strtoi64**。

**_I64_MAX**并 **_I64_MIN**限制中定义。H.

如果*strSource*是**NULL**或*基*为非零值且小于 2 或大于 36， **errno**设置为**EINVAL**.

有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Strtoi64**函数转换*strSource*到 **__int64**。 这两个函数停止读取字符串*strSource*在它们无法识别为数字一部分的第一个字符。 这可能是终止 null 字符，也可能会大于或等于第一个数字字符*基*。 **_wcstoi64**是宽字符版本 **_strtoi64**; 它*strSource*参数是宽字符字符串。 否则这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoi64**|**_strtoi64**|**_strtoi64**|**_wcstoi64**|
|**_tcstoi64_l**|**_strtoi64_l**|**_strtoi64_l**|**_wcstoi64_l**|

区域设置的**LC_NUMERIC**类别设置确定中基数字符的识别*strSource * *;* 有关详细信息，请参阅[setlocale](setlocale-wsetlocale.md)。 不带 _l 后缀的函数使用当前区域设置;**_strtoi64_l**并 **_wcstoi64_l**而无需相应函数相同 **_l**后缀，只不过它们改用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**NULL**，指向的位置存储指向停止扫描的字符的指针*endptr*。 如果可以不执行任何转换 （未找到任何有效的数字或指定了无效的基数） 的值*strSource*指向的位置处存储*endptr*。

**_strtoi64**预期*strSource*以指向以下形式的字符串：

> [*空格*] [{**+** &#124; **-**}] [**0** [{ **x**&#124; **X** }]] [*数字*&#124; *字母*]  

一个*空格*可能包含的空格和制表符，将被忽略;*位数*是一个或多个十进制数字;*字母*中的一个或多个字母 a 到 z （或 A 到 Z）。  不符合此形式的第一个字符停止扫描。 如果*基*则用作数字的基数是 2 和 36，之间。 如果*基*为 0，指向字符串的初始字符*strSource*用于确定基数。 如果第一个字符为 0，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 *base* 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果*基*为 0 和扫描的第一个字符为"0"，则假定八进制整数，且"8"或"9"字符将停止扫描。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_strtoi64**， **_strtoi64_l**|\<stdlib.h>|
|**_wcstoi64**， **_wcstoi64_l**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
