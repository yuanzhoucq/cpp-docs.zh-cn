---
title: exp、 expf、 资源管理器 |Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- expf
- expl
- exp
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
- _expl
- expf
- expl
- exp
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9569eee475a80fc5c08c2ec1d099cf627c7b5fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="exp-expf-expl"></a>exp、 expf，资源管理器

计算指数。

## <a name="syntax"></a>语法

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点值到 exponentiate 自然对数底*e*通过。

## <a name="return-value"></a>返回值

**Exp**函数返回的浮点参数的指数值*x*，如果成功。 结果是，即*e*<sup>*x*</sup>，其中*e*是自然对数的底。 在溢出时，在函数返回 INF （无穷大） 和下溢， **exp**返回 0。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± Quiet NaN、 不确定|无|_DOMAIN|
|± 无穷大|INVALID|_DOMAIN|
|x ≥ 7.097827e+002|INEXACT+OVERFLOW|OVERFLOW|
|X ≤ -7.083964e+002|INEXACT+UNDERFLOW|UNDERFLOW|

**Exp**函数具有使用流式处理 SIMD 扩展 2 (SSE2) 实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](set-sse2-enable.md)。

## <a name="remarks"></a>备注

C + + 允许重载，因此您可以调用的重载**exp**采用**float**或**长双精度**自变量。 在 C 程序中， **exp**始终采用并返回**double**。

## <a name="requirements"></a>要求

|函数|必需的 C 标头|必需的 C++ 标头|
|--------------|---------------------|---|
|**exp**， **expf**，**资源管理器**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
