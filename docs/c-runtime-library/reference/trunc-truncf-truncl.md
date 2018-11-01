---
title: trunc、truncf、truncl
ms.date: 04/05/2018
apiname:
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: 6e023b9d894ea1b40a0e056e73b7c32f1e3cbed7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519855"
---
# <a name="trunc-truncf-truncl"></a>trunc、truncf、truncl

确定小于或等于指定浮点值的最接近的整数。

## <a name="syntax"></a>语法

```C
double trunc( double x );
float trunc( float x ); //C++ only
long double truncl( long double x );
```

```cpp
long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>参数

*x*<br/>
要截断的值。

## <a name="return-value"></a>返回值

如果成功，返回的整数值*x*向零舍入。

否则，可能返回以下值之一：

|问题|返回|
|-----------|------------|
|*x* = ±INFINITY|x|
|*x* = ±0|x|
|*x* = NaN|NaN|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

由于 c + + 允许重载，可以调用的重载**trunc**采用并返回**float**并**长** **double**类型。 在 C 程序中， **trunc**始终采用并返回**double**。

由于最大的浮点值是精确的整数，因此该函数不会自行溢出。 但是，将值还原为整型时可能会导致此函数溢出。

还可以通过从浮点隐式转换为整数来向下舍入；但是此操作仅限于可存储为目标类型的值。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**trunc**， **truncf**， **truncl**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[round、roundf、roundl](round-roundf-roundl.md)<br/>
