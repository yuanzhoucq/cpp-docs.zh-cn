---
title: "_atoi64、_atoi64_l、_wtoi64、_wtoi64_l | Microsoft Docs"
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
  - "_atoi64_l"
  - "_wtoi64"
  - "_atoi64"
  - "_wtoi64_l"
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
  - "_atoi64"
  - "_tstoi64"
  - "_ttoi64"
  - "wtoi64"
  - "_tstoi64_l"
  - "atoi64"
  - "_wtoi64_l"
  - "_wtoi64"
  - "wtoi64_l"
  - "_atoi64_l"
  - "atoi64_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tstoi64 函数"
  - "wtoi64 函数"
  - "atoi64_l 函数"
  - "_ttoi64 函数"
  - "字符串转换, 为整数"
  - "wtoi64_l 函数"
  - "atoi64 函数"
  - "_tstoi64 函数"
  - "_atoi64_l 函数"
  - "_wtoi64_l 函数"
  - "ttoi64 函数"
  - "_wtoi64 函数"
  - "_atoi64 函数"
ms.assetid: 2c3e30fd-545d-4222-8364-0c5905df9526
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _atoi64、_atoi64_l、_wtoi64、_wtoi64_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Converts a string to a 64\-bit integer.  
  
## 语法  
  
```  
__int64 _atoi64(  
   const char *str   
);  
__int64 _wtoi64(  
   const wchar_t *str   
);  
__int64 _atoi64_l(  
   const char *str,  
   _locale_t locale  
);  
__int64 _wtoi64_l(  
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
 每个函数返回 `__int64` 值，此值由将输入字符作为数字解析而生成。  如果输入不能被转换为这种类型的值，返回值是 `_atoi64`的0值。  
  
 In the case of overflow with large positive integral values, `_atoi64` returns `I64_MAX` and `I64_MIN` in the case of overflow with large negative integral values.  
  
 在所有超出范围的情况下，`errno` 设置为 `ERANGE`。  If the parameter passed in is `NULL`, the invalid parameter handler is invoked, as described in [参数验证](../../c-runtime-library/parameter-validation.md).  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回 0。  
  
## 备注  
 These functions convert a character string to a 64\-bit integer value.  
  
 输入字符串是可被解释为指定类型的数值的字符序列。  当第一个字符不能识别为数字时，函数将停止读入输入字符串。  This character might be the null character \('\\0' or L'\\0'\) terminating the string.  
  
 `_atoi64` 的 `str` 参数具有以下格式：  
  
```  
[whitespace] [sign] [digits]]  
```  
  
 `whitespace` 包含已忽略的空格或制表符；`sign` 是加号 \(\+\) 或减号 \(\-\)；而 `digits` 是一个或多个数字。  
  
 `_wtoi64` 与 `_atoi64` 与相同，但它采用宽字符字符串作为参数。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tstoi64`|`_atoi64`|`_atoi64`|`_wtoi64`|  
|`_ttoi64`|`_atoi64`|`_atoi64`|`_wtoi64`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_atoi64`, `_atoi64_l`|\<stdlib.h\>|  
|`_wtoi64`, `_wtoi64_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
## 示例  
 This program shows how numbers stored as strings can be converted to numeric values using the `_atoi64` functions.  
  
```  
// crt_atoi64.c  
// This program shows how numbers stored as  
// strings can be converted to numeric values  
// using the _atoi64 functions.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    __int64 value = 0;  
  
    // An example of the _atoi64 function  
    // with leading and trailing white spaces.  
    str = "  -2309 ";  
    value = _atoi64( str );  
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the _atoi64 function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = _atoi64( str );  
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the _atoi64 function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = _atoi64( str );  
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **Function: \_atoi64\( "  \-2309 " \) \= \-2309**  
**Function: \_atoi64\( "314127.64" \) \= 314127**  
**Function: \_atoi64\( "3336402735171707160320" \) \= \-1**  
**发生了溢出条件。**   
## .NET Framework 等效项  
  
-   [System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)  
  
-   [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_atodbl, \_atodbl\_l, \_atoldbl, \_atoldbl\_l, \_atoflt, \_atoflt\_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)