---
title: atoi、_atoi_l、_wtoi、_wtoi_l
ms.date: 4/2/2020
api_name:
- _wtoi
- _wtoi_l
- atoi
- _atoi_l
- _o__atoi_l
- _o__wtoi
- _o__wtoi_l
- _o_atoi
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tstoi
- _wtoi
- _ttoi
- atoi
- _atoi_l
- _wtoi_l
helpviewer_keywords:
- _atoi_l function
- ttoi function
- atoi_l function
- string conversion, to integers
- _wtoi function
- wtoi_l function
- tstoi function
- _ttoi function
- _tstoi function
- _wtoi_l function
- atoi function
- wtoi function
ms.assetid: ad7fda30-28ab-421f-aaad-ef0b8868663a
ms.openlocfilehash: b8be8af9fc56eea0011e5b07c1573dfe848b6c7d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919867"
---
# <a name="atoi-_atoi_l-_wtoi-_wtoi_l"></a>atoi、_atoi_l、_wtoi、_wtoi_l

将字符串转换为整数。

## <a name="syntax"></a>语法

```C
int atoi(
   const char *str
);
int _wtoi(
   const wchar_t *str
);
int _atoi_l(
   const char *str,
   _locale_t locale
);
int _wtoi_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*字符串*<br/>
要转换的字符串。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

每个函数都返回通过将输入字符解释为数字而产生的**int**值。 如果输入不能转换为该类型的值，则**atoi**和 **_wtoi**的返回值为0。

对于具有大量负整数值的溢出，将返回**LONG_MIN** 。 **atoi**和 **_wtoi**返回这些条件**INT_MAX**和**INT_MIN** 。 在所有超出范围的情况下， **errno**设置为**ERANGE**。 如果传入的参数为**NULL**，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将**errno**设置为**EINVAL** ，并返回0。

## <a name="remarks"></a>备注

这些函数将字符串转换为整数值（**atoi**和 **_wtoi**）。 输入字符串是一系列字符，可以解释为指定类型的数值。 该函数在首个它无法无法识别为数字一部分的字符处停止读取输入字符串。 此字符可能是终止字符串的空字符（'\0' 或 L'\0'）。

**Atoi**和 **_wtoi**的*str*参数具有以下形式：

> [*空格*][*sign*][*数字*]]

*空白*包含被忽略的空格或制表符;*sign*为加号（+）或减号（-）;和*数字*是一个或多个数字。

这些具有 **_l**后缀的函数的版本相同，只不过它们使用传入的区域设置参数而不是当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstoi**|**atoi**|**atoi**|**_wtoi**|
|**_ttoi**|**atoi**|**atoi**|**_wtoi**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|--------------|---------------------|
|**atoi**|\<stdlib.h>|
|**_atoi_l**、 **_wtoi** **_wtoi_l**|\<stdlib.h> 或 \<wchar.h>|

## <a name="example"></a>示例

此程序说明如何使用**atoi**函数将存储为字符串的数字转换为数值。

```C
// crt_atoi.c
// This program shows how numbers
// stored as strings can be converted to
// numeric values using the atoi functions.

#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    int     value = 0;

    // An example of the atoi function.
    str = "  -2309 ";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );

    // Another example of the atoi function.
    str = "31412764";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );

    // Another example of the atoi function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoi( "  -2309 " ) = -2309
Function: atoi( "31412764" ) = 31412764
Function: atoi( "3336402735171707160320" ) = 2147483647
Overflow condition occurred.
```

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
