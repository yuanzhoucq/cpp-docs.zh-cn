---
title: _set_output_format
ms.date: 11/04/2016
api_name:
- _set_output_format
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_output_format
- _set_output_format
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
ms.openlocfilehash: b67abb58f4d62c7c54b61d1b1699f09c1bd51b40
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957311"
---
# <a name="_set_output_format"></a>_set_output_format

自定义格式化 I/O 函数使用的输出格式。

> [!IMPORTANT]
>  此函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供此函数。

## <a name="syntax"></a>语法

```
unsigned int _set_output_format(
   unsigned int format
);
```

#### <a name="parameters"></a>参数

*format*<br/>
[in] 表示要使用的格式的值。

## <a name="return-value"></a>返回值

以前的输出格式。

## <a name="remarks"></a>备注

`_set_output_format` 用于配置格式化 I/O 函数的输出，如 [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)。 目前，此函数可以更改的唯一格式设置约定是输出浮点数时在指数中显示的位数。

默认情况下，即使不需要使用三位数来表示指数的值，由函数（例如 `printf_s`、 `wprintf_s`等）和 Visual C++ 标准 C 库中的相关函数输出浮点数也会打印表示指数值的三位数。 用零来填充此值，使其成为三位数。 利用`_set_output_format` 可以更改此行为，这样就可以只打印指数中的两位数，除非指数的大小必需具有第三个数字。

若要启用两位数指数，请使用参数 `_TWO_DIGIT_EXPONENT`调用此函数，如示例中所示。 若要禁用两位数指数，请使用参数 0 调用此函数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

有关更多兼容性信息，请参见“简介”中的 [兼容性](../c-runtime-library/compatibility.md) 。

## <a name="example"></a>示例

```C
// crt_set_output_format.c
#include <stdio.h>

void printvalues(double x, double y)
{
   printf_s("%11.4e %11.4e\n", x, y);
   printf_s("%11.4E %11.4E\n", x, y);
   printf_s("%11.4g %11.4g\n", x, y);
   printf_s("%11.4G %11.4G\n", x, y);
}

int main()
{
   double x = 1.211E-5;
   double y = 2.3056E-112;
   unsigned int old_exponent_format;

   // Use the default format
   printvalues(x, y);

   // Enable two-digit exponent format
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);

   printvalues(x, y);

   // Disable two-digit exponent format
   _set_output_format( old_exponent_format );

   printvalues(x, y);
}
```

```Output
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
1.2110e-05 2.3056e-112
1.2110E-05 2.3056E-112
  1.211e-05  2.306e-112
  1.211E-05  2.306E-112
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
```

## <a name="see-also"></a>请参阅

[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_get_output_format](../c-runtime-library/get-output-format.md)
