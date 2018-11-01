---
title: cos、 cosf、 cosl
ms.date: 04/05/2018
apiname:
- cos
- cosf
- cosl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cos
- cosf
- cosl
helpviewer_keywords:
- cosines
- cosl function
- calculating cosine
- cosf function
- cos function
- trigonometric functions
- cosines, calculating
ms.assetid: ae90435e-6b68-4a47-a81f-be87d5c08f16
ms.openlocfilehash: b050fd98a35028b121def8b665fce62ad58ec437
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519883"
---
# <a name="cos-cosf-cosl"></a>cos、 cosf、 cosl

计算余弦值。

## <a name="syntax"></a>语法

```C
double cos( double x );
float cosf( float x );
long double cosl( long double x );
```

```cpp
float cos( float x );  // C++ only
long double cos( long double x );  // C++ only
```

### <a name="parameters"></a>参数

*x*<br/>
角度（以弧度为单位）。

## <a name="return-value"></a>返回值

余弦*x*。 如果*x*是大于或等于 263，或小于或等于-263，会发生丢失结果中的基数。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|为 QNAN IND|无|**（_D)**|
|为 INF|**无效**|**（_D)**|

## <a name="remarks"></a>备注

由于 c + + 允许重载，可以调用的重载**cos**采用并返回**float**或**长** **double**值。 在 C 程序中， **cos**始终采用并返回**double**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的 C 标头|必需的 C++ 标头|
|-------------|---------------------|-|
|**cos**， **cosh**， **cosf**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅中的示例[sin、 sinf、 sinl](sin-sinf-sinl.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[asin、asinf、asinl](asin-asinf-asinl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
[_CIcos](../../c-runtime-library/cicos.md)<br/>