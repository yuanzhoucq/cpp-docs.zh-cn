---
title: "ato，_atol_l，_wtol，_wtol_l | Microsoft Docs"
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
  - "atol"
  - "_wtol_l"
  - "_wtol"
  - "_atol_l"
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
  - "_atol_l"
  - "_ttol_l"
  - "_tstol_l"
  - "_tstol"
  - "_wtol"
  - "_ttol"
  - "_wtol_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tstol 函数"
  - "atol 函数"
  - "ttol 函数"
  - "_atol_l 函数"
  - "_tatol_l 函数"
  - "字符串转换, 为整数"
  - "_tstol 函数"
  - "_ttol 函数"
  - "_ttol_l 函数"
  - "atol_l 函数"
  - "wtol_l 函数"
  - "_wtol_l 函数"
  - "wtol 函数"
  - "_wtol 函数"
ms.assetid: cedfc21c-2d64-4e9c-bd04-bdf60b12db46
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ato，_atol_l，_wtol，_wtol_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convert a string to a long integer.  
  
## 语法  
  
```  
long atol(  
   const char *str   
);  
long _atol_l(  
   const char *str,  
   _locale_t locale  
);  
long _wtol(  
   const wchar_t *str   
);  
long _wtol_l(  
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
 每个函数返回 `long` 值，此值由将输入字符作为数字解析而生成。  如果该输入无法转换为该类型的值，则 `atol` 的返回值为 0L。  
  
 In the case of overflow with large positive integral values, `atol` returns `LONG_MAX`; in the case of overflow with large negative integral values, `LONG_MIN` is returned.  在所有超出范围的情况下，`errno` 设置为 `ERANGE`。  If the parameter passed in is `NULL`, the invalid parameter handler is invoked, as described in [参数验证](../../c-runtime-library/parameter-validation.md).  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回 0。  
  
## 备注  
 These functions convert a character string to a long integer value \(`atol`\).  
  
 输入字符串是可被解释为指定类型的数值的字符序列。  当第一个字符不能识别为数字时，函数将停止读入输入字符串。  This character may be the `NULL` character \('\\0' or L'\\0'\) terminating the string.  
  
 `atol` 的 `str` 参数具有以下格式：  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\]\]  
  
 `whitespace` 包含已忽略的空格或制表符；`sign` 是加号 \(\+\) 或减号 \(\-\)；而 `digits` 是一个或多个数字。  
  
 `_wtol` is identical to `atol` except that it takes a wide character string.  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 & \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-------------------------------|----------------|-------------------|  
|`_tstol`|`atol`|`atol`|`_wtol`|  
|`_ttol`|`atol`|`atol`|`_wtol`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`atol`|\<stdlib.h\>|  
|`_atol_l`, `_wtol`, `_wtol_l`|\<stdlib.h\> and \<wchar.h\>|  
  
## 示例  
 此过程演示如何使用 `atol` 函数将作为字符串存储的数字转换为数值。  
  
```  
// crt_atol.c  
// This program shows how numbers stored as  
// strings can be converted to numeric values  
// using the atol functions.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    long    value = 0;  
  
    // An example of the atol function  
    // with leading and trailing white spaces.  
    str = "  -2309 ";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **Function: atol\( "  \-2309 " \) \= \-2309**  
**Function: atol\( "314127.64" \) \= 314127**  
**Function: atol\( "3336402735171707160320" \) \= 2147483647**  
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