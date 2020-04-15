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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a688846d5db4d508327745728f8933c91bfd54e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337671"
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

*端点*<br/>
指向停止扫描的字符的指针。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strtod**返回浮点数的值，除非表示形式将导致溢出，在这种情况下，函数返回 +/-**HUGE_VAL**。 **HUGE_VAL**的符号与无法表示的值的符号匹配。 如果无法执行转换或发生，**则 strtod**返回 0 。

**wcstod**返回类似于**strstrd**的值。 对于这两个函数，如果发生溢出或下溢并调用无效的参数处理程序 **，errno**设置为**ERANGE，** 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 有关此代码和其他退货代码的详细信息[，请参阅_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>备注

每个函数将输入字符串*strSource*转换为**双**。 **strstrd**函数将*strSource*转换为双精度值。 **strtod**停止读取字符串*strSource*的第一个字符，它不能识别为数字的一部分。 这可能是终止 null 字符。 **wcstod**是一个宽字符版本的**斯特。** 其*strSource*参数是宽字符字符串。 否则这些函数具有相同行为。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

当前区域设置**的LC_NUMERIC**类别设置决定了*strSource*中半径点字符的识别。 有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 没有 **_l**后缀的函数使用当前区域设置;**_strtod_l**与 **_strtod_l**相同，只是它们使用传入*区域设置*。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*端点*不是**NULL，** 则指向停止扫描的字符的指针存储在*端点指向*的位置。 如果无法执行转换（未找到有效数字或指定了无效的基），*则 strSource*的值存储在*endptr*指向的位置。

**strtod**期望*strSource*指向以下形式之一的字符串：

[*空白 ]*[*符号*][*数字*]*半径**数字*• &#124;*半径**数字**[e**e** &#124; **E**=*符号*[**NAN***数字**]** 空白 **** 符号 ***0x** &#124; **0X***sequence*= 十*六进制数字*•*&#124;半径*六*radix**hexdigits**进制数字** ***p** &#124; **P**=*符号*=*六进制数字**** 空白 *** 符号 [**INF** &#124; **INFINITY**] [*空白*]***

可选的前导*空格*可以由忽略的空格和制表符组成;*符号*是加（+）或减（-）;*数字*是一个或多个十进制数字;*六进制数字*是一个或多个十六进制数字;*radix*是 radix 点字符，在默认"C"区域设置中为句点 （.），或者在当前区域设置不同或指定*区域设置*时特定于区域设置的值;*序列*是字母数字或下划线字符的序列。 在十进制和十六进制数字窗体中，如果半径点字符之前没有数字，则半径点字符之后必须至少显示一个数字。 在十进制形式中，小数位数可以跟一个指数，它由介绍性字母 **（e**或**E**） 和可选签名的整数组成。 在十六进制形式中，十六进制数字可以跟一个指数，它由介绍性字母 **（p**或**p**） 和可选签名的十六进制整数组成，表示指数为 2 的幂。 在这两种形式中，如果既不出现指数零件，也不出现半径点字符，则假定半径点字符遵循字符串中的最后一个数字。 在**INF**和**NAN**窗体中都会忽略案例。 不适合这些窗体之一的第一个字符将停止扫描。

这些函数的 UCRT 版本不支持转换 Fortran 样式 （**d**或**D**） 指数字母。 这个非标准扩展受早期版本的 CRT 支持，可能会为你的代码的带来重大变化。 UCRT 版本支持 INF 和 NAN 值的十六进制字符串和往返，在早期版本中不支持这些值。 这还可能导致代码的中断更改。 例如，字符串"0x1a"将在早期版本中被**strstrd**解释为 0.0，但在 UCRT 版本中为 26.0。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**斯特托德** **， _strtod_l**|C：&lt;stdlib.h> C++：&lt;cstdlib> 或 &lt;stdlib.h> |
|**wcstod**， **_wcstod_l**|C：&lt;stdlib.h> 或 &lt;wchar.h> C++：&lt;cstdlib>、&lt;stdlib.h> 或 &lt;wchar.h> |

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
[现场](../../c-runtime-library/locale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
