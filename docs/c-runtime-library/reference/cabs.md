---
title: _cabs
ms.date: 11/04/2016
api_name:
- _cabs
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cabs
helpviewer_keywords:
- cabs function
- absolute values
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 2c2bd6b3f097095514e47b757306b4d83a990e45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170336"
---
# <a name="_cabs"></a>_cabs

计算复数的绝对值。

## <a name="syntax"></a>语法

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>parameters

*z*<br/>
复数。

## <a name="return-value"></a>返回值

如果成功， **_cabs**返回其参数的绝对值。 溢出时， **_cabs**返回**HUGE_VAL**并将**errno**设置为**ERANGE**。 可以使用 [_matherr](matherr.md) 更改错误处理。

## <a name="remarks"></a>备注

**_Cabs**函数计算复数的绝对值，它必须是[_complex](../../c-runtime-library/standard-types.md)类型的结构。 结构*z*由实部分量*x*和虚部*y*组成。 对 **_cabs**的调用会生成一个与 `sqrt( z.x * z.x + z.y * z.y )`表达式的值等效的值。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_cabs**|\<math.h>|

有关兼容性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)
