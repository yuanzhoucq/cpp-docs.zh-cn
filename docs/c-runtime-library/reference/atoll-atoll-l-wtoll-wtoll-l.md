---
title: "atoll、_atoll_l、_wtoll、_wtoll_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtoll
- _atoll_l
- _wtoll_l
- atoll
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tstoll_l
- _wtoll
- _atoll_l
- _ttoll
- _tstoll
- _wtoll_l
- atoll
dev_langs:
- C++
helpviewer_keywords:
- atoll function
- _wtoll_l function
- _wtoll function
- _atoll_l function
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: e707c06f06015a684e968367f61e7e763ff87a6d
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="atoll-atolll-wtoll-wtolll"></a>atoll、_atoll_l、_wtoll、_wtoll_l
将字符串转换成 `long long` 整数。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `str`  
 要转换的字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 每个函数均返回 `long long` 值，此值是通过将输入字符解释为数字来生成的。 如果输入不能转换为该类型的值，则 `atoll` 的返回值为 0。  
  
 对于大量正整数值的溢出，`atoll` 将返回 `LLONG_MAX`，对于大量负整数值的溢出，则返回 `LLONG_MIN`。  
  
 在所有超出范围的情况下，将 `errno` 设置为 `ERANGE`。 如果传入的参数为 `NULL`，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL`，并返回 0。  
  
## <a name="remarks"></a>备注  
 这些函数将字符串转换为`long long`整数值。  
  
 输入字符串是一系列字符，可以解释为指定类型的数值。 该函数在首个它无法无法识别为数字一部分的字符处停止读取输入字符串。 此字符可能是终止字符串的 null 字符（'\0' 或 L'\0'）。  
  
 `atoll` 的 `str` 参数具有以下形式：  
  
```  
[whitespace] [sign] [digits]  
```  
  
 A`whitespace`空格或制表符字符，将被忽略; 组成`sign`是加号 （+） 或减号 （-）; 和`digits`是一个或多个数字。  
  
 `_wtoll` 与 `atoll` 相同，但前者将宽字符串用作参数。  
  
 这些带有 `_l` 后缀的函数的版本与不带有该后缀的函数版本相同，只不过前者使用传入的区域设置参数而不是当前区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tstoll`|`atoll`|`atoll`|`_wtoll`|  
|`_tstoll_l`|`_atoll_l`|`_atoll_l`|`_wtoll_l`|  
|`_ttoll`|`_atoll`|`_atoll`|`_wtoll`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|--------------|---------------------|  
|`atoll`, `_atoll_l`|\<stdlib.h>|  
|`_wtoll`, `_wtoll_l`|\<stdlib.h> 或 \<wchar.h>|  
  
## <a name="example"></a>示例  
 此程序说明如何使用 `atoll` 函数将存储为字符串的数字转换为数值。  
  
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
  
```Output  
Function: atoll("  -27182818284 ") = -27182818284  
Function: atoll("314127.64") = 314127  
Function: atoll("3336402735171707160320") = 9223372036854775807  
Overflow condition occurred.  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)
