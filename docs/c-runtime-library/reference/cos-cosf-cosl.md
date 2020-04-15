---
title: cos、cosf、cosl
ms.date: 4/2/2020
api_name:
- cos
- cosf
- cosl
- _o_cos
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
ms.openlocfilehash: 536d9a235ef0d4b2bb68362645b5b4e03d8f37a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348470"
---
# <a name="cos-cosf-cosl"></a>cos、cosf、cosl

计算结果子。

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

** x <br/>
角度（以弧度为单位）。

## <a name="return-value"></a>返回值

*x*的可数。 如果*x*大于或等于 263，或小于或等于 -263，则结果中会发生显著性损失。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|• QNAN，IND|无|**_DOMAIN**|
|• INF|**无效**|**_DOMAIN**|

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用获取和返回**浮点**值或**长****双**精度值的**co**的重载。 在 C 程序中 **，cos**始终获取并返回**一个双**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的 C 标头|必需的 C++ 标头|
|-------------|---------------------|-|
|**科斯**，**科斯**，**科斯 ， 科斯夫**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

见[在辛，鼻法，鼻下](sin-sinf-sinl.md)的例子。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[asin、asinf、asinl](asin-asinf-asinl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
[_CIcos](../../c-runtime-library/cicos.md)<br/>
