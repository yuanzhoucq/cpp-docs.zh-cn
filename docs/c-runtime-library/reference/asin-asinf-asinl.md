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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 98f7babfbfcbfcdbf36b79b70aac33f002e3bc90
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87189436"
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

*x*<br/>
要计算反正弦值的值。

## <a name="return-value"></a>返回值

**Asin**函数返回范围-π/2 到π/2 弧度的*x*的反正弦值（反正弦函数）。

默认情况下，如果*x*小于-1 或大于1，则**asin**将返回无限值。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± ∞|**无效**|**_DOMAIN**|
|± **QNAN**， **IND**|无|**_DOMAIN**|
|&#124;x&#124;>1|**无效**|**_DOMAIN**|

## <a name="remarks"></a>备注

由于 c + + 允许重载，因此可以调用**asin**的重载 **`float`** 和 **`long double`** 值。 在 C 程序中， **asin**始终采用并返回 **`double`** 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------|-|
|**asin**、 **asinf**、 **asinl**|\<math.h>|\<cmath> 或 \<math.h>|

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
