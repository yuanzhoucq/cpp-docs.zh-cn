---
title: acos、acosf、acosl
ms.date: 4/2/2020
api_name:
- acosf
- acos
- acosl
- _o_acos
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- acos
- acosl
- acosf
- math/acosf
- math/acosl
helpviewer_keywords:
- acos function
- acosl function
- acosf function
- trigonometric functions
- arccosine function
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
ms.openlocfilehash: b6188c585d2f3b7f2bce1a50569e6bae60ee4942
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220764"
---
# <a name="acos-acosf-acosl"></a>acos、acosf、acosl

计算反余弦值。

## <a name="syntax"></a>语法

```C
double acos( double x );
float acosf( float x );
long double acosl( long double x );
```

```cpp
float acos( float x );   // C++ only
long double acos( long double x );   // C++ only
```

### <a name="parameters"></a>参数

*x*<br/>
介于-1 和1之间的值，用于计算反余弦值（反余弦值）。

## <a name="return-value"></a>返回值

**Acos**函数返回0到π弧度范围内*x*的反余弦。

默认情况下，如果*x*小于-1 或大于1，则**acos**将返回无限值。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± ∞|INVALID|_DOMAIN|
|± QNAN，IND|无|_DOMAIN|
|&#124;x&#124;>1|INVALID|_DOMAIN|

## <a name="remarks"></a>备注

由于 c + + 允许重载，因此你可以调用采用并返回和类型的**acos**的重载 **`float`** **`long double`** 。 在 C 程序中， **acos**始终采用并返回 **`double`** 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**acos**、 **acosf**、 **acosl**|\<math.h>|\<errno.h>|

## <a name="example"></a>示例

此程序提示 -1 到 1 范围内的值。 此范围之外的输入值将产生 `_DOMAIN` 错误消息。 如果输入了有效值，此程序将输出该值的反正弦值和反余弦值。

```C
// crt_asincos.c
// arguments: 0

#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int ac, char* av[] )
{
    double  x,
            y;
    errno_t err;

    // argument checking
    if (ac != 2)
    {
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",
                   av[0]);
        return 1;
    }

    // Convert argument into a double value
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)
    {
        fprintf_s( stderr, "Error converting argument into ",
                   "double value.\n");
        return 1;
    }

    // Arcsine of X
    y = asin( x );
    printf_s( "Arcsine of %f = %f\n", x, y );

    // Arccosine of X
    y = acos( x );
    printf_s( "Arccosine of %f = %f\n", x, y );
}
```

```Output
Arcsine of 0.000000 = 0.000000
Arccosine of 0.000000 = 1.570796
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[asin、asinf、asinl](asin-asinf-asinl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)
