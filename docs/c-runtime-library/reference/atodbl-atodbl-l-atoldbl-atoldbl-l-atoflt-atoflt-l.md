---
title: _atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l
ms.date: 04/05/2018
api_name:
- _atoldbl
- _atoldbl_l
- _atodbl
- _atoflt
- _atoflt_l
- _atodbl_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _atoflt
- _atoflt_l
- atodbl_l
- atoflt_l
- _atoldbl
- _atoldbl_l
- atodbl
- _atodbl_l
- atoldbl
- atoflt
- atoldbl_l
- _atodbl
helpviewer_keywords:
- _atodbl function
- _atoldbl_l function
- atoflt function
- atoflt_l function
- atoldbl function
- _atoldbl function
- atodbl_l function
- _atoflt_l function
- atoldbl_l function
- atodbl function
- string conversion, to floating point values
- _atoflt function
- _atodbl_l function
ms.assetid: 2d2530f4-4bd4-42e3-8083-f2d2fbc8432a
ms.openlocfilehash: 3f3b164042006cab22d0dfd9a7968e2d2e494f5c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943628"
---
# <a name="_atodbl-_atodbl_l-_atoldbl-_atoldbl_l-_atoflt-_atoflt_l"></a>_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l

将字符串转换为双精度（ **_atodbl**）、long double （ **_atoldbl**）或 float （ **_atoflt**）。

## <a name="syntax"></a>语法

```C
int _atodbl( _CRT_DOUBLE * value, char * str );
int _atodbl_l ( _CRT_DOUBLE * value, char * str, locale_t locale );
int _atoldbl( _LDOUBLE * value, char * str );
int _atoldbl_l ( _LDOUBLE * value, char * str, locale_t locale );
int _atoflt( _CRT_FLOAT * value, const char * str );
int _atoflt_l( _CRT_FLOAT * value, const char * str, locale_t locale );
```

### <a name="parameters"></a>参数

*value*<br/>
通过将字符串转换为浮点值生成的双精度型、长双精度型或浮点型值。 这些值都包装在一个结构中。

*str*<br/>
要解析的字符串将转换为浮点值。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，则返回 0。 可能的错误代码是标头文件\<_UNDERFLOW 中定义的或 _OVERFLOW >。

## <a name="remarks"></a>备注

这些函数将字符串转换为浮点值。 这些函数与**atof**系列函数之间的区别是：这些函数不生成浮点代码，也不会导致硬件异常。 改为将错误条件报告为错误代码。

如果字符串不具有作为浮点值的有效解释，则*value*设置为零，返回值为零。

这些具有 **_l**后缀的函数的版本与没有后缀的版本相同，只不过它们使用传入的*区域设置*参数而不是当前线程区域设置。

## <a name="requirements"></a>要求

|例程|必需的标头|
|--------------|---------------------|
|**_atodbl**、 **_atoldbl**、 **_atoflt**<br /><br /> **_atodbl_l**、 **_atoldbl_l**、 **_atoflt_l**|\<stdlib.h>|

## <a name="example"></a>示例

```C
// crt_atodbl.c
// Uses _atodbl to convert a string to a double precision
// floating point value.

#include <stdlib.h>
#include <stdio.h>

int main()
{
   char str1[256] = "3.141592654";
   char abc[256] = "abc";
   char oflow[256] = "1.0E+5000";
   _CRT_DOUBLE dblval;
   _CRT_FLOAT fltval;
   int retval;

   retval = _atodbl(&dblval, str1);

   printf("Double value: %lf\n", dblval.x);
   printf("Return value: %d\n\n", retval);

   retval = _atoflt(&fltval, str1);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // A non-floating point value: returns 0.
   retval = _atoflt(&fltval, abc);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   // Overflow.
   retval = _atoflt(&fltval, oflow);
   printf("Float value: %f\n", fltval.f);
   printf("Return value: %d\n\n", retval);

   return 0;
}
```

```Output
Double value: 3.141593
Return value: 0

Float value: 3.141593
Return value: 0

Float value: 0.000000
Return value: 0

Float value: inf
Return value: 3
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
