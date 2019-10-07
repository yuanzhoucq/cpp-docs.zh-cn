---
title: sqrt、sqrtf、sqrtl
ms.date: 04/05/2018
api_name:
- sqrtl
- sqrtf
- sqrt
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- sqrt
- sqrtf
- _sqrtl
helpviewer_keywords:
- sqrtf function
- sqrt function
- sqrtl function
- _sqrtl function
- calculating square roots
- square roots, calculating
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
ms.openlocfilehash: 9805141a630afc123c19416595b2a96bc801eee3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958098"
---
# <a name="sqrt-sqrtf-sqrtl"></a>sqrt、sqrtf、sqrtl

计算平方根。

## <a name="syntax"></a>语法

```C
double sqrt(
   double x
);
float sqrt(
   float x
);  // C++ only
long double sqrt(
   long double x
);  // C++ only
float sqrtf(
   float x
);
long double sqrtl(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
非负浮点值

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用采用**浮点**或**长** **双精度**类型的**sqrt**的重载。 在 C 程序中， **sqrt**始终采用并返回**double**。

## <a name="return-value"></a>返回值

**Sqrt**函数返回*x*的平方根。 默认情况下，如果*x*为负数， **sqrt**将返回一个无限的 NaN。

|输入|SEH 异常|**_matherr**异常|
|-----------|-------------------|--------------------------|
|± QNAN，IND|无|_DOMAIN|
|- ∞|无|_DOMAIN|
|x<0|无|_DOMAIN|

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**sqrt**、 **sqrtf**、 **sqrtl**|\<math.h>|\<cmath>|

有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_sqrt.c
// This program calculates a square root.

#include <math.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   double question = 45.35, answer;
   answer = sqrt( question );
   if( question < 0 )
      printf( "Error: sqrt returns %f\n", answer );
   else
      printf( "The square root of %.2f is %.2f\n", question, answer );
}
```

```Output
The square root of 45.35 is 6.73
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[exp、expf、expl](exp-expf.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
[pow、powf、powl](pow-powf-powl.md)<br/>
[_CIsqrt](../../c-runtime-library/cisqrt.md)<br/>
