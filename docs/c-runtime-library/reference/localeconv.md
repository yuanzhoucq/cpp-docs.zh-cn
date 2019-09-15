---
title: localeconv
ms.date: 11/04/2016
api_name:
- localeconv
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: ca7113903e1ed6e9ffb94bef79beba41e09bfb71
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953364"
---
# <a name="localeconv"></a>localeconv

获取区域设置的详细信息。

## <a name="syntax"></a>语法

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>返回值

**localeconv**返回指向[结构 lconv](../../c-runtime-library/standard-types.md)类型的已填充对象的指针。 对象中包含的值将从线程本地存储中的区域设置中进行复制，并可由对**localeconv**的后续调用覆盖。 对此对象中的值所做的更改不会修改区域设置。 对*类别*值为**LC_ALL**、 **LC_MONETARY**或**LC_NUMERIC**的[setlocale](setlocale-wsetlocale.md)的调用将覆盖该结构的内容。

## <a name="remarks"></a>备注

**Localeconv**函数获取有关当前区域设置的数字格式的详细信息。 此信息存储在 **lconv** 类型的结构中。 LOCALE.H 中定义的 **lconv** 结构，包含以下成员：

|字段|含义|
|-|-|
decimal_point,<br/>_W_decimal_point|指向非货币数量的小数点字符的指针。
thousands_sep,<br/>_W_thousands_sep|指向在非货币数量之间分隔小数点左边的位数的指针。
分组|指向**字符**大小的整数的指针，该整数包含非货币数量中每个数字组的大小。
int_curr_symbol,<br/>_W_int_curr_symbol|指向当前区域设置的国际货币符号的指针。 前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。 第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。
currency_symbol,<br/>_W_currency_symbol|指向当前区域设置的本地货币符号的指针。
mon_decimal_point,<br/>_W_mon_decimal_point|指向货币数量的小数点字符的指针。
mon_thousands_sep,<br/>_W_mon_thousands_sep|一个指针，指向要在货币数量中的小数位数左边的位数。
mon_grouping|指向**字符**大小的整数的指针，该整数包含每个数字组的大小（以货币数量表示）。
positive_sign,<br/>_W_positive_sign|非负货币数量的字符串指示符号。
negative_sign,<br/>_W_negative_sign|负货币数量的字符串指示符号。
int_frac_digits|带国际格式的货币数量中小数点右侧的数字个数。
frac_digits|带格式的货币数量中小数点右侧的数字个数。
p_cs_precedes|如果货币符号位于带格式的非负货币数量值的前面，则设置为 1。 如果符号紧随值后，则设置为 0。
p_sep_by_space|如果货币符号通过空格与带格式的非负货币数量值分隔开来，则设置为 1。 如果没有空格分离，则设置为 0。
n_cs_precedes|如果货币符号位于带格式的负货币数量值的前面，则设置为 1。 如果符号紧随值后，则设置为 0。
n_sep_by_space|如果货币符号通过空格与带格式的负货币数量值分隔开来，则设置为 1。 如果没有空格分离，则设置为 0。
p_sign_posn|带格式的非负货币数量中的加号位置。
n_sign_posn|带格式的负货币数量中的加号位置。

除了指定外，具有`char *`和`wchar_t *`版本的**lconv**结构的成员是指向字符串的指针。 任何等于 **""** （对于**wchar_t** <strong>\*</strong>为 "" **（或 ""）** 的值均为长度为零或在当前区域设置中不受支持。 请注意， **decimal_point**和 **_W_decimal_point**始终受支持且长度为非零。

此结构的**char**成员是不太负的非负数，而不是字符。 任何这些等于 **CHAR_MAX** 的成员在当前区域设置中不受支持。

根据以下规则解释**分组**和**mon_grouping**的值：

- **CHAR_MAX** -不执行任何进一步的分组。

- 0-对其余每个数字使用上一个元素。

- *n* -构成当前组的位数。 检查下一个元素以确定当前组前下一组数字的大小。

根据以下规则解释 **int_curr_symbol** 的值：

- 前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。

- 第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。

根据以下规则（**n_cs_precedes**规则位于括号中）解释 **p_cs_precedes** 和 **n_cs_precedes** 的值：

- 0-如果为非负（负）格式的货币值，则为货币符号。

- 1-在非负（负）格式化货币值的值之前的货币符号。

根据以下规则（**n_sep_by_space** 规则位于括号中）解释 **p_sep_by_space** 和 **n_sep_by_space** 的值：

- 0-对于非负（负）格式化货币值，货币符号是由空格分隔的。

- 1-非负（负）格式化货币值的货币符号和值之间没有空格分隔。

根据以下规解释 **p_sign_posn** 和 **n_sign_posn** 的值：

- 0-括号环绕数量和货币符号。

- 1-符号字符串位于数量和货币符号之前。

- 2-符号字符串位于数量和货币符号之后。

- 3-符号字符串位于货币符号之前。

- 4-符号字符串紧跟在货币符号之后。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[区域设置](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
