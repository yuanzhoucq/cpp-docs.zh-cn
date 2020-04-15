---
title: localeconv
ms.date: 4/2/2020
api_name:
- localeconv
- _o_localeconv
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a617980d60b3a12c06b30aab6cd457792a1aa770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342148"
---
# <a name="localeconv"></a>localeconv

获取区域设置的详细信息。

## <a name="syntax"></a>语法

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>返回值

**localeconv**返回指向类型[结构 lconv](../../c-runtime-library/standard-types.md)的填充对象的指针。 对象中包含的值从线程本地存储中的区域设置复制，并且可以通过后续调用**localeconv**覆盖。 对此对象中的值所做的更改不会修改区域设置。 使用**LC_ALL、LC_MONETARY**或**LC_NUMERIC**的*类别*值[设置局部性的](setlocale-wsetlocale.md)调用覆盖结构的内容。 **LC_MONETARY**

## <a name="remarks"></a>备注

**localeconv**函数获取有关当前区域设置的数字格式的详细信息。 此信息存储在 **lconv** 类型的结构中。 LOCALE.H 中定义的 **lconv** 结构，包含以下成员：

|字段|含义|
|-|-|
decimal_point<br/>_W_decimal_point|指向非货币量的十进制点字符。
thousands_sep，<br/>_W_thousands_sep|指向字符的指针，该字符将数字组分隔至非货币数量的十进制点左侧。
分组|指向**字符**大小的整数的指针，该整数包含以非货币数量表示的每组数字的大小。
int_curr_symbol<br/>_W_int_curr_symbol|指向当前区域设置的国际货币符号。 前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。 第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。
currency_symbol<br/>_W_currency_symbol|指向当前区域设置的本地货币符号。
mon_decimal_point<br/>_W_mon_decimal_point|指向货币数量的十进制点字符。
mon_thousands_sep<br/>_W_mon_thousands_sep|指向分隔符的指针，数字组以货币数量向小数位数左侧。
mon_grouping|指向**字符**大小的整数的指针，该整数包含每组数字的大小（以货币数量表示）。
positive_sign<br/>_W_positive_sign|非负货币数量的字符串指示符号。
negative_sign<br/>_W_negative_sign|负货币数量的字符串指示符号。
int_frac_digits|带国际格式的货币数量中小数点右侧的数字个数。
frac_digits|带格式的货币数量中小数点右侧的数字个数。
p_cs_precedes|如果货币符号位于带格式的非负货币数量值的前面，则设置为 1。 如果符号紧随值后，则设置为 0。
p_sep_by_space|如果货币符号通过空格与带格式的非负货币数量值分隔开来，则设置为 1。 如果没有空格分离，则设置为 0。
n_cs_precedes|如果货币符号位于带格式的负货币数量值的前面，则设置为 1。 如果符号紧随值后，则设置为 0。
n_sep_by_space|如果货币符号通过空格与带格式的负货币数量值分隔开来，则设置为 1。 如果没有空格分离，则设置为 0。
p_sign_posn|带格式的非负货币数量中的加号位置。
n_sign_posn|带格式的负货币数量中的加号位置。

除指定内容外，具有`char *`和`wchar_t *`版本的**lconv**结构的成员是指向字符串的指针。 对于**wchar_t），**<strong>\*</strong>任何等于 **""（** 或**L"）** 的）的长度为零，或者在当前区域设置中不支持。 请注意，**始终支持decimal_point**和 **_W_decimal_point**且长度为非零。

结构的**字符**成员是小非负数，而不是字符。 任何这些等于 **CHAR_MAX** 的成员在当前区域设置中不受支持。

**分组**和**mon_grouping**的值根据以下规则进行解释：

- **CHAR_MAX** - 不要执行任何进一步的分组。

- 0 - 对其余每个数字使用上一个元素。

- *n* - 构成当前组的位数。 检查下一个元素以确定当前组前下一组数字的大小。

根据以下规则解释 **int_curr_symbol** 的值：

- 前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。

- 第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。

根据以下规则（**n_cs_precedes**规则位于括号中）解释 **p_cs_precedes** 和 **n_cs_precedes** 的值：

- 0 - 货币符号遵循非负（负）格式货币值的值。

- 1 - 货币符号位于非负（负）格式货币值的值之前。

根据以下规则（**n_sep_by_space** 规则位于括号中）解释 **p_sep_by_space** 和 **n_sep_by_space** 的值：

- 0 - 货币符号与值由非负（负）格式化货币值的空间分隔。

- 1 - 货币符号和非负（负）格式货币值的值之间没有空间分隔。

根据以下规解释 **p_sign_posn** 和 **n_sign_posn** 的值：

- 0 - 括号环绕数量和货币符号。

- 1 - 符号字符串位于数量和货币符号之前。

- 2 - 符号字符串跟随数量和货币符号。

- 3 - 符号字符串紧接货币符号。

- 4 - 符号字符串紧随货币符号。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>另请参阅

[现场](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
