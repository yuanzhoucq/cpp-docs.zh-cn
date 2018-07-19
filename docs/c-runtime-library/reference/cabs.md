---
title: _cabs | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _cabs
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
- cabsl
- _cabs
- _cabsl
dev_langs:
- C++
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80ea966b748407d51283823073a0c10a40717cf5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393532"
---
# <a name="cabs"></a>_cabs

计算复数的绝对值。

## <a name="syntax"></a>语法

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>参数

*z*<br/>
复数。

## <a name="return-value"></a>返回值

**_cabs**如果成功返回其自变量的绝对值。 在溢出时， **_cabs**返回**HUGE_VAL**和设置**errno**到**ERANGE**。 可以使用 [_matherr](matherr.md) 更改错误处理。

## <a name="remarks"></a>备注

**_Cabs**函数计算绝对值的数值的复数，它必须是类型的结构[_complex](../../c-runtime-library/standard-types.md)。 结构*z*由组成实分量*x*和虚部*y*。 调用 **_cabs**生成等效的表达式值`sqrt( z.x * z.x + z.y * z.y )`。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_cabs**|\<math.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)   