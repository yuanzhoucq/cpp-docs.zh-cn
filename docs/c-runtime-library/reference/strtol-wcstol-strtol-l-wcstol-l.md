---
title: ':::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::'
ms.date: 4/2/2020
api_name:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- '_o_:::no-loc(_strtol_l):::'
- '_o_:::no-loc(_wcstol_l):::'
- '_o_:::no-loc(strtol):::'
- '_o_:::no-loc(wcstol):::'
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
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(strtol):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_tcstol_l):::'
helpviewer_keywords:
- ':::no-loc(wcstol)::: function'
- :::no-loc(wcstol):::_l function
- ':::no-loc(_tcstol)::: function'
- string conversion, to integers
- tcstol function
- :::no-loc(strtol):::_l function
- ':::no-loc(_wcstol_l)::: function'
- ':::no-loc(_strtol_l)::: function'
- ':::no-loc(strtol)::: function'
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(LONG_MAX):::'
- ':::no-loc(LONG_MIN):::'
- ':::no-loc(errno):::'
- ':::no-loc(ERANGE):::'
- ':::no-loc(EINVAL):::'
- ':::no-loc(LC_NUMERIC):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(_tcstol_l):::'
- ':::no-loc(localeconv):::'
- ':::no-loc(setlocale):::'
- ':::no-loc(_wsetlocale):::'
- ':::no-loc(strtod):::'
- ':::no-loc(_strtod_l):::'
- ':::no-loc(wcstod):::'
- ':::no-loc(_wcstod_l):::'
- ':::no-loc(strtoll):::'
- ':::no-loc(_strtoll_l):::'
- ':::no-loc(wcstoll):::'
- ':::no-loc(_wcstoll_l):::'
- ':::no-loc(strtoul):::'
- ':::no-loc(_strtoul_l):::'
- ':::no-loc(wcstoul):::'
- ':::no-loc(_wcstoul_l):::'
- ':::no-loc(atof):::'
- ':::no-loc(_atof_l):::'
- ':::no-loc(_wtof):::'
- ':::no-loc(_wtof_l):::'
ms.openlocfilehash: a5265b434f14f299532d6f5ebb65c83d75ea63ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232399"
---
# <a name="no-locstrtol-no-locwcstol-no-loc_strtol_l-no-loc_wcstol_l"></a>:::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::

将字符串转换为 **`long`** 整数值。

## <a name="syntax"></a>语法

