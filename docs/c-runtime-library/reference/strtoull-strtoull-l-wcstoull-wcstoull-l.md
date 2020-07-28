---
title: strtoull、_strtoull_l、wcstoull、_wcstoull_l
ms.date: 4/2/2020
api_name:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
- _o__strtoull_l
- _o__wcstoull_l
- _o_strtoull
- _o_wcstoull
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
ms.openlocfilehash: 9664ee4c671796ad8805c19c93d5a5fd289c80ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87189111"
---
# <a name="strtoull-_strtoull_l-wcstoull-_wcstoull_l"></a>strtoull、_strtoull_l、wcstoull、_wcstoull_l

将字符串转换为 **`unsigned long long`** 整数值。

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

**strtoull**返回转换后的值（如果有）或**ULLONG_MAX**溢出。 如果无法执行任何转换，则**strtoull**将返回0。 **wcstoull**将类似值返回到**strtoull**。 对于这两个函数，如果出现溢出或下溢，则**errno**设置为**ERANGE** 。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

其中每个函数将输入字符串*strSource*转换为 **`unsigned long long`** 整数值。

**strtoull**停止读取其无法识别为数字一部分的第一个字符的字符串*strSource* 。 这可能是终止 null 字符，也可能是大于或等于*基准*的第一个数字字符。 区域设置的**LC_NUMERIC**类别确定*strSource*中的基数字符的识别;有关详细信息，请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md)。 **strtoull**和**wcstoull**使用当前区域设置;**_strtoull_l**和 **_wcstoull_l**改为使用传入的区域设置，但却是相同的。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不为**NULL**，则指向停止扫描的字符的指针将存储在*endptr*指向的位置。 如果无法执行任何转换（未找到任何有效的数字或指定了无效的基数），则*strSource*的值将存储在*endptr*指向的位置。

**wcstoull**是**strtoull**的宽字符版本，其*strSource*参数是宽字符字符串。 否则，这些函数具有相同行为。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull**|**strtoull**|**wcstoull**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull**要求*strSource*指向以下格式的字符串：

> [*空格*][{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*数字*&#124;*字母*]

*空白*可能包含被忽略的空格和制表符。 *数字*是一个或多个十进制数字。 *字母*是从 "a" 到 "z" （或 "a" 到 "z"）的一个或多个字母。 不符合此形式的第一个字符停止扫描。 如果*base*介于2和36之间，则将其用作数字的基数。 如果*base*为0，则使用*strSource*指向的字符串的初始字符来确定基。 如果第一个字符为“0”，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 *base* 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果*base*为0且扫描的第一个字符为 "0"，则假定八进制整数，且 "8" 或 "9" 字符会停止扫描。 **strtoull**允许加号（ **+** ）或减号（ **-** ）前缀; 前导减号表示返回值为否定。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtoull**|\<stdlib.h>|
|**wcstoull**|\<stdlib.h> 或 \<wchar.h>|
|**_strtoull_l**|\<stdlib.h>|
|**_wcstoull_l**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [strtod](strtod-strtod-l-wcstod-wcstod-l.md) 的示例。

## <a name="see-also"></a>另请参阅

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
