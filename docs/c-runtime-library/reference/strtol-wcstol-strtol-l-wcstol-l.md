---
title: "strtol、wcstol、_strtol_l、_wcstol_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
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
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
dev_langs:
- C++
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3fd2d3a78138ca4c6f94cf77bb33de9fda89743d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="strtol-wcstol-strtoll-wcstoll"></a>strtol、wcstol、_strtol_l、_wcstol_l
将字符串转换为长整数值。  
  
## <a name="syntax"></a>语法  
  
```  
long strtol(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
long wcstol(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
long _strtol_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
long _wcstol_l(  
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
 `strtol` 返回字符串 `nptr` 中表示的值，只有当表示形式会导致溢出时才返回 `LONG_MAX` 或 `LONG_MIN`。 如果无法执行任何转换，则 `strtol` 返回 0。 `wcstol` 返回类似于 `strtol` 的值。 对于这两个函数，如果出现溢出或下溢，则 `errno` 设置为 `ERANGE`。  
  
 有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `strtol` 函数将 `nptr` 转换为 `long`。 `strtol` 在首个无法识别为数字一部分的字符处停止读取字符串 `nptr`。 这可能是终止 null 字符，也可能是大于或等于 `base` 的第一个数字字符。  
  
 `wcstol` 是 `strtol` 的宽字符版本；它的 `nptr` 参数是宽字符字符串。 否则这些函数具有相同行为。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstol`|`strtol`|`strtol`|`wcstol`|  
|`_tcstol_l`|`_strtol_l`|`_strtol_l`|`_wcstol_l`|  
  
 当前区域设置的 `LC_NUMERIC` 类别设置确定 `nptr` *中的基数字符的识别；* 有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 不带 `_l` 后缀的函数的版本使用当前区域设置；`_strtol_l` 和 `_wcstol_l` 与不带 `_l` 后缀的相应的函数相同，只不过它们使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `endptr` 不为 `NULL`，则在 `endptr` 所指向的位置存储指向字符的指针（该指针停止扫描）。 如果无法执行任何转换（未找到任何有效的数字或指定了无效的基数），则将 `nptr` 的值存储在由 `endptr` 指向的位置。  
  
 `strtol` 需要 `nptr` 指向以下形式的字符串：  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits`]  
  
 `whitespace` 可能包含被忽略的空格和制表符；`digits` 是一个或多个十进制数字。 不符合此形式的第一个字符停止扫描。 如果 `base` 在 2 和 36 之间，则将其用作数字的基数。 如果 `base` 为 0，则由 `nptr` 指向的字符串的初始字符用于确定基数。 如果第一个字符为 0，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 `base` 的字母。 超出基数范围的第一个字符停止扫描。 例如，如果 `base` 为 0 且扫描的第一个字符为“0”，则假定为八进制整数，且“8”或“9”字符将停止扫描。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`strtol`|\<stdlib.h>|  
|`wcstol`|\<stdlib.h> 或 \<wchar.h>|  
|`_strtol_l`|\<stdlib.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 请参阅 [strtod](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod、_strtod_l、wcstod、_wcstod_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)