---
title: strtof、_strtof_l、wcstof、_wcstof_l
ms.date: 04/05/2018
apiname:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: 10a50a175685f3e8f7f1241683c7705fd9a9b142
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376427"
---
# <a name="strtof-strtofl-wcstof-wcstofl"></a>strtof、_strtof_l、wcstof、_wcstof_l

将字符串转换为单精度浮点值。

## <a name="syntax"></a>语法

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>参数

*strSource*<br/>
要转换的 null 终止的字符串。

*endptr*<br/>
指向停止扫描的字符的指针。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strtof**返回的值的浮点数，只有当表示形式会导致的溢出时，该函数返回 + /-**HUGE_VALF**。 符号**HUGE_VALF**不能表示的值相匹配。 **strtof**如果可以执行任何转换或发生下溢，则返回 0。

**wcstof**类似于返回值**strtof**。 对于这两个函数， **errno**设置为**ERANGE**如果出现溢出或下溢并调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

每个函数将输入的字符串转换*strSource*到**float**。 **Strtof**函数转换*strSource*为单精度值。 **strtof**停止读取字符串*strSource*在它无法识别为数字一部分的第一个字符。 这可能是终止 null 字符。 **wcstof**是宽字符版本**strtof**; 它*strSource*参数是宽字符字符串。 否则，这些函数具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

**LC_NUMERIC**的当前区域设置类别设置确定中基数字符的识别*strSource*; 有关详细信息，请参阅[setlocale、 _wsetlocale](setlocale-wsetlocale.md). 没有的函数 **_l**后缀使用当前区域设置; 具有后缀的完全相同，只不过它们改用已传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*endptr*不是**NULL**，在所指向的位置存储指向停止扫描的字符的指针*endptr*。 如果可以不执行任何转换 （未找到任何有效的数字或指定了无效的基数） 的值*strSource*所指向的位置存储*endptr*。

**strtof**预期*strSource*以指向以下形式的字符串：

[*空格*] [*登录*] [*数字*] [__。__*位数*] [{**e** &#124; **E**} [*登录*]*数字*]

一个*空格*可能包含的空格和制表符，将被忽略;*符号*是加上 (**+**) 或减号 (**-**); 并*数字*是一个或多个十进制数字。 如果基数字符前没有任何数字，则基数字符后必须至少有一个数字。 十进制数字可以跟一个指数，其中包含介绍性字母 (**e**或**E**) 和一个可选的带符号整数。 如果指数部分和基数字符都没有出现，则假定基数字符跟随字符串中的最后一个数字。 不符合此形式的第一个字符停止扫描。

这些函数的 UCRT 版本不支持转换 Fortran 样式的 (**d**或**D**) 指数字母。 这个非标准扩展受早期版本的 CRT 支持，可能会为你的代码的带来重大变化。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtof**， **_strtof_l**|C：\<stdlib.h> C++：&lt;cstdlib> 或 \<stdlib.h>|
|**wcstof**， **_wcstof_l**|C：\<stdlib.h> 或 \<wchar.h> C++：&lt;cstdlib>、\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
