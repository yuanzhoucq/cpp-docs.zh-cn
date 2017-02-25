---
title: "atoll、_atoll_l、_wtoll、_wtoll_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wtoll"
  - "_atoll_l"
  - "_wtoll_l"
  - "atoll"
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
  - "_tstoll_l"
  - "_wtoll"
  - "_atoll_l"
  - "_ttoll"
  - "_tstoll"
  - "_wtoll_l"
  - "atoll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_atoll_l 函数"
  - "_wtoll 函数"
  - "_wtoll_l 函数"
  - "atoll 函数"
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# atoll、_atoll_l、_wtoll、_wtoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为 `long long` 整数。  
  
## 语法  
  
```  
long long atoll(  
   const char *str   
);  
long long _wtoll(  
   const wchar_t *str   
);  
long long _atoll_l(  
   const char *str,  
   _locale_t locale  
);  
long long _wtoll_l(  
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
 每个函数返回 `long long` 值，此值由将输入字符作为数字解析而生成。  如果该输入无法转换为该类型的值，则 `atoll` 的返回值为 0。  
  
 对于大量正整数值的溢出，`atoll` 将返回 `LLONG_MAX`，对于大量负整数值的溢出，则返回 `LLONG_MIN`。  
  
 在所有超出范围的情况下，`errno` 设置为 `ERANGE`。  如果传递的参数为 `NULL`，则调用无效的参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回 0。  
  
## 备注  
 这些函数将字符串转换为 `long long` 整数值。  
  
 输入字符串是可被解释为指定类型的数值的字符序列。  当第一个字符不能识别为数字时，函数将停止读入输入字符串。  此字符可能是终止字符串的 null 字符（'\\0' 或 L'\\0'）。  
  
 `atoll` 的 `str` 参数具有以下格式：  
  
```  
[whitespace] [sign] [digits]  
```  
  
 `whitespace` 包含已忽略的空格或制表符；`sign` 是加号 \(\+\) 或减号 \(\-\)；而 `digits` 是一个或多个数字。  
  
 `_wtoll` 与 `atoll` 与相同，但它采用宽字符字符串作为参数。  
  
 这些带有 `_l` 后缀的函数版本与那些不带此后缀的函数版本相同，只不过它们使用传递的区域设置参数而不是当前区域设置。  有关详细信息，请参阅 [区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tstoll`|`atoll`|`atoll`|`_wtoll`|  
|`_tstoll_l`|`_atoll_l`|`_atoll_l`|`_wtoll_l`|  
|`_ttoll`|`_atoll`|`_atoll`|`_wtoll`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`atoll`, `_atoll_l`|\<stdlib.h\>|  
|`_wtoll`, `_wtoll_l`|\<stdlib.h\> 或 \<wchar.h\>|  
  
## 示例  
 此过程演示如何使用 `atoll` 函数将作为字符串存储的数字转换为数值。  
  
```  
// crt_atoll.c  
// Build with: cl /W4 /Tc crt_atoll.c  
// This program shows how to use the atoll   
// functions to convert numbers stored as   
// strings to numeric values.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main(void)  
{  
    char *str = NULL;  
    long long value = 0;  
  
    // An example of the atoll function  
    // with leading and trailing white spaces.  
    str = "  -27182818284 ";  
    value = atoll(str);  
    printf("Function: atoll(\"%s\") = %lld\n", str, value);  
  
    // Another example of the atoll function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = atoll(str);  
    printf("Function: atoll(\"%s\") = %lld\n", str, value);  
  
    // Another example of the atoll function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = atoll(str);  
    printf("Function: atoll(\"%s\") = %lld\n", str, value);  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **函数：atoll\(" \-27182818284 "\) \= \-27182818284**  
**函数：atoll\("314127.64"\) \= 314127**  
**函数：atoll\("3336402735171707160320"\) \= 9223372036854775807**  
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