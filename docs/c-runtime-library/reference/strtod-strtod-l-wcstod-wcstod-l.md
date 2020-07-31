---
title: strtod、_strtod_l、wcstod、_wcstod_l
ms.date: 4/2/2020
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
- _o__strtod_l
- _o__wcstod_l
- _o_strtod
- _o_wcstod
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 58cb9e72fc11f0120ed4d99fd5086a195244ac31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233972"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod、_strtod_l、wcstod、_wcstod_l

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

**strtod**返回浮点数的值，除非表示形式导致溢出，在这种情况下，函数返回 +/-**HUGE_VAL**。 **HUGE_VAL**的符号与无法表示的值的符号匹配。 **strtod**如果无法 `0` 执行任何转换或发生下溢，则 strtod 返回。

**wcstod**返回类似为**strtod**的值：

- 对于这两个函数，如果出现溢出或下溢，则**errno**设置为**ERANGE** 。
- 如果有无效参数， **errno**将设置为**EINVAL** ，并且将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

有关此代码及其他返回代码的详细信息，请参阅[_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

每个函数将输入字符串*strSource*转换为 **`double`** 。 **Strtod**函数将*strSource*转换为双精度值。 **strtod**停止读取其无法识别为数字一部分的第一个字符的字符串*strSource* 。 此字符可能是终止 null 字符。 **wcstod**是**strtod**的宽字符版本;其*strSource*参数是宽字符字符串。 否则这些函数具有相同行为。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

当前区域设置的**LC_NUMERIC**类别设置确定*strSource*中的基数点字符的识别。 有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 没有 **_l**后缀的函数使用当前区域设置;**_strtod_l**与 **_strtod_l**相同，只不过它们只使用传入的*区域设置*。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不**为 NULL**，则指向停止扫描的字符的指针将存储在*endptr*指向的位置。 如果无法执行任何转换（未找到任何有效的数字或指定了无效的基数），则*strSource*的值将存储在*endptr*指向的位置。

**strtod**要求*strSource*指向以下格式之一的字符串：

[*空格*][*sign*]{*数字*[*基数**数字*] &#124;*基数**位数*}[{**e** &#124; **e**} [*sign*]*数字*] [*空格*] [*sign*] {**0x** &#124; **0x**} {*hexdigits* [*基数* *hexdigits*] &#124;*基数* *hexdigits*} [{**p** &#124; **p**} [*sign*] *hexdigits*] [*空格*] [*sign*] {**INF** &#124;**无限大**} [*空格*] [*sign*] **NAN** [*序列*]

可选前导*空格*可能包含被忽略的空格和制表符;*sign*为加号（+）或减号（-）;*位数*为一个或多个十进制数字;*hexdigits*是一个或多个十六进制数字;*基数*是基数点字符，在默认 "C" 区域设置中是句点（.），或者如果当前区域设置不同或指定了*区域*设置，则为特定于区域设置的值;*序列*是字母数字或下划线字符的序列。 在十进制和十六进制数字形式中，如果没有数字出现在基数点字符之前，则必须至少有一个数字出现在基数点字符之后。 在十进制格式中，十进制数字后面可以跟一个指数，其中包含一个引导字母（**e**或**e**）和一个可选择的带符号整数。 在十六进制形式中，十六进制数字后面可以跟一个指数，其中包含一个介绍性字母（**p**或**p**）和一个可选的带符号的十六进制整数，该整数表示指数作为2的幂。 在任一窗体中，如果不存在指数部分或基数点字符，则假定使用了字符串中的最后一个数字。 **INF**和**NAN**形式都忽略大小写。 不符合其中一种形式的第一个字符会停止扫描。

这些函数的 UCRT 版本不支持 Fortran 样式（**d**或**d**）指数字母的转换。 这个非标准扩展受早期版本的 CRT 支持，可能会为你的代码的带来重大变化。 UCRT 版本支持十六进制字符串和 INF 和 NAN 值的往返，这在早期版本中不受支持。 这也可能导致代码中的重大更改。 例如，在以前的版本中，字符串 "0x1a" 将由**strtod**解释为0.0，而不是在 UCRT 版本中解释为26.0。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtod**、 **_strtod_l**|C：&lt;stdlib.h> C++：&lt;cstdlib> 或 &lt;stdlib.h> |
|**wcstod**、 **_wcstod_l**|C：&lt;stdlib.h> 或 &lt;wchar.h> C++：&lt;cstdlib>、&lt;stdlib.h> 或 &lt;wchar.h> |

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

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