```C
long :::no-loc(strtol):::(
   const char *string,
   char **end_ptr,
   int base
);
long :::no-loc(wcstol):::(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long :::no-loc(_strtol_l):::(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long :::no-loc(_wcstol_l):::(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*类似*\
要转换的 null 终止的字符串。

*end_ptr*\
一个输出参数，设置为指向最后解释的字符后面的字符。 如果**为 NULL**，则忽略。

*基座*\
要使用的基数。

*本地*\
要使用的区域设置。

## <a name="return-value"></a>返回值

**:::no-loc(strtol):::**、 **:::no-loc(wcstol):::** 、 **:::no-loc(_strtol_l):::** 和 **:::no-loc(_wcstol_l):::** 返回*字符串*中表示的值。 如果无法进行转换，则返回0。 当表示形式导致溢出时，它们将返回 **:::no-loc(LONG_MAX):::** 或 **:::no-loc(LONG_MIN):::** 。

**:::no-loc(errno):::****:::no-loc(ERANGE):::** 如果发生溢出或下溢，则设置为。 **:::no-loc(EINVAL):::** 如果*String*为**NULL**，则设置为。 如果*基数*为非零且小于2，或大于36，则为。 有关 **:::no-loc(ERANGE):::** 、 **:::no-loc(EINVAL):::** 和其他返回代码的详细信息，请参阅[_dos :::no-loc(errno)::: 、 :::no-loc(errno)::: 、_sys_errlist 和 _sys_nerr](../../c-runtime-library/:::no-loc(errno):::-dos:::no-loc(errno):::-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**:::no-loc(strtol):::**、、 **:::no-loc(wcstol):::** **:::no-loc(_strtol_l):::** 和 **:::no-loc(_wcstol_l):::** 函数将*字符串*转换为 **`long`** 。 它们会在第一个不能识别为数字一部分的字符处停止读取*字符串*。 它可以是终止 null 字符，也可以是大于或等于*base*的第一个字母数字字符。

**:::no-loc(wcstol):::** 和 **:::no-loc(_wcstol_l):::** 是和的宽字符版本 **:::no-loc(strtol):::** **:::no-loc(_strtol_l):::** 。 它们的*字符串*参数是宽字符字符串。 这些函数的行为与 **:::no-loc(strtol):::** 和中的行为相同 **:::no-loc(_strtol_l):::** 。 区域设置的 **:::no-loc(LC_NUMERIC):::** 类别设置确定*字符串*中基数字符的识别（小数标记或小数点）。 函数 **:::no-loc(strtol):::** 和 **:::no-loc(wcstol):::** 使用当前区域设置。 **:::no-loc(_strtol_l):::** 并改用 **:::no-loc(_wcstol_l):::** 传入的区域设置。 有关详细信息，请参阅 [ :::no-loc(setlocale)::: ] 和[区域设置](../../c-runtime-library/locale.md)。

当*end_ptr*为**NULL**时，它将被忽略。 否则，指向停止扫描的字符的指针将存储在*end_ptr*指向的位置。 如果找不到有效的数字或指定了无效的基，则不可能进行转换。 然后，*字符串*的值将存储在*end_ptr*指向的位置。

**:::no-loc(strtol):::** 应将*字符串*指向以下格式的字符串：

> [*空格*][{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*字母数字*]

方括号（ `[ ]` ）将可选元素括起来。 大括号和竖线（ `{ | }` ）环绕单个元素的替代项。 *空格*可能包含被忽略的空格和制表符。 *字母数字*是十进制数字或字母 "a" 到 "z" （或 "a" 到 "z"）。 不符合此窗体的第一个字符会停止扫描。 如果*base*介于2和36之间，则将其用作数字的基数。 如果*base*为0，则使用*字符串*指向的字符串的初始字符来确定基。 如果第一个字符为0，且第二个字符不为 "x" 或 "X"，则字符串将被解释为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 字母 "a" 到 "z" （或 "A" 到 "Z"）被分配值10到35。 扫描仅允许值小于*基数*的字母。 超出基数范围的第一个字符停止扫描。 例如，假设*字符串*以 "01" 开头。 如果*base*为0，则扫描程序假定它是八进制整数。 "8" 或 "9" 字符会停止扫描。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**:::no-loc(_tcstol):::**|**:::no-loc(strtol):::**|**:::no-loc(strtol):::**|**:::no-loc(wcstol):::**|
|**:::no-loc(_tcstol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_wcstol_l):::**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**:::no-loc(strtol):::**|\<stdlib.h>|
|**:::no-loc(wcstol):::**|\<stdlib.h> 或 \<wchar.h>|
|**:::no-loc(_strtol_l):::**|\<stdlib.h>|
|**:::no-loc(_wcstol_l):::**|\<stdlib.h> 或 \<wchar.h>|

**:::no-loc(_strtol_l):::** 和 **:::no-loc(_wcstol_l):::** 函数是 Microsoft 特定的，而不是标准 C 库的一部分。 有关其他兼容性信息，请参阅[兼容性](../compatibility.md)。

## <a name="example"></a>示例

请参阅的示例 [:::no-loc(strtod):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md) 。

## <a name="see-also"></a>另请参阅

[数据转换](../data-conversion.md)\
[本地](../locale.md)\
[:::no-loc(localeconv):::](:::no-loc(localeconv):::.md)\
[:::no-loc(setlocale):::, :::no-loc(_wsetlocale):::](:::no-loc(setlocale):::-w:::no-loc(setlocale):::.md)\
[字符串到数值函数](../string-to-numeric-value-functions.md)\
[:::no-loc(strtod):::, :::no-loc(_strtod_l):::, :::no-loc(wcstod):::, :::no-loc(_wcstod_l):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md)\
[:::no-loc(strtoll):::, :::no-loc(_strtoll_l):::, :::no-loc(wcstoll):::, :::no-loc(_wcstoll_l):::](:::no-loc(strtoll):::-:::no-loc(strtoll):::-l-:::no-loc(wcstoll):::-:::no-loc(wcstoll):::-l.md)\
[:::no-loc(strtoul):::, :::no-loc(_strtoul_l):::, :::no-loc(wcstoul):::, :::no-loc(_wcstoul_l):::](:::no-loc(strtoul):::-:::no-loc(strtoul):::-l-:::no-loc(wcstoul):::-:::no-loc(wcstoul):::-l.md)\
[:::no-loc(atof):::, :::no-loc(_atof_l):::, :::no-loc(_wtof):::, :::no-loc(_wtof_l):::](:::no-loc(atof):::-:::no-loc(atof):::-l-wtof-wtof-l.md)
