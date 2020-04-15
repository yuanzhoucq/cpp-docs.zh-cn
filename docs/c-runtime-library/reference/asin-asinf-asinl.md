---
title: asin、asinf、asinl
ms.date: 4/2/2020
api_name:
- asinf
- asinl
- asin
- _o_asin
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- asin
- asinl
- asinf
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
ms.openlocfilehash: 424fee6995fae4a7f878054ede1bb85d33d1706d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334129"
---
# <a name="asin-asinf-asinl"></a>asin、asinf、asinl

计算反正弦值。

## <a name="syntax"></a>语法

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
```

```cpp
float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>参数

** x <br/>
要计算反正弦值的值。

## <a name="return-value"></a>返回值

**asin**函数返回范围 -+/2 到 +/2 弧度中的*x*的弧线（逆正因函数）。

默认情况下，如果*x*小于 -1 或大于 1，**则 asin**返回无限期。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± ∞|**无效**|**_DOMAIN**|
|• **QNAN**， **IND**|无|**_DOMAIN**|
|&#124;x&#124;>1|**无效**|**_DOMAIN**|

## <a name="remarks"></a>备注

由于C++允许重载，因此可以使用**浮点**和**长****双**精度值调用**asin**的重载。 在 C 程序中 **，asin**始终采用并返回**一个双**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------|-|
|**阿辛**，**阿辛夫**，**阿辛**|\<math.h>|\<cmath> 或 \<math.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [acos、acosf、acosl](acos-acosf-acosl.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
