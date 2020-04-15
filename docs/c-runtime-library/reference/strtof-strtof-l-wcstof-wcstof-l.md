---
title: strtof、_strtof_l、wcstof、_wcstof_l
ms.date: 4/2/2020
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
- _o__strtof_l
- _o__wcstof_l
- _o_strtof
- _o_wcstof
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
ms.openlocfilehash: f61aa0edeadd74a254f906dd745e18b059da7f24
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365137"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof、_strtof_l、wcstof、_wcstof_l

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

*端点*<br/>
指向停止扫描的字符的指针。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**strtof**返回浮点数的值，除非表示形式将导致溢出，在这种情况下，函数返回 +/-**HUGE_VALF**。 **HUGE_VALF**的符号与无法表示的值的符号匹配。 如果无法执行转换或发生，**则 strtof**返回 0 。

**wcstof**返回的值类似于**strtof。** 对于这两个函数，如果发生溢出或下溢并调用无效的参数处理程序 **，errno**设置为**ERANGE，** 如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

每个函数将输入字符串*strSource*转换为**浮点**。 **strtof**函数将*strSource*转换为单精度值。 **strtof**停止读取字符串*strSource*的第一个字符，它不能识别为数字的一部分。 这可能是终止 null 字符。 **wcSTof**是一个宽字符版本的**斯特夫**;其*strSource*参数是宽字符字符串。 否则，这些函数具有相同行为。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

当前区域设置**LC_NUMERIC**类别设置决定了*strSource*中半径字符的识别;有关详细信息，请参阅[设置区域设置，_wsetlocale](setlocale-wsetlocale.md)。 没有 **_l**后缀的函数使用当前区域设置;但是，没有_l后缀的函数使用当前区域设置。具有后缀的那些是相同的，只是它们使用传入区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

如果*端点*不是**NULL，** 则指向停止扫描的字符的指针存储在*端点指向*的位置。 如果无法执行转换（未找到有效数字或指定了无效的基），*则 strSource*的值存储在*endptr*指向的位置。

**strtof**期望*strSource*指向以下形式的字符串：

[*空白 ]*[*符号*][*数字*][__.__*数字*|[**e** &#124; **E**= =*符号*=*数字*|

*空格*可以由忽略的空格和制表符组成;*符号*是加 （**+**） 或**-** 减 （ ）;*数字*是一个或多个十进制数字。 如果基数字符前没有任何数字，则基数字符后必须至少有一个数字。 十进制数字可以跟一个指数，它由介绍性字母 **（e**或**E**） 和可选签名的整数组成。 如果指数部分和基数字符都没有出现，则假定基数字符跟随字符串中的最后一个数字。 不符合此形式的第一个字符停止扫描。

这些函数的 UCRT 版本不支持转换 Fortran 样式 （**d**或**D**） 指数字母。 这个非标准扩展受早期版本的 CRT 支持，可能会为你的代码的带来重大变化。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**斯特特_strtof_l** **_strtof_l**|C：\<stdlib.h> C++：&lt;cstdlib> 或 \<stdlib.h>|
|**wcstof**， **_wcstof_l**|C：\<stdlib.h> 或 \<wchar.h> C++：&lt;cstdlib>、\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[字符串到数值函数](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod、_strtod_l、wcstod、_wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol、wcstol、_strtol_l、_wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul、_strtoul_l、wcstoul、_wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
