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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d7d2050be406e7f2be66ca200d1e3cfd9c2960b0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348433"
---
# <a name="cosh-coshf-coshl"></a>cosh、coshf、coshl

计算双曲性抛物。

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

** x <br/>
角度（以弧度为单位）。

## <a name="return-value"></a>返回值

*x*的双曲性抛物素。

默认情况下，如果结果在**cosh、coshf**或**coshf** **coshl**调用中过大，则函数将返回**HUGE_VAL**并将**errno**设置到**ERANGE**。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|• **QNAN**， **IND**|无|**_DOMAIN**|
|*x* = 7.104760e+002|**不准确的**+**溢出**|**溢出**|

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用获取和返回**浮点**值或**长****双**精度值的**cosh**重载。 在 C 程序中 **，cosh**总是获取并返回**一个双**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------|-|
|**科斯夫**，**科斯尔**，**科斯尔**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

见[辛、辛夫、辛赫尔](sinh-sinhf-sinhl.md)中的例子。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh、asinhf、asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>
