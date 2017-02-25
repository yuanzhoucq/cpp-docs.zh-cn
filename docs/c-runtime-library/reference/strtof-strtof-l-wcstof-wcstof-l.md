---
title: "strtof、_strtof_l、wcstof、_wcstof_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strtof_l"
  - "wcstof"
  - "strtof"
  - "_wcstof_l"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcstof"
  - "_tcstof_l"
  - "stdlib/strtof"
  - "strtof"
  - "stdlib/_strtof_l"
  - "_strtof_l"
  - "corecrt_wstdlib/wcstof"
  - "wcstof"
  - "corecrt_wstdlib/_wcstof_l"
  - "_wcstof_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtof_l 函数"
  - "_tcstof 函数"
  - "_tcstof_l 函数"
  - "_wcstof_l 函数"
  - "strtof 函数"
  - "wcstof 函数"
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# strtof、_strtof_l、wcstof、_wcstof_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为单精度浮点值。  
  
## 语法  
  
```  
float strtof(  
   const char *nptr,  
   char **endptr   
);  
float _strtof_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
float wcstof(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
float wcstof_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `nptr`  
 要转换的 null 终止的字符串。  
  
 `endptr`  
 指向停止扫描的字符的指针。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 除非表示形式导致溢出（在这种情况下，函数返回 \+\/\-`HUGE_VALF`），否则 `strtof` 返回浮点数的值。  `HUGE_VALF` 的符号匹配无法表示的值的符号。  如果不能执行转换或发生下溢，则 `strtof` 返回 0。  
  
 `wcstof` 返回值类似于 `strtof`。  对于两个函数，如果出现溢出或下溢且包含无效参数处理程序，请将 `errno` 设置为 `ERANGE`，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  
  
 有关返回代码的详细信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 每个函数将输入的字符串 `nptr` 转换为 `float`。  `strtof` 函数将 `nptr` 转换成单精度值。  `strtof` 在发现第一个不能将其识别为数字的字符时，将停止读入字符串 `nptr`。  这可能是终止 null 字符。  `wcstof` 是 `strtof` 的宽字符版本；其 `nptr` 参数是宽字符字符串。  否则这三个函数否则具有相同行为。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstof`|`strtof`|`strtof`|`wcstof`|  
|`_tcstof_l`|`_strtof_l`|`_strtof_l`|`_wcstof_l`|  
  
 当前区域设置的 `LC_NUMERIC` 类别设置确定 `nptr` 中基数字符的识别；有关详细信息，请参阅 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  无 `_l` 后缀的函数使用当前区域设置；有后缀的函数与其相同，只不过它们改用传递的区域设置。  有关详细信息，请参阅 [区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不为 `NULL`，停止扫描的字符指针将存储在 `endptr` 指向的位置。  如果不能指向转换（未找到有效数字或指定了无效基础），`nptr` 的值存储在 `endptr` 指向的位置。  
  
 `strtof` 希望 `nptr` 指向以下格式的字符串：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\] \[`.digits`\] \[ {`d` &#124; `D` &#124; `e` &#124; `E`}\[`sign`\]`digits`\]  
  
 `whitespace` 可能包含已忽略的空格和制表符；`sign` 是加号 \(`+`\) 或减号 \(`–`\)；而 `digits` 是一个或多个十进制数字。  如果在基数字符前面没有出现数字，则至少基数字符后面应有一个数字。  十进制数字后跟指数，包括一个介绍性字母（`d`、`D`、`e` 或 `E`）和一个可选带符号整数。  如果指数部分和基数字符均未出现，则基数字符假定后跟该字符串的最后一位数。  不符合此窗体的首个字符将终止扫描。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strtof`, `_strtof_l`|\<stdlib.h\>|  
|`wcstof`, `_wcstof_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strtof.c  
// This program uses strtof to convert a  
// string to a single-precision value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *string;  
   char *stopstring;  
   float x;  
  
   string = "3.14159This stopped it";  
   x = strtof(string, &stopstring);  
   printf("string = %s\n", string);  
   printf("   strtof = %f\n", x);  
   printf("   Stopped scan at: %s\n\n", stopstring);  
}  
```  
  
  **字符串 \= 3.14159 这停止了它**  
 **strtof \= 3.141590**  
 **已停止的扫描：这停止了它**   
## .NET Framework 等效项  
 [System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、\_strtod\_l、wcstod、\_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol、wcstol、\_strtol\_l、\_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)