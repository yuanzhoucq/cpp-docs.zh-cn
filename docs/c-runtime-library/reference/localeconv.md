---
title: "localeconv | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e93e21505a661deb470e4b31c8807ef5133a774
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="localeconv"></a>localeconv
获取区域设置的详细信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct lconv *localeconv( void );  
```  
  
## <a name="return-value"></a>返回值  
 `localeconv` 返回指向类型为 [struct lconv](../../c-runtime-library/standard-types.md) 的已填写对象的指针。 该对象中包含的值，从复制中线程本地存储的区域设置设置后续调用可以覆盖`localeconv`。 对此对象中的值所做更改不修改的区域设置。 使用 `LC_ALL`、`LC_MONETARY` 或 `LC_NUMERIC` 的 `category` 值调用 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 将覆盖该结构的内容。  
  
## <a name="remarks"></a>备注  
 `localeconv` 函数获取有关当前区域设置的数字格式的详细信息。 此信息存储在类型的结构`lconv`。 `lconv`区域设置中定义的结构。H，包含以下成员：  
  
 `char *decimal_point, wchar_t *_W_decimal_point`  
 非货币数量的小数点字符。  
  
 `char *thousands_sep, wchar_t *_W_thousands_sep`  
 将数字组分隔到小数点左边的非货币数量的字符。  
  
 `char *grouping`  
 指向`char`-大小包含每个组中非货币性数量的数字大小的整数。  
  
 `char *int_curr_symbol, wchar_t *_W_int_curr_symbol`  
 当前区域设置的国际货币符号。 前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。 第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。  
  
 `char *currency_symbol, wchar_t *_W_currency_symbol`  
 当前区域设置的本地货币符号。  
  
 `char *mon_decimal_point, wchar_t *_W_mon_decimal_point`  
 货币数量的小数点字符。  
  
 `char *mon_thousands_sep, wchar_t *_W_mon_thousands_sep`  
 货币数量中将数字组分隔到小数点位置左边的分隔符。  
  
 `char *mon_grouping`  
 指向`char`-大小包含每个组的位数资金数量大小的整数。  
  
 `char *positive_sign, wchar_t *_W_positive_sign`  
 非负货币数量的字符串指示符号。  
  
 `char *negative_sign, wchar_t *_W_negative_sign`  
 负货币数量的字符串指示符号。  
  
 `char int_frac_digits`  
 带国际格式的货币数量中小数点右侧的数字个数。  
  
 `char frac_digits`  
 带格式的货币数量中小数点右侧的数字个数。  
  
 `char p_cs_precedes`  
 如果货币符号位于带格式的非负货币数量值的前面，则设置为 1。 如果符号紧随值后，则设置为 0。  
  
 `char p_sep_by_space`  
 如果货币符号通过空格与带格式的非负货币数量值分隔开来，则设置为 1。 如果没有空格分离，则设置为 0。  
  
 `char n_cs_precedes`  
 如果货币符号位于带格式的负货币数量值的前面，则设置为 1。 如果符号紧随值后，则设置为 0。  
  
 `char n_sep_by_space`  
 如果货币符号通过空格与带格式的负货币数量值分隔开来，则设置为 1。 如果没有空格分离，则设置为 0。  
  
 `char p_sign_posn`  
 带格式的非负货币数量中的加号位置。  
  
 `char n_sign_posn`  
 带格式的负货币数量中的加号位置。  
  
除指定，成员`lconv`结构中具有`char *`和`wchar_t *`版本是指向字符串的指针。 任何等于 `""`（或 `wchar_t *` 的 `L""`） 的成员长度为零，或在当前区域设置中不受支持。 请注意，`decimal_point` 和 `_W_decimal_point` 始终受支持且长度为非零。  
  
结构为 `char` 的成员是小的非负数字，不是字符。 任一这些等于`CHAR_MAX`的当前区域设置中不支持。  
  
值`grouping`和`mon_grouping`解释根据下列规则：  
  
- `CHAR_MAX` -不执行任何进一步分组。  
  
- 0-使用为每个剩余的数字的上一个元素。  
  
- *n* -构成当前组的数字个数。 检查下一个元素以确定当前组前下一组数字的大小。  
  
值`int_curr_symbol`解释根据下列规则：  
  
-   前三个字符指定字母国际货币符号，如*货币和资金表示形式的 ISO 4217 代码*标准中定义。  
  
-   第四个字符（前面紧邻 null 字符）将国际货币符号与货币数量分隔开来。  
  
值`p_cs_precedes`和`n_cs_precedes`解释根据以下规则 (`n_cs_precedes`规则位于括号中):  
  
- 0-为非负数 （负号） 的格式化货币值的值货币符号后面。  
  
- 1-货币符号之前的非负数 （负号） 的格式化货币值的值。  
  
值`p_sep_by_space`和`n_sep_by_space`解释根据以下规则 (`n_sep_by_space`规则位于括号中):  
  
- 0-货币符号被分开的非负数 （负号） 的格式化货币值的空间的值。  
  
- 1-没有无需空间分离的货币符号和非负 （负号） 的格式化货币值的值。  
  
值`p_sign_posn`和`n_sign_posn`解释根据下列规则：  
  
- 0-括号括起的数量和货币符号。  
  
- 1-登录字符串之前数量和货币符号。  
  
- 2-登录字符串之后数量和货币符号。  
  
- 3-登录字符串紧跟货币符号。  
  
- 4-登录立即字符串如下所示货币符号。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`localeconv`|\<locale.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="see-also"></a>请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)