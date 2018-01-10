---
title: "printf_p 位置参数 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords:
- _printf_p function, positional parameters
- printf_p function, positional parameters
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 10d48a899b2d2e6ad644c385c2b2116353c20f8e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="printfp-positional-parameters"></a>printf_p 位置参数
位置参数可以按要替换到格式字符串中字段的自变量的编号进行指定。 以下位置参数 `printf` 函数可用：  
  
| 非位置 printf 函数 | 位置参数等效项 |  
|---|---|  
|[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|  
|[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|  
|[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)|  
|[fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|  
|[vprintf、_vprintf_l、vwprintf、_vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p、_vprintf_p_l、_vwprintf_p、_vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|  
|[vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|  
|[vsprintf、_vsprintf_l、vswprintf、_vswprintf_l、\__vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|  
  
## <a name="how-to-specify-positional-parameters"></a>如何指定位置参数  
  
### <a name="parameter-indexing"></a>参数索引  
默认情况下，如果不存在位置格式，则位置函数的行为与非位置函数的行为相同。 在格式说明符开头使用 `%n$` 可将位置参数指定为格式化，其中 `n` 是参数列表中要格式化的参数位置。 格式字符串之后，第一个参数的参数位置从 1 开始。 格式说明符的其余部分遵循与 `printf` 格式说明符相同的规则。 有关格式说明符的详细信息，请参阅[格式规范语法：printf 和 wprintf 函数](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
下面是位置格式的示例：  
  
```C  
_printf_p("%1$s %2$s", "November", "10");  
```  
  
显示为：  
  
```  
November 10  
```  
  
所使用的数字顺序不需要与自变量顺序匹配。 例如，下面是一个有效的格式字符串：  
  
```C  
_printf_p("%2$s %1$s", "November", "10");  
```  
  
显示为：  
  
```  
10 November  
```  
  
与传统的格式字符串不同，位置参数可多次在格式字符串中使用。 例如，应用于对象的  
  
```C  
_printf_p("%1$d times %1$d is %2$d", 10, 100);  
```  
  
显示为：  
  
```  
10 times 10 is 100  
```  
  
所有自变量都必须在格式字符串中的某个位置至少使用一次。 格式字符串中允许的位置参数的最大数量由 `_ARGMAX` 指定。  
  
### <a name="width-and-precision"></a>宽度和精度  
可以使用 `*n$` 指定位置参数作为宽度或精度说明符，其中 `n` 是参数列表中的宽度或精度参数。 宽度或精度值的位置必须紧跟 \* 符号出现。 例如，应用于对象的  
  
```C  
_printf_p("%1$*2$s","Hello", 10);  
```  
  
或  
  
```C  
_printf_p("%2$*1$s", 10, "Hello");  
```  
  
### <a name="mixing-positional-and-non-positional-arguments"></a>混合位置和非位置参数  
在同一格式字符串中，不得混用位置参数与非位置参数。 如果使用任何位置格式，则所有格式说明符都必须使用位置格式。 但是，`printf_p` 和相关函数仍然支持在不包含位置参数的格式字符串中使用非位置参数。  
  
## <a name="example"></a>示例  
  
```C  
// positional_args.c  
// Build by using: cl /W4 positional_args.c  
// Positional arguments allow the specification of the order  
// in which arguments are consumed in a formatting string.  
  
#include <stdio.h>  
  
int main()  
{  
    int     i = 1,  
            j = 2,  
            k = 3;  
    double  x = 0.1,  
            y = 2.22,  
            z = 333.3333;  
    char    *s1 = "abc",  
            *s2 = "def",  
            *s3 = "ghi";  
  
    // If positional arguments are unspecified,  
    // normal input order is used.  
    _printf_p("%d %d %d\n", i, j, k);  
  
    // Positional arguments are numbers followed by a $ character.  
    _printf_p("%3$d %1$d %2$d\n", i, j, k);  
  
    // The same positional argument may be reused.  
    _printf_p("%1$d %2$d %1$d\n", i, j);  
  
    // The positional arguments may appear in any order.
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);  
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);  
  
    // Precision and width specifiers must be int types.  
    _printf_p("%3$*5$f %2$.*4$f %1$*4$.*5$f\n", x, y, z, j, k);  
}  
```  
  
```Output  
1 2 3
3 1 2
1 2 1
abc def ghi
ghi abc def
333.333300 2.22 0.100
```  
  
## <a name="see-also"></a>请参阅  
 [格式规范语法：printf 和 wprintf 函数](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)