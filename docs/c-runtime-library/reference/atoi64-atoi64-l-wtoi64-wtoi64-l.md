---
title: _atoi64、_atoi64_l、_wtoi64、_wtoi64_l | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _atoi64_l
- _wtoi64
- _atoi64
- _wtoi64_l
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
- _atoi64
- _tstoi64
- _ttoi64
- wtoi64
- _tstoi64_l
- atoi64
- _wtoi64_l
- _wtoi64
- wtoi64_l
- _atoi64_l
- atoi64_l
dev_langs:
- C++
helpviewer_keywords:
- tstoi64 function
- wtoi64 function
- atoi64_l function
- _ttoi64 function
- string conversion, to integers
- wtoi64_l function
- atoi64 function
- _tstoi64 function
- _atoi64_l function
- _wtoi64_l function
- ttoi64 function
- _wtoi64 function
- _atoi64 function
ms.assetid: 2c3e30fd-545d-4222-8364-0c5905df9526
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fbb0f49edcba73bdf2b7e83d6495573cc2cc0567
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396672"
---
# <a name="atoi64-atoi64l-wtoi64-wtoi64l"></a>_atoi64、_atoi64_l、_wtoi64、_wtoi64_l

将字符串转换为 64 位整数。

## <a name="syntax"></a>语法

```C
__int64 _atoi64(
   const char *str
);
__int64 _wtoi64(
   const wchar_t *str
);
__int64 _atoi64_l(
   const char *str,
   _locale_t locale
);
__int64 _wtoi64_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*str*<br/>
要转换的字符串。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

每个函数返回 **__int64**值生成的输入的字符解释为数字。 返回值为 0 **_atoi64**如果输入不能转换为该类型的值。

对于大量正整数值，与溢出 **_atoi64**返回**I64_MAX**和**I64_MIN**对于大量负整数值的溢出。

在所有范围外的情况下， **errno**设置为**ERANGE**。 如果传递的参数是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回 0。

## <a name="remarks"></a>备注

这些函数将字符串转换为 64 位整数值。

输入字符串是一系列字符，可以解释为指定类型的数值。 该函数在首个它无法无法识别为数字一部分的字符处停止读取输入字符串。 此字符可能是终止字符串的 null 字符（'\0' 或 L'\0'）。

*Str*参数 **_atoi64**具有以下形式：

> [*空白*] [*登录*] [*数字*]

A*空白*空格或制表符字符，将被忽略; 组成*登录*是加号 （+） 或减号 （-）; 和*数字*是一个或多个数字。

**_wtoi64**等同于 **_atoi64** ，但前者将宽字符字符串作为参数。

使用这些函数的版本 **_l**后缀是相同，只不过它们使用传递而不是当前区域设置的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoi64**|**_atoi64**|**_atoi64**|**_wtoi64**|
|**_ttoi64**|**_atoi64**|**_atoi64**|**_wtoi64**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|--------------|---------------------|
|**_atoi64**， **_atoi64_l**|\<stdlib.h>|
|**_wtoi64**， **_wtoi64_l**|\<stdlib.h> 或 \<wchar.h>|

## <a name="example"></a>示例

此程序说明如何将存储为字符串的数字转换为数字值使用 **_atoi64**函数。

```C
// crt_atoi64.c
// This program shows how numbers stored as
// strings can be converted to numeric values
// using the _atoi64 functions.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    __int64 value = 0;

    // An example of the _atoi64 function
    // with leading and trailing white spaces.
    str = "  -2309 ";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );

    // Another example of the _atoi64 function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );

    // Another example of the _atoi64 function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: _atoi64( "  -2309 " ) = -2309
Function: _atoi64( "314127.64" ) = 314127
Function: _atoi64( "3336402735171707160320" ) = -1
Overflow condition occurred.
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
