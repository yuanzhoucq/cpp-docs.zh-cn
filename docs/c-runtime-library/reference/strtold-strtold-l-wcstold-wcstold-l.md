---
title: "strtold、_strtold_l、wcstold、_wcstold_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
dev_langs:
- C++
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
caps.latest.revision: 8
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
ms.openlocfilehash: f23b0e3105532357ba9d31634a999c98df366552
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="strtold-strtoldl-wcstold-wcstoldl"></a>strtold、_strtold_l、 wcstold、_wcstold_l
将字符串转换为长双精度浮点值。  
  
## <a name="syntax"></a>语法  
  
```  
long double strtold(  
   const char *nptr,  
   char **endptr   
);  
long double _strtold_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
long double wcstold(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
long double wcstold_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `nptr`  
 要转换的 null 终止的字符串。  
  
 `endptr`  
 指向停止扫描的字符的指针。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 `strtold`返回作为的浮点数的值`long double`，表示将导致溢出时除外 — 在这种情况下，该函数将返回 + /-`HUGE_VALL`。 `HUGE_VALL` 的符号与无法表示的值的符号相匹配。 如果无法执行转换或出现下溢，则 `strtold` 返回 0。  
  
 `wcstold` 返回类似于 `strtold` 的值。 对于这两个函数，如果发生溢出或下溢，则将 `errno` 设置为 `ERANGE`，并调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
 有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 每个函数均将输入字符串 `nptr` 转换为 `long double`。 `strtold` 函数将 `nptr` 转换为长双精度值。 `strtold` 在首个无法识别为数字一部分的字符处停止读取字符串 `nptr`。 这可能是终止 null 字符。 `strtold` 的宽字符版本是 `wcstold`；它的 `nptr` 参数是宽字符字符串。 否则，这些函数具有相同行为。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstold`|`strtold`|`strtold`|`wcstold`|  
|`_tcstold_l`|`_strtold_l`|`_strtold_l`|`_wcstold_l`|  
  
 当前区域设置的 `LC_NUMERIC` 类别设置确定 `nptr` 中的基数字符的识别。 有关详细信息，请参阅 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 不带 `_l` 后缀的函数使用当前区域设置；`_strtold_l` 和 `_wcstold_l` 与 `_strtold` 和 `_wcstold` 相同，只不过它们改用传入的区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不为 `NULL`，则在 `endptr` 所指向的位置存储指向字符的指针（该指针停止扫描）。 如果不能执行任何转换（未找到任何有效的数字或指定了无效的基数），则将 `nptr` 的值存储在由 `endptr` 指向的位置。  
  
 `strtold` 需要 `nptr` 指向以下形式的字符串：  
  
 [`whitespace`] [`sign`] [`digits`] [`.digits`] [ {`d` &#124; `D` &#124; `e` &#124; `E`}[`sign`]`digits`]  
  
 `whitespace` 可能包含被忽略的空格和制表符；`sign` 是加号 (`+`) 或减号 (`-`)；`digits` 是一个或多个十进制数字。 如果基数字符前没有任何数字，则基数字符后必须至少有一个数字。 十进制数字可以后跟一个指数，其中包含介绍性字母（`d`、`D`、`e` 或 `E`）和可选的带符号的整数。 如果指数部分和基数字符都没有出现，则假定基数字符跟随字符串中的最后一个数字。 不符合此形式的第一个字符停止扫描。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`strtold`, `_strtold_l`|\<stdlib.h>|  
|`wcstold`, `_wcstold_l`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_strtold.c  
// Build with: cl /W4 /Tc crt_strtold.c  
// This program uses strtold to convert a  
// string to a long double-precision value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *string;  
   char *stopstring;  
   long double x;  
  
   string = "3.1415926535898This stopped it";  
   x = strtold(string, &stopstring);  
   printf("string = %s\n", string);  
   printf("   strtold = %.13Lf\n", x);  
   printf("   Stopped scan at: %s\n\n", stopstring);  
}  
```  
  
```Output  
string = 3.1415926535898This stopped it  
   strtold = 3.1415926535898  
   Stopped scan at: This stopped it  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、_strtod_l、wcstod、_wcstod_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol、wcstol、_strtol_l、_wcstol_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [_create_locale、_wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../../c-runtime-library/reference/free-locale.md)
