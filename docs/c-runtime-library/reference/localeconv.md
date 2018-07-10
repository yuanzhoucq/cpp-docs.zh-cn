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
ms.openlocfilehash: fe3cc75430dfa9bb2f4c5513f4b2ba5a2fd1c4c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405245"
---
# <a name="localeconv"></a>localeconv

获取区域设置的详细信息。

## <a name="syntax"></a>语法

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>返回值

**localeconv**返回指向类型的填入对象的指针[结构 lconv](../../c-runtime-library/standard-types.md)。 该对象中包含的值，从复制中线程本地存储的区域设置设置后续调用可以覆盖**localeconv**。 对此对象中的值所做更改不修改的区域设置。 调用[setlocale](setlocale-wsetlocale.md)与*类别*值**LC_ALL**， **LC_MONETARY**，或**LC_NUMERIC**覆盖结构的内容。

## <a name="remarks"></a>备注

**Localeconv**函数获取有关当前区域设置的数值格式的详细的信息。 此信息存储在 **lconv** 类型的结构中。 LOCALE.H 中定义的 **lconv** 结构，包含以下成员：

|字段|含义|
|-|-|
decimal_point，<br/>_W_decimal_point|要小数点的非货币性数量的字符指针。
thousands_sep，<br/>_W_thousands_sep|指针，用以字符分隔的非货币性数量的小数点左边数字组。
分组|指向**char**-大小包含每个组中非货币性数量的数字大小的整数。
int_curr_symbol，<br/>_W_int_curr_symbol|指向当前区域设置的国际货币符号的指针。 前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。 第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。
currency_symbol，<br/>_W_currency_symbol|指向当前区域设置的本地货币符号的指针。
mon_decimal_point，<br/>_W_mon_decimal_point|以十进制点资金数量的字符的指针。
mon_thousands_sep，<br/>_W_mon_thousands_sep|指向左侧在资金数量的小数位的数字组分隔符。
mon_grouping|指向**char**-大小包含每个组的位数资金数量大小的整数。
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

除指定，成员**lconv**结构中具有`char *`和`wchar_t *`版本是指向字符串的指针。 任一这些等于 **""** (或**L""** 为**wchar_t \*** ) 是长度为零或不受支持的当前区域设置中。 请注意， **decimal_point**和 **_W_decimal_point**是否始终支持和的长度不为零。

**Char**结构成员是小的非负数字，不是字符。 任何这些等于 **CHAR_MAX** 的成员在当前区域设置中不受支持。

值**分组**和**mon_grouping**解释根据下列规则：

- **CHAR_MAX** -不执行任何进一步分组。

- 0-使用为每个剩余的数字的上一个元素。

- *n* -构成当前组的位数。 检查下一个元素以确定当前组前下一组数字的大小。

根据以下规则解释 **int_curr_symbol** 的值：

- 前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。

- 第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。

根据以下规则（**n_cs_precedes**规则位于括号中）解释 **p_cs_precedes** 和 **n_cs_precedes** 的值：

- 0-为非负数 （负号） 的格式化货币值的值货币符号后面。

- 1-货币符号之前的非负数 （负号） 的格式化货币值的值。

根据以下规则（**n_sep_by_space** 规则位于括号中）解释 **p_sep_by_space** 和 **n_sep_by_space** 的值：

- 0-货币符号被分开的非负数 （负号） 的格式化货币值的空间的值。

- 1-没有无需空间分离的货币符号和非负 （负号） 的格式化货币值的值。

根据以下规解释 **p_sign_posn** 和 **n_sign_posn** 的值：

- 0-括号括起的数量和货币符号。

- 1-登录字符串之前数量和货币符号。

- 2-登录字符串之后数量和货币符号。

- 3-登录字符串紧跟货币符号。

- 4-登录立即字符串如下所示货币符号。

## <a name="requirements"></a>要求

|例程|必需的标头|
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
