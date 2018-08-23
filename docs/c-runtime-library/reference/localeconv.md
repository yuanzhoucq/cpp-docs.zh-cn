---
title: localeconv | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- localeconv
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- localeconv
dev_langs:
- C++
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4e8a20ef31f4379e7ddf6b7425fd7ecc70294a
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2018
ms.locfileid: "42573017"
---
# <a name="localeconv"></a>localeconv

获取区域设置的详细信息。

## <a name="syntax"></a>语法

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>返回值

**localeconv**返回指向类型的填充的对象的指针[struct lconv](../../c-runtime-library/standard-types.md)。 对象中包含的值从线程本地存储中的区域设置设置复制，并对后续调用可以覆盖**localeconv**。 为此对象中的值所做的更改不修改的区域设置。 调用[setlocale](setlocale-wsetlocale.md)与*类别*的值**LC_ALL**， **LC_MONETARY**，或**LC_NUMERIC**覆盖该结构的内容。

## <a name="remarks"></a>备注

**Localeconv**函数获取有关当前区域设置的数字格式的详细的信息。 此信息存储在 **lconv** 类型的结构中。 LOCALE.H 中定义的 **lconv** 结构，包含以下成员：

|字段|含义|
|-|-|
decimal_point，<br/>_W_decimal_point|以十进制点非货币数量的字符的指针。
thousands_sep，<br/>_W_thousands_sep|字符的指针分隔到小数点左侧的非货币数量的数字进行分组。
分组|指向**char**-调整大小的整数，其中包含每个组的非货币数量中的数字的大小。
int_curr_symbol，<br/>_W_int_curr_symbol|指向当前区域设置的国际货币符号。 前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。 第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。
currency_symbol，<br/>_W_currency_symbol|指向当前区域设置的本地货币符号。
mon_decimal_point，<br/>_W_mon_decimal_point|以十进制点货币数量的字符的指针。
mon_thousands_sep，<br/>_W_mon_thousands_sep|指向货币数量中小数点位置左边的数字分隔符。
mon_grouping|指向**char**-调整大小的整数，它包含数字货币数量中每个组的大小。
positive_sign，<br/>_W_positive_sign|非负货币数量的字符串指示符号。
negative_sign，<br/>_W_negative_sign|负货币数量的字符串指示符号。
int_frac_digits|带国际格式的货币数量中小数点右侧的数字个数。
frac_digits|带格式的货币数量中小数点右侧的数字个数。
p_cs_precedes|如果货币符号位于带格式的非负货币数量值的前面，则设置为 1。 如果符号紧随值后，则设置为 0。
p_sep_by_space|如果货币符号通过空格与带格式的非负货币数量值分隔开来，则设置为 1。 如果没有空格分离，则设置为 0。
n_cs_precedes|如果货币符号位于带格式的负货币数量值的前面，则设置为 1。 如果符号紧随值后，则设置为 0。
n_sep_by_space|如果货币符号通过空格与带格式的负货币数量值分隔开来，则设置为 1。 如果没有空格分离，则设置为 0。
p_sign_posn|带格式的非负货币数量中的加号位置。
n_sign_posn|带格式的负货币数量中的加号位置。

除非有指定，成员**lconv**结构具有`char *`和`wchar_t *`版本都是指向字符串。 任何这些等于 **""** (或**L""** 有关**wchar_t \*** ) 是长度为零的或不支持当前区域设置中。 请注意， **decimal_point**并 **_W_decimal_point**始终受支持且长度为非零。

**Char**结构的成员是小的非负数字，不是字符。 任何这些等于 **CHAR_MAX** 的成员在当前区域设置中不受支持。

值**分组**并**mon_grouping**根据以下规则解释：

- **CHAR_MAX** -不执行任何分组。

- 0-使用上一个元素的每个剩余数字。

- *n* -构成当前组的数字个数。 检查下一个元素以确定当前组前下一组数字的大小。

根据以下规则解释 **int_curr_symbol** 的值：

- 前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。

- 第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。

根据以下规则（**n_cs_precedes**规则位于括号中）解释 **p_cs_precedes** 和 **n_cs_precedes** 的值：

- 0-货币符号位于非负 （负） 格式化货币值的值。

- 1-货币符号位于非负 （负） 格式化货币值的值。

根据以下规则（**n_sep_by_space** 规则位于括号中）解释 **p_sep_by_space** 和 **n_sep_by_space** 的值：

- 0-货币符号的非负 （负） 格式化货币值的空间值分隔。

- 1-货币符号和非负 （负） 格式化货币值的值之间没有空格分隔。

根据以下规解释 **p_sign_posn** 和 **n_sign_posn** 的值：

- 0-括号括起来的数量和货币符号。

- 1-符号字符串位于数量和货币符号。

- 2-符号字符串位于数量和货币符号。

- 3-符号字符串位于货币符号之前。

- 4-登录立即字符串如下所示的货币符号。

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
