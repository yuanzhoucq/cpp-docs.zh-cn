---
title: "strtoull、_strtoull_l、wcstoull、_wcstoull_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
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
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
dev_langs: C++
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4fb85ae9aa0c21d2afdc5c4cb5a906154cb42c6b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="strtoull-strtoulll-wcstoull-wcstoulll"></a>strtoull、_strtoull_l、wcstoull、_wcstoull_l
将字符串转换为无符号的长整数值。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned long long strtoull(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
unsigned long long _strtoull_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
unsigned long long wcstoull(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
unsigned long long _wcstoull_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `nptr`  
 要转换的 null 终止的字符串。  
  
 `endptr`  
 指向停止扫描的字符的指针。  
  
 `base`  
 要使用的基数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 `strtoull` 返回转换后的值（如果有），或溢出的 `ULLONG_MAX`。 如果无法执行任何转换，则 `strtoull` 返回 0。 `wcstoull` 返回类似于 `strtoull` 的值。 对于这两个函数，如果出现溢出或下溢，则 `errno` 设置为 `ERANGE`。  
  
 有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 这些函数均将输入字符串 `nptr` 转换为 `unsigned long long` 整数值。  
  
 `strtoull` 在无法将其识别为数字的一部分的第一个字符处停止读取字符串 `nptr`。 这可能是终止 null 字符，也可能是大于或等于 `base` 的第一个数字字符。 区域设置的 `LC_NUMERIC` 类别设置确定 `nptr` 中的基数字符的识别；有关详细信息，请参阅 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 `strtoull` 和 `wcstoull` 使用当前区域设置；而 `_strtoull_l` 和 `_wcstoull_l` 改用传入但相同的区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不为 `NULL`，则在 `endptr` 所指向的位置存储指向字符的指针（该指针停止扫描）。 如果不能执行任何转换（未找到任何有效的数字或指定了无效的基数），则将 `nptr` 的值存储在由 `endptr` 指向的位置。  
  
 `wcstoull` 是 `strtoull` 的宽字符版本；而且它的 `nptr` 参数是宽字符字符串。 否则，这些函数具有相同行为。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoull`|`strtoull`|`strtoull`|`wcstoull`|  
|`_tcstoull_l`|`strtoull_l`|`_strtoull_l`|`_wcstoull_l`|  
  
 `strtoull` 需要 `nptr` 指向以下形式的字符串：  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits` &#124; [`letters`]]  
  
 `whitespace` 可能包含被忽略的空格和制表符；`digits` 是一个或多个十进制数字；`letters` 是从“a”到“z”（或从“A”到“Z”）的一个或多个字母。 不符合此形式的第一个字符停止扫描。 如果 `base` 在 2 和 36 之间，则将其用作数字的基数。 如果 `base` 为 0，则由 `nptr` 指向的字符串的初始字符用于确定基数。 如果第一个字符为“0”，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 `base` 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果 `base` 为 0 且扫描的第一个字符为“0”，则假定八进制整数，且“8”或“9”字符会停止扫描。 `strtoull` 允许加号 (`+`) 或减号 (`-`) 前缀；前导减号符号表示返回值不起作用。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`strtoull`|\<stdlib.h>|  
|`wcstoull`|\<stdlib.h> 或 \<wchar.h>|  
|`_strtoull_l`|\<stdlib.h>|  
|`_wcstoull_l`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [strtod](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、_strtod_l、wcstod、_wcstod_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol、wcstol、_strtol_l、_wcstol_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoll、_strtoll_l、wcstoll、_wcstoll_l](../../c-runtime-library/reference/strtoll-strtoll-l-wcstoll-wcstoll-l.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)