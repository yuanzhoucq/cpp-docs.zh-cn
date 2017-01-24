---
title: "strtod、_strtod_l、wcstod、_wcstod_l | Microsoft Docs"
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
  - "wcstod"
  - "_wcstod_l"
  - "_strtod_l"
  - "strtod"
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
  - "_tcstod"
  - "strtod"
  - "wcstod"
  - "_strtod_l"
  - "_wcstod_l"
  - "stdlib/strtod"
  - "corecrt_wstdlib/wcstod"
  - "stdlib/_strtod_l"
  - "corecrt_wstdlib/_wcstod_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtod_l 函数"
  - "_tcstod 函数"
  - "_tcstod_l 函数"
  - "_wcstod_l 函数"
  - "字符串转换, 为浮点值"
  - "strtod 函数"
  - "strtod_l 函数"
  - "tcstod 函数"
  - "tcstod_l 函数"
  - "wcstod 函数"
  - "wcstod_l 函数"
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
caps.latest.revision: 20
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strtod、_strtod_l、wcstod、_wcstod_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

字符串转换为双精度值。  
  
## 语法  
  
```  
double strtod(  
   const char *nptr,  
   char **endptr   
);  
double _strtod_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
double wcstod(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
double wcstod_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `nptr`  
 要转换的 null 终止的字符串。  
  
 `endptr`  
 指向停止扫描字符的指针。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 除非表示形式导致溢出（在这种情况下，函数返回 \+\/\-`HUGE_VAL`），否则 `strtod` 返回浮点数的值。  `HUGE_VAL` 的符号匹配无法表示的值的符号。  如果不能执行转换或发生下溢，则 `strtod` 返回 0。  
  
 `wcstod` 返回值类似于 `strtod`。  对于两个函数，如果出现溢出或下溢且包含无效参数处理程序，请将 `errno` 设置为 `ERANGE`，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  
  
 有关这个和其他返回代码的更多信息，请参见 [\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 每个函数将输入的字符串 `nptr` 转换为 `double`。  `strtod` 函数将 `nptr` 转换成长双精度值。  `strtod` 在发现第一个不能将其识别为数字的字符时，将停止读入字符串 `nptr`。  这可能是终止 null 字符。  `wcstod` 是 `strtod` 的宽字符版本；其 `nptr` 参数是宽字符字符串。  否则这些函数具有相同行为。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS 未定义|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstod`|`strtod`|`strtod`|`wcstod`|  
|`_tcstod_l`|`_strtod_l`|`_strtod_l`|`_wcstod_l`|  
  
 当前区域设置的 `LC_NUMERIC` 类别设置决定`nptr` 中基数字符的识别*;* 有关详细信息，请参阅 [区域设置](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  不带 `_l` 后缀的函数使用当前区域设置；`_strtod_l` 与 `_strtod_l` 相同，只不过它们使用的是传递的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不为 `NULL`，停止扫描的字符指针将存储在 `endptr` 指向的位置。  如果没有转换（未找到有效数字或指定了无效基础），`nptr` 的值存储在 `endptr` 指向的位置。  
  
 `strtod` 希望 `nptr` 指向以下格式的字符串：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\] \[`.digits`\] \[ {`d` &#124; `D` &#124; `e` &#124; `E`}\[`sign`\]`digits`\]  
  
 `whitespace` 可能包含已忽略的空格和制表符；`sign` 是加号 \(`+`\) 或减号 \(`–`\)；而 `digits` 是一个或多个十进制数字。  如果在基数字符前面没有出现数字，则至少基数字符后面应有一个数字。  十进制数字后跟指数，包括一个介绍性字母（`d`、`D`、`e` 或 `E`）和一个可选带符号整数。  如果指数部分和基数字符均未出现，则基数字符假定后跟该字符串的最后一位数。  不符合此窗体的首个字符将终止扫描。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strtod`, `_strtod_l`|\<stdlib.h\>|  
|`wcstod`, `_wcstod_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strtod.c  
// This program uses strtod to convert a  
// string to a double-precision value; strtol to  
// convert a string to long integer values; and strtoul  
// to convert a string to unsigned long-integer values.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char   *string, *stopstring;  
   double x;  
   long   l;  
   int    base;  
   unsigned long ul;  
  
   string = "3.1415926This stopped it";  
   x = strtod( string, &stopstring );  
   printf( "string = %s\n", string );  
   printf("   strtod = %f\n", x );  
   printf("   Stopped scan at: %s\n\n", stopstring );  
  
   string = "-10110134932This stopped it";  
   l = strtol( string, &stopstring, 10 );  
   printf( "string = %s\n", string );  
   printf("   strtol = %ld\n", l );  
   printf("   Stopped scan at: %s\n\n", stopstring );  
  
   string = "10110134932";  
   printf( "string = %s\n", string );  
  
   // Convert string using base 2, 4, and 8:  
   for( base = 2; base <= 8; base *= 2 )  
   {  
      // Convert the string:  
      ul = strtoul( string, &stopstring, base );  
      printf( "   strtol = %ld (base %d)\n", ul, base );  
      printf( "   Stopped scan at: %s\n", stopstring );  
   }  
}  
```  
  
  **字符串 \= 3.1415926这停止了它**  
 **strtod \= 3.141593**  
 **已停止的扫描：这停止了它**  
**string \= \-10110134932这停止了它**  
 **strtol \= \-2147483648**  
 **已停止的扫描：这停止了它**  
**字符串 \= 10110134932**  
 **strtol \= 45 \(base 2\)**  
 **在：34932停止扫描**  
 **strtol \= 4423 \(base 4\)**  
 **在：4932停止扫描**  
 **strtol \= 2134108 \(base 8\)**  
 **在：932停止扫描**   
## .NET Framework 等效项  
 [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtol、wcstol、\_strtol\_l、\_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)