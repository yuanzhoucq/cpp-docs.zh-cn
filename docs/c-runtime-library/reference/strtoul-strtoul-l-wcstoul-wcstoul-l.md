---
title: strtoul、_strtoul_l、wcstoul、_wcstoul_l
ms.date: 4/2/2020
api_name:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
- _o__strtoul_l
- _o__wcstoul_l
- _o_strtoul
- _o_wcstoul
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strtoul
- _tcstoul
- wcstoul
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
ms.openlocfilehash: 9e0e466893aedb565fcd5852c6768ecfc620c611
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912408"
---
# <a name="strtoul-_strtoul_l-wcstoul-_wcstoul_l"></a>strtoul、_strtoul_l、wcstoul、_wcstoul_l

将字符串转换为无符号的长整数值。

## <a name="syntax"></a>语法

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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

**strtoul**返回转换后的值（如果有）或**ULONG_MAX**溢出。 如果无法执行任何转换，则**strtoul**将返回0。 **wcstoul**将类似值返回到**strtoul**。 对于这两个函数，如果出现溢出或下溢，则**errno**设置为**ERANGE** 。

关于此代码以及其他返回代码的详细信息，请参阅 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。

## <a name="remarks"></a>备注

其中每个函数将输入字符串*strSource*转换为**无符号****长**整数。

**strtoul**停止读取其无法识别为数字一部分的第一个字符的字符串*strSource* 。 这可能是终止 null 字符，也可能是大于或等于*base*的第一个数字字符。 区域设置的**LC_NUMERIC**类别设置确定*strSource*中的基数字符的识别;有关详细信息，请参阅[setlocale](setlocale-wsetlocale.md)。 **strtoul**和**wcstoul**使用当前区域设置;**_strtoul_l**和 **_wcstoul_l**相同，只不过它们改用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不为**NULL**，则指向停止扫描的字符的指针将存储在*endptr*指向的位置。 如果无法执行任何转换（未找到任何有效的数字或指定了无效的基数），则*strSource*的值将存储在*endptr*指向的位置。

**wcstoul**是**strtoul**的宽字符版本;其*strSource*参数是宽字符字符串。 否则，这些函数具有相同行为。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**strtoul**要求*strSource*指向以下格式的字符串：

> [*空格*][{**+** &#124; **-**}][**0** [{ **x** &#124; **x** }]] [*数字*&#124;*字母*]

*空白*可能包含被忽略的空格和制表符。 *数字*是一个或多个十进制数字。 *字母*是从 "a" 到 "z" （或 "a" 到 "z"）的一个或多个字母。 不符合此形式的第一个字符停止扫描。 如果*base*介于2和36之间，则将其用作数字的基数。 如果*base*为0，则使用*strSource*指向的字符串的初始字符来确定基。 如果第一个字符为 0，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 *base* 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果*base*为0且扫描的第一个字符为 "0"，则假定八进制整数，且 "8" 或 "9" 字符会停止扫描。 **strtoul**允许加号（**+**）或减号（**-**）符号前缀;前导减号表示返回值为否定。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strtoul**|\<stdlib.h>|
|**wcstoul**|\<stdlib.h> 或 \<wchar.h>|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [strtod](strtod-strtod-l-wcstod-wcstod-l.md) 的示例。

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
