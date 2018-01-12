---
title: "strtod、_strtod_l、wcstod、_wcstod_l | Microsoft 文档"
ms.custom: 
ms.date: 10/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
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
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
dev_langs: C++
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1d46e6402efe69a9099d53d9d93b5b367f6dd18c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="strtod-strtodl-wcstod-wcstodl"></a>strtod、_strtod_l、wcstod、_wcstod_l

将字符串转换为双精度值。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*nptr*  
要转换的 null 终止的字符串。

*endptr*  
指向停止扫描的字符的指针。

*locale*  
要使用的区域设置。

## <a name="return-value"></a>返回值

`strtod`返回的值的浮点数，除时表示形式将导致的溢出，在其中 case 函数将返回 + /-`HUGE_VAL`。 `HUGE_VAL` 的符号与无法表示的值的符号相匹配。 如果无法执行转换或出现下溢，则 `strtod` 返回 0。

`wcstod` 返回类似于 `strtod` 的值。 对于这两个函数，如果发生溢出或下溢，则将 `errno` 设置为 `ERANGE`，并调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 有关此代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

每个函数将转换输入的字符串*nptr*到`double`。 `strtod`函数将转换*nptr*为双精度值。 `strtod`停止读取字符串*nptr*不能将其识别为一个数字部分的第一个字符。 这可能是终止 null 字符。 `wcstod`是的宽字符版本`strtod`; 其*nptr*参数是宽字符字符串。 否则这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcstod`|`strtod`|`strtod`|`wcstod`|
|`_tcstod_l`|`_strtod_l`|`_strtod_l`|`_wcstod_l`|

`LC_NUMERIC`类别设置的当前区域设置确定识别中的基数点字符*nptr*。 有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 功能，而不必`_l`后缀使用当前区域设置;`_strtod_l`等同于`_strtod_l`只不过它们使用*区域设置*改用已传入。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不`NULL`，停止扫描的字符的指针指向的位置存储*endptr*。 如果可以不执行任何转换 （未找到有效的数字或指定了无效的基本） 的值*nptr*指向的位置存储*endptr*。

`strtod`需要*nptr*以指向的字符串的以下形式之一：

[*空白*] [*登录*] {*数字*[*基数**数字*] &#124;*基数**数字*} [{**e** &#124;**E**} [*登录*]*数字*]  
[*空白*] [*登录*] {**0x** &#124;**0x**} {*hexdigits* [*基数* *hexdigits*] &#124;*基数* *hexdigits*} [{**p** &#124;**P**} [*登录*] *hexdigits*]  
[*空白*] [*登录*] {**INF** &#124;**无穷大**}  
[*空白*] [*登录*] **NAN** [*序列*]

可选的前导*空白*可能包含空格和制表符字符，将被忽略;*登录*是加号 （+） 或减号 （-）;*数字*是一个或多个十进制数字;*hexdigits*是一个或多个十六进制数字;*基数*是基数点字符，或者句点 （.） 在默认"C"区域，或特定于区域设置的值或如果当前区域设置不同时*区域设置*指定，则为*序列*是一系列的字母数字或下划线字符。 在十进制和十六进制数字的窗体，如果没有任何数字出现在之前的基数点字符，至少一个必须出现在之后的基数点字符。 十进制形式的十进制数字后面可以跟一个指数，介绍性字母组成 (**e**或**E**) 和一个可选带符号的整数。 十六进制形式的十六进制数字后面可以跟一个指数，介绍性字母组成 (**p**或**P**) 和一个可选带符号十六进制整数，表示为 2 的幂的指数。 在其中任一种形式中，如果一个指数部分和基数点字符都不出现，基数点字符假定要遵循在字符串中的最后一位数。 在这两忽略大小写**INF**和**NAN**窗体。 不符合这些窗体的第一个字符停止扫描。

这些函数的 UCRT 版本不支持的 Fortran 样式转换 (**d**或**D**) 指数字母。 这个非标准扩展受早期版本的 CRT 支持，可能会为你的代码的带来重大变化。 UCRT 版本支持十六进制字符串与 INF 和 NAN 值，在早期版本中不支持的往返。 这也会导致在代码中的重大更改。 例如，字符串"0x1a"将被解释`strtod`作 0.0 在以前版本，而应用作 26.0 UCRT 版本中。

## <a name="requirements"></a>惠?

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`strtod`, `_strtod_l`|C：&lt;stdlib.h> C++：&lt;cstdlib> 或 &lt;stdlib.h> |
|`wcstod`, `_wcstod_l`|C：&lt;stdlib.h> 或 &lt;wchar.h> C++：&lt;cstdlib>、&lt;stdlib.h> 或 &lt;wchar.h> |

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
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

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)   
[浮点支持](../../c-runtime-library/floating-point-support.md)   
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
[区域设置](../../c-runtime-library/locale.md)   
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)   
[strtol、wcstol、_strtol_l、_wcstol_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
[atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
[localeconv](../../c-runtime-library/reference/localeconv.md)   
[_create_locale、_wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
[_free_locale](../../c-runtime-library/reference/free-locale.md)