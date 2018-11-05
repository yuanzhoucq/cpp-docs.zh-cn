---
title: atoi、_atoi_l、_wtoi、_wtoi_l
ms.date: 11/04/2016
apiname:
- _wtoi
- _wtoi_l
- atoi
- _atoi_l
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
ms.openlocfilehash: 5c03f2766701f7e360ad0bf4f0fc701d2a7e983c
ms.sourcegitcommit: b401a05c5c0f5cc4b32893d7382c05a51e4ab783
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2018
ms.locfileid: "50999981"
---
# <a name="atoi-atoil-wtoi-wtoil"></a>atoi、_atoi_l、_wtoi、_wtoi_l

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

*str*<br/>
要转换的字符串。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

每个函数返回**int**产生的输入的字符解释为数字值。 返回值为 0 **atoi**并 **_wtoi**，如果输入不能转换为该类型的值。

对于大量负整数值的溢出**LONG_MIN**返回。 **atoi**并 **_wtoi**返回**INT_MAX**并**INT_MIN**在这些情况。 在所有超出范围情况下， **errno**设置为**ERANGE**。 如果传入的参数是**NULL**，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，这些函数将设置**errno**到**EINVAL** ，返回 0。

## <a name="remarks"></a>备注

这些函数将字符串转换为整数值 (**atoi**并 **_wtoi**)。 输入字符串是一系列字符，可以解释为指定类型的数值。 该函数在首个它无法无法识别为数字一部分的字符处停止读取输入字符串。 此字符可能是终止字符串的空字符（'\0' 或 L'\0'）。

*Str*自变量**atoi**并 **_wtoi**具有以下形式：

> [*空格*] [*登录*] [*数字*]]

一个*空格*包含的空格或制表符字符，将被忽略;*符号*可以是加号 （+） 或减号 （–）; 并且*数字*是一个或多个数字。

使用这些函数的版本 **_l**后缀完全相同，只不过它们使用传递中而不是当前区域设置的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstoi**|**atoi**|**atoi**|**_wtoi**|
|**_ttoi**|**atoi**|**atoi**|**_wtoi**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|--------------|---------------------|
|**atoi**|\<stdlib.h>|
|**_atoi_l**， **_wtoi**， **_wtoi_l**|\<stdlib.h> 或 \<wchar.h>|

## <a name="example"></a>示例

此程序说明如何将存储为字符串的数字转换为数字值使用**atoi**函数。

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

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
