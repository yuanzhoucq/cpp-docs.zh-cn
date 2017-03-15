---
title: "atof、_atof_l、_wtof、_wtof_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wtof_l"
  - "atof"
  - "_atof_l"
  - "_wtof"
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
  - "_tstof"
  - "_ttof"
  - "atof"
  - "stdlib/atof"
  - "math/atof"
  - "_atof_l"
  - "stdlib/_atof_l"
  - "math/_atof_l"
  - "_wtof"
  - "corecrt_wstdlib/_wtof"
  - "_wtof_l"
  - "corecrt_wstdlib/_wtof_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tstof 函数"
  - "atof_l 函数"
  - "_atof_l 函数"
  - "atof 函数"
  - "_tstof 函数"
  - "_ttof 函数"
  - "wtof 函数"
  - "_wtof_l 函数"
  - "ttof 函数"
  - "wtof_l 函数"
  - "_wtof 函数"
  - "字符串转换, 为浮点值"
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# atof、_atof_l、_wtof、_wtof_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为双精度。  
  
## 语法  
  
```  
double atof(  
   const char *str   
);  
double _atof_l(  
   const char *str,  
   _locale_t locale  
);  
double _wtof(  
   const wchar_t *str   
);  
double _wtof_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 要转换的字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 每个函数返回 `double` 值，此值由将输入字符作为数字解析而生成。  如果该输入无法转换为该类型的值，则返回值为 0.0。  
  
 在所有超出范围的情况下，errno设置为`ERANGE`。  如果传递的参数为 `NULL`，则调用无效的参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回 0。  
  
## 备注  
 这些函数将字符串转换为双精度浮点值。  
  
 输入字符串是可被解释为指定类型的数值的字符序列。  当第一个字符不能识别为数字时，函数将停止读入输入字符串。  此字符可能是终止字符串的 null 字符（'\\0' 或 L'\\0'）。  
  
 `atof` 和 `_wtof` 的 `str` 参数具有以下格式：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\] \[`.digits`\] \[ {`d` &#124; `D` &#124; `e` &#124; `E` }\[`sign`\]`digits`\]  
  
 `whitespace` 包含已忽略的空格或制表符；`sign` 是加号 \(\+\) 或减号 \(\-\)；而 `digits` 是一个或多个十进制数字。  如果数字没在小数点出现之前，至少一个必须在小数点后显示。  十进制数字后跟指数，包括一个介绍性字母（`d`、`D`、`e` 或 `E`）和一个可选带符号十进制整数。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE& 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tstof`|`atof`|`atof`|`_wtof`|  
|`_ttof`|`atof`|`atof`|`_wtof`|  
  
## 要求  
  
|Routine\(s\)|必需的标头|  
|------------------|-----------|  
|`atof`|\<math.h\> and \<stdlib.h\>|  
|`_atof_l`|\<math.h\> and \<stdlib.h\>|  
|`_wtof`, `_wtof_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
## 示例  
 此过程演示如何使用 `atof` 函数将作为字符串存储的数字转换为数值。  
  
```  
// crt_atof.c  
//  
// This program shows how numbers stored as   
// strings can be converted to numeric  
// values using the atof function.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    double  value = 0;  
  
    // An example of the atof function  
    // using leading and training spaces.  
    str = "  3336402735171707160320 ";  
    value = atof( str );  
    printf( "Function: atof( \"%s\" ) = %e\n", str, value );  
  
    // Another example of the atof function  
    // using the 'd' exponential formatting keyword.  
    str = "3.1412764583d210";  
    value = atof( str );  
    printf( "Function: atof( \"%s\" ) = %e\n", str, value );  
  
    // An example of the atof function  
    // using the 'e' exponential formatting keyword.  
    str = "  -2309.12E-15";  
    value = atof( str );  
    printf( "Function: atof( \"%s\" ) = %e\n", str, value );  
  
}  
```  
  
  **Function: atof\( " 3336402735171707160320 " \) \= 3.336403e\+021**  
**Function: atof\( "3.1412764583d210" \) \= 3.141276e\+210**  
**Function: atof\( " \-2309.12E\-15" \) \= \-2.309120e\-012**   
## .NET Framework 等效项  
  
-   [System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)  
  
-   [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_atodbl, \_atodbl\_l, \_atoldbl, \_atoldbl\_l, \_atoflt, \_atoflt\_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)