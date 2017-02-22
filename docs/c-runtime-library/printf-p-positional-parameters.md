---
title: "printf_p 位置参数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_printf_p 函数, 位置参数"
  - "printf_p 函数, 位置参数"
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# printf_p 位置参数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

位置参数可以按要替换到格式字符串中字段的参数的编号进行指定。  以下位置参数 `printf` 函数可用：  
  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)  
 [\_printf\_p、\_printf\_p\_l、\_wprintf\_p、\_wprintf\_p\_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)  
  
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)  
 [\_sprintf\_p, \_sprintf\_p\_l, \_swprintf\_p, \_swprintf\_p\_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)  
  
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)  
 [\_cprintf\_p、\_cprintf\_p\_l、\_cwprintf\_p、\_cwprintf\_p\_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)  
  
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)  
 [\_fprintf\_p、\_fprintf\_p\_l、\_fwprintf\_p、\_fwprintf\_p\_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)  
  
 [vprintf、\_vprintf\_l、vwprintf、\_vwprintf\_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)  
 [\_vprintf\_p、\_vprintf\_p\_l、\_vwprintf\_p、\_vwprintf\_p\_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)  
  
 [vfprintf、\_vfprintf\_l、vfwprintf、\_vfwprintf\_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)  
 [\_vfprintf\_p、\_vfprintf\_p\_l、\_vfwprintf\_p、\_vfwprintf\_p\_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)  
  
 [vsprintf、\_vsprintf\_l、vswprintf、\_vswprintf\_l、\_\_vswprintf\_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)  
 [\_vsprintf\_p、\_vsprintf\_p\_l、\_vswprintf\_p、\_vswprintf\_p\_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)  
  
## 指定位置参数  
  
##### 参数索引  
 默认情况下，如果不存在位置格式，则位置函数的行为与非位置函数的行为相同。  位置参数通过使用格式“`%m$x`”进行指定，其中 `m` 是指示参数在整个参数列表中所处位置的数字序号，位于格式字符串的前面，而  `x` 表示 `printf` 函数中指定的类型字段字符类型。  列表中的第一个元素对应值 1，依此类推，对列表中的参数进行索引。  有关类型字段字符的其他信息，请参阅 [printf 类型字段字符](../c-runtime-library/printf-type-field-characters.md)。  
  
 此行为的示例：  
  
```  
_printf_p("%1$s %2$s", "November", "10");  
```  
  
 将打印  
  
```  
November 10  
```  
  
 所使用的数字顺序不需要与给定的自变量顺序匹配。  因此，以下行为有效：  
  
```  
_printf_p("%2$s %1$s", "November", "10");  
```  
  
 将打印  
  
```  
10 November  
```  
  
 当格式化时，可能会不止一次使用参数，这与传统的格式字符串不同，因此  
  
```  
_printf_p("%1$d times %1$d is %2$d", 10, 100);  
```  
  
 将打印  
  
```  
10 times 10 is 100  
```  
  
 但是，所有自变量都必须在格式字符串中的某个位置至少使用一次。  
  
 格式字符串中允许的位置参数的最大数量由 `_ARGMAX` 指定。  
  
##### 宽度和精度  
 当使用 \* 符号指定将从自变量确定宽度或精度时，宽度或精度值的位置必须立即出现在 \* 符号后面。  例如，  
  
```  
_printf_p("%1$*2$s","Hello", 10);  
```  
  
 或  
  
```  
_printf_p("%2$*1$s",10, "Hello");  
```  
  
##### 混合位置和非位置自变量  
 在同一格式字符串中，不得混用位置参数与非位置参数。  但是，`printf_p` 和相关函数仍然支持在不包含位置参数的格式字符串中使用非位置参数。  
  
## 示例  
  
```  
// positional_args.c  
// Positional arguments allow the specification of the order  
// in which arguments are consumed in a formatting string.  
  
#include <stdio.h>  
  
int main(int argc, char *argv[])  
{  
    int     i = 1,  
            j = 2,  
            k = 3;  
    double  x = 0.1,  
            y = 0.2,  
            z = 0.3;  
    char    *s1 = "abc",  
            *s2 = "def",  
            *s3 = "ghi";  
  
    // If positional arguments are unspecified,  
    // normal input order is used.  
    _printf_p("%d %d %d\n", i, j, k);  
  
    // Positional args are numbers indicating the  
    // argument enclosed in curly braces.  
    _printf_p("%3$d %1$d %2$d\n", i, j, k);  
  
    // The same positional argument may be reused.  
    _printf_p("%1$d %2$d %1$d\n", i, j);  
  
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);  
  
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);  
}  
```  
  
  **1 2 3**  
**3 1 2**  
**1 2 1**  
**abc def ghi**  
**ghi abc def**   
## 请参阅  
 [printf 类型字段字符](../c-runtime-library/printf-type-field-characters.md)   
 [printf 宽度规范](../c-runtime-library/printf-width-specification.md)   
 [精度规范](../c-runtime-library/precision-specification.md)