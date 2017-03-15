---
title: "atoi、_atoi_l、_wtoi、_wtoi_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wtoi"
  - "_wtoi_l"
  - "atoi"
  - "_atoi_l"
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
  - "_tstoi"
  - "_wtoi"
  - "_ttoi"
  - "atoi"
  - "_atoi_l"
  - "_wtoi_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_atoi_l 函数"
  - "ttoi 函数"
  - "atoi_l 函数"
  - "字符串转换, 为整数"
  - "_wtoi 函数"
  - "wtoi_l 函数"
  - "tstoi 函数"
  - "_ttoi 函数"
  - "_tstoi 函数"
  - "_wtoi_l 函数"
  - "atoi 函数"
  - "wtoi 函数"
ms.assetid: ad7fda30-28ab-421f-aaad-ef0b8868663a
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# atoi、_atoi_l、_wtoi、_wtoi_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convert a string to integer.  
  
## 语法  
  
```  
int atoi(  
   const char *str   
);  
int _wtoi(  
   const wchar_t *str   
);  
int _atoi_l(  
   const char *str,  
   _locale_t locale  
);  
int _wtoi_l(  
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
 每个函数返回 `int` 值，此值由将输入字符作为数字解析而生成。  如果该输入无法转换为该类型的值，则 `atoi` 和`_wtoi` 的返回值为 0。  
  
 对于使用大量负整数值的溢出，则返回 `LONG_MIN`。  `atoi` 和 `_wtoi` 返回 `INT_MAX` 和 `INT_MIN` 对这些条件。  在所有超出范围的情况下，`errno` 设置为 `ERANGE`。  如果传递的参数为 `NULL`，则调用无效的参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回 0。  
  
## 备注  
 这些函数将字符串转换为整数值\(`atoi` 和 `_wtoi`\)。  输入字符串是可被解释为指定类型的数值的字符序列。  当第一个字符不能识别为数字时，函数将停止读入输入字符串。  此字符可能是终止字符串的 null 字符（'\\0' 或 L'\\0'）。  
  
 `str` 参数传到 `atoi` ``  和 `_wtoi` 具有以下格式：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\]\]  
  
 `whitespace` 包含已忽略的空格或制表符；`sign` 是加号 \(\+\) 或减号 \(\-\)；而 `digits` 是一个或多个数字。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE& 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tstoi`|`atoi`|`atoi`|`_wtoi`|  
|`_ttoi`|`atoi`|`atoi`|`_wtoi`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`atoi`|\<stdlib.h\>|  
|`_atoi_l`, `_wtoi`, `_wtoi_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
## 示例  
 此过程演示如何使用 `atoi` 函数将作为字符串存储的数字转换为数值。  
  
```  
// crt_atoi.c  
// This program shows how numbers   
// stored as strings can be converted to  
// numeric values using the atoi functions.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    int     value = 0;  
  
    // An example of the atoi function.  
    str = "  -2309 ";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function.  
    str = "31412764";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function   
    // with an overflow condition occuring.  
    str = "3336402735171707160320";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **函数：atoi\( " \-2309 " \) \= \-2309**  
**Function: atoi\( "31412764" \) \= 31412764**  
**Function: atoi\( "3336402735171707160320" \) \= 2147483647**  
**发生了溢出条件。**   
## .NET Framework 等效项  
  
-   [System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)  
  
-   [System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_atodbl, \_atodbl\_l, \_atoldbl, \_atoldbl\_l, \_atoflt, \_atoflt\_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)