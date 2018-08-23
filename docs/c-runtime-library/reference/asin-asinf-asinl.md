---
title: asin、asinf、asinl | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- asinf
- asinl
- asin
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
- asin
- asinl
- asinf
dev_langs:
- C++
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee65e4c8ce884ac42de35a23c81dbf5009dd1185
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393272"
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

**Asin**函数返回的反正弦值 （的反正弦函数） 的*x*到 π/2 弧度范围-π/2 中。

默认情况下，如果*x*小于-1 或大于 1， **asin**返回无穷大。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± ∞|**无效**|**_DOMAIN**|
|± **QNAN**， **IND**|无|**_DOMAIN**|
|&#124;x&#124;>1|**无效**|**_DOMAIN**|

## <a name="remarks"></a>备注

由于 c + + 允许重载，你可以调用的重载**asin**与**float**和**长** **double**值。 在 C 程序中， **asin**始终采用并返回**double**。

## <a name="requirements"></a>要求

|例程|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------|-|
|**asin**， **asinf**， **asinl**|\<math.h>|\<cmath> 或 \<math.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [acos、acosf、acosl](acos-acosf-acosl.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
