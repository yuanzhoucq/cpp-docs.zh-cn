---
title: cosh、coshf、coshl
ms.date: 4/2/2020
api_name:
- cosh
- coshf
- coshl
- _o_cosh
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: e5e313f08fc7e6d00a1cffc9522d3c8a818cd152
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917230"
---
# <a name="cosh-coshf-coshl"></a>cosh、coshf、coshl

计算双曲余弦值。

## <a name="syntax"></a>语法

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
```

```cpp
float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>参数

*x*<br/>
角度（以弧度为单位）。

## <a name="return-value"></a>返回值

*X*的双曲余弦值。

默认情况下，如果结果在**cosh**、 **coshf**或**coshl**调用中太大，则函数将返回**HUGE_VAL** ，并将**errno**设置为**ERANGE**。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|无|**_DOMAIN**|
|*x* ≥ 7.104760 e + 002|**不精确**+**溢出**|**超出**|

## <a name="remarks"></a>备注

由于 c + + 允许重载，因此你可以调用**cosh**的重载，该重载采用并返回**浮点**或**长****双精度**值。 在 C 程序中， **cosh**始终采用并返回**双精度型**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------|-|
|**coshf**、 **cosl**、 **coshl**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)中的示例。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh、asinhf、asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>
