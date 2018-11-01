---
title: strtoull、_strtoull_l、wcstoull、_wcstoull_l
ms.date: 11/04/2016
apiname:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
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
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
ms.openlocfilehash: f23799b43a356600f48fb0fbf32b4604966c416b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677547"
---
# <a name="strtoull-strtoulll-wcstoull-wcstoulll"></a>strtoull、_strtoull_l、wcstoull、_wcstoull_l

将字符串转换为无符号的长整数值。

## <a name="syntax"></a>语法

```C
unsigned long long strtoull(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long long _strtoull_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long long wcstoull(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long long _wcstoull_l(
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

**strtoull**返回转换后的值，如果有，或**ULLONG_MAX**在溢出。 **strtoull**如果可以不执行任何转换，则返回 0。 **wcstoull**类似于返回值**strtoull**。 对于这两个函数， **errno**设置为**ERANGE**如果出现溢出或下溢。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

每个函数将输入的字符串转换*strSource*到**无符号****长****长**整数值。

**strtoull**停止读取字符串*strSource*在它无法识别为数字一部分的第一个字符。 这可能是终止 null 字符，也可能会大于或等于第一个数字字符*基*。 设置**LC_NUMERIC**区域设置类别设置确定中基数字符的识别*strSource*; 有关详细信息，请参阅[setlocale、 _wsetlocale](setlocale-wsetlocale.md). **strtoull**并**wcstoull**使用当前区域设置;**_strtoull_l**并 **_wcstoull_l**改为否则使用传入的区域设置但完全相同。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**NULL**，在所指向的位置存储指向停止扫描的字符的指针*endptr*。 如果可以不执行任何转换 （未找到任何有效的数字或指定了无效的基数） 的值*strSource*所指向的位置存储*endptr*。

**wcstoull**是宽字符版本**strtoull**并将其*strSource*参数是宽字符字符串。 否则，这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull**|**strtoull**|**wcstoull**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull**预期*strSource*以指向以下形式的字符串：

> [*空格*] [{**+** &#124; **-**}] [**0** [{ **x**&#124; **X** }]] [*数字*&#124; *字母*]  

一个*空格*可能包含的空格和制表符，被忽略。 *数字*是一个或多个十进制数字。 *字母*中的一个或多个字母 a 到 z （或 A 到 Z）。 不符合此形式的第一个字符停止扫描。 如果*基*则用作数字的基数是 2 和 36，之间。 如果*基*为 0，所指向的字符串的初始字符*strSource*用于确定基数。 如果第一个字符为“0”，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 *base* 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果*基*为 0 和扫描的第一个字符为"0"，则假定八进制整数，且"8"或"9"字符停止扫描。 **strtoull**允许加号 (**+**) 或减号 (**-**) 前缀; 前导减号符号表示返回值不起作用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtoull**|\<stdlib.h>|
|**wcstoull**|\<stdlib.h> 或 \<wchar.h>|
|**_strtoull_l**|\<stdlib.h>|
|**_wcstoull_l**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [strtod](strtod-strtod-l-wcstod-wcstod-l.md) 的示例。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll、_strtoll_l、wcstoll、_wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
