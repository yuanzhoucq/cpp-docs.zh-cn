---
title: "localeconv | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "localeconv"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "localeconv"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "lconv 类型"
  - "localeconv 函数"
  - "区域设置, 获取相关信息"
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# localeconv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有关区域设置的 Gets 详细信息。  
  
## 语法  
  
```  
  
struct lconv *localeconv( void );  
```  
  
## 返回值  
 `localeconv` 返回一个指针指向一个填充 [结构 lconv](../../c-runtime-library/standard-types.md)类型的对象。  对象中包含的值可由对 `localeconv` 的后续调用都覆盖，不直接修改对象。  调用[地区控制](../../c-runtime-library/reference/setlocale-wsetlocale.md) 和 `category` 值 `LC_ALL`、`LC_MONETARY`或 `LC_NUMERIC` 重写结构的内容。  
  
## 备注  
 `localeconv` 函数为当前区域设置获取有关格式化数字的详细信息。  此信息存储在 **lconv**类型的结构中。  **lconv** 结构，在 LOCALE.H 定义，包含以下成员：  
  
 `char *decimal_point, wchar_t *_W_decimal_point`  
 非货币的小数点字符。  
  
 `char *thousands_sep, wchar_t *_W_thousands_sep`  
 字符数字进行分组，以非货币小数点左为准  
  
 `char *grouping`  
 在非货币的数量中每个组的数字的大小。  
  
 `char *int_curr_symbol, wchar_t *_W_int_curr_symbol`  
 当前区域设置的国际货币符号。  前三个字符指定按字母顺序的国际货币符号。在 *ISO 4217 编码针对货币和资金表示的规范* 标准中定义。  第四个字符 \(紧接在空字符之前\)从货币数量中分隔国际货币符号。  
  
 `char *currency_symbol, wchar_t *_W_currency_symbol`  
 当前区域设置的本地货币符号。  
  
 `char *mon_decimal_point, wchar_t *_W_mon_decimal_point`  
 货币数量的小数点字符。  
  
 `char *mon_thousands_sep, wchar_t *_W_mon_thousands_sep`  
 在货币数量中数字组的小数位置左侧的分隔符。  
  
 `char *mon_grouping`  
 在货币的数量中每个组的数字的大小。  
  
 `char *positive_sign, wchar_t *_W_positive_sign`  
 非负的货币数量的字符串表示符号。  
  
 `char *negative_sign, wchar_t *_W_negative_sign`  
 负的货币数量的字符串表示符号。  
  
 `char int_frac_digits`  
 在国际格式化的货币数量中数字的个数在小数点右侧的。  
  
 `char frac_digits`  
 在格式化的货币数量中数字的个数在小数点右侧的。  
  
 `char p_cs_precedes`  
 如果货币符号在非负格式化的货币数量的值之前，设置为 1。  如果符号在值之后，设置为 0。  
  
 `char p_sep_by_space`  
 如果货币符号从非负格式化货币数量的值中由空格分隔开。设置为 1。  如果没有空格分隔，设置为 0。  
  
 `char n_cs_precedes`  
 如果货币符号在负的格式化的货币数量的值之前，设置为 1。  如果符号在值之后，设置为 0。  
  
 `char n_sep_by_space`  
 如果货币符号在负的格式化货币数量的值中以空格分隔开。设置为 1。  如果没有空格分隔，设置为 0。  
  
 `char p_sign_posn`  
 非负格式化货币数量中正号的位置。  
  
 `char n_sign_posn`  
 负格式化货币数量中正号的位置。  
  
 具有 `char`、`*` 和 `wchar_t *` 版本的结构成员是字符串指针。  这些中的任何一个的等于`""`\(或`L""`为`wchar_t *` \)长度为零或者在当前区域设置中不被支持。  注意 `decimal_point` 和 `_W_decimal_point` 始终被支持并且是非零长度。  
  
 结构的 `char` 成员是小的非负数字，而不是字符。  这些中任何一个等于 **CHAR\_MAX** 在当前区域设置中不被支持。  
  
 **分组** 和 **mon\_grouping** 的元素根据下列规则被解释。  
  
 **CHAR\_MAX**  
 不执行任何其他分组。  
  
 0  
 为每一个剩余的数字使用以前的元素。  
  
 *n*  
 组成当前组的数字位数。  检查下一个元素用于在当前组之前确定下一个数字的组的大小。  
  
 **int\_curr\_symbol** 的值按照以下规则解释：  
  
-   前三个字符指定按字母顺序的国际货币符号,在 *ISO 4217 编码针对货币和资金表示的规范* 标准中定义。  
  
-   第四个字符 \(紧接在空字符之前\)将国际货币符号从货币数量分隔出来。  
  
 **p\_cs\_precedes** 和 **n\_cs\_precedes** 的值按照以下规则解释 \( **n\_cs\_precedes** 规则括号中\):  
  
 0  
 货币符号在非负 \(负\) 格式化货币值后面。  
  
 1  
 货币符号在非负 \(负\) 格式化货币值之前。  
  
 **p\_sep\_by\_space** 和 **n\_sep\_by\_space** 的值按照以下规则解释 \( **n\_sep\_by\_space** 规则在括号中\):  
  
 0  
 货币符号在非负（负）的格式化货币值中以空格分隔开。  
  
 1  
 在货币符号和非负 \(负\) 格式化货币值之间没有空格分隔。  
  
 **p\_sign\_posn** 和 **n\_sign\_posn** 的值按照以下规则解释：  
  
 0  
 括号中包括数量和货币符号。  
  
 1  
 符号字符串在数目和货币符号之前。  
  
 2  
 符号字符串在数目和货币符号之后。  
  
 3  
 符号字符串仅先于货币符号。  
  
 4  
 符号字符串后面紧跟货币符号。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`localeconv`|\<locale.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 请参阅  
 [区域设置](../../c-runtime-library/locale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)