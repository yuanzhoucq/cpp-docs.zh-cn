---
title: strtod、_strtod_l、wcstod、_wcstod_l
ms.date: 10/20/2017
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
ms.openlocfilehash: c8c2b3b491e2e7265829fa88580529dc757ace8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376466"
---
# <a name="strtod-strtodl-wcstod-wcstodl"></a>strtod、_strtod_l、wcstod、_wcstod_l

将字符串转换为双精度值。

## <a name="syntax"></a>语法

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*strSource*<br/>
要转换的 null 终止的字符串。

*endptr*<br/>
指向停止扫描的字符的指针。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strtod**返回的值的浮点数，只有当表示形式会导致的溢出时，该函数返回 + /-**HUGE_VAL**。 符号**HUGE_VAL**不能表示的值相匹配。 **strtod**如果可以执行任何转换或发生下溢，则返回 0。

**wcstod**类似于返回值**strtod**。 对于这两个函数， **errno**设置为**ERANGE**如果出现溢出或下溢并调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 有关此代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

每个函数将输入的字符串转换*strSource*到**double**。 **Strtod**函数转换*strSource*为双精度值。 **strtod**停止读取字符串*strSource*在它无法识别为数字一部分的第一个字符。 这可能是终止 null 字符。 **wcstod**是宽字符版本**strtod**; 它*strSource*参数是宽字符字符串。 否则这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

**LC_NUMERIC**的当前区域设置类别设置确定在基数点字符的识别*strSource*。 有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 功能而无需 **_l**后缀使用当前区域设置; **_strtod_l**等同于 **_strtod_l** ，只不过它们使用*区域设置*中传递。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**NULL**，指向的位置存储指向停止扫描的字符的指针*endptr*。 如果可以不执行任何转换 （未找到任何有效的数字或指定了无效的基数） 的值*strSource*指向的位置处存储*endptr*。

**strtod**预期*strSource*以指向字符串的以下形式之一：

[*空格*] [*登录*] {*数字*[*基数* *数字*] &#124; *基数* *位数*} [{**e** &#124; **电子**} [*登录*]*数字*] [*空格*] [*登录*] {**0x** &#124; **0 X**} {*hexdigits* [*基数* *hexdigits*] &#124; *基数* *hexdigits*} [{**p** &#124;**P**} [*登录*] *hexdigits*] [*空格*] [*登录*] {**INF** &#124; **无穷大**} [*空格*] [*登录*] **NAN** [*序列*]

可选前导*空格*可能包含的空格和制表符，将被忽略;*登录*是加号 （+） 或减号 （–）;*位数*是一个或多个十进制数字;*hexdigits*是一个或多个十六进制数字;*基数*基数点字符，也是一个句点 （.） 默认值"C"区域设置，或特定于区域设置的值或如果当前区域设置不同时*区域设置*指定，则为*序列*是一系列字母数字或下划线字符。 在十进制和十六进制数字的窗体，如果没有数字前基数点字符，至少一个必须出现后基数点字符。 在十进制，十进制数字可以后接一个指数，其中包含介绍性字母 (**e**或**E**) 和一个可选的带符号整数。 以十六进制形式，十六进制数字可以后接一个指数，其中包含介绍性字母 (**p**或**P**) 和一个可选的带符号的十六进制整数，表示为 2 的幂的指数。 在任一窗体中，如果指数部分和基数点字符都不出现，基数点字符假定按照字符串中的最后一位数。 在这种忽略大小写**INF**并**NAN**窗体。 不符合这些窗体的第一个字符停止扫描。

这些函数的 UCRT 版本不支持转换 Fortran 样式的 (**d**或**D**) 指数字母。 这个非标准扩展受早期版本的 CRT 支持，可能会为你的代码的带来重大变化。 UCRT 版本支持十六进制字符串与 INF 和 NAN 值，不受支持早期版本中的往返。 这也会在代码中导致重大更改。 例如，字符串"0x1a"将解释由**strtod**作为 0.0 在以前版本，而是作为中的 UCRT 版本 26.0。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtod**， **_strtod_l**|C：&lt;stdlib.h> C++：&lt;cstdlib> 或 &lt;stdlib.h> |
|**wcstod**， **_wcstod_l**|C：&lt;stdlib.h> 或 &lt;wchar.h> C++：&lt;cstdlib>、&lt;stdlib.h> 或 &lt;wchar.h> |

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

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
