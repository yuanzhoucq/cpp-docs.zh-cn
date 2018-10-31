---
title: imaxdiv
ms.date: 04/05/2018
apiname:
- imaxdiv
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- imaxdiv
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
ms.openlocfilehash: 23067b2028fc11193fae707e25165fb0ce754515
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434453"
---
# <a name="imaxdiv"></a>imaxdiv

按单个操作计算两个任意大小整数值的商和余数。

## <a name="syntax"></a>语法

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>参数

*号码*<br/>
分子。

*denom*<br/>
分母。

## <a name="return-value"></a>返回值

**imaxdiv**类型的参数调用[intmax_t](../../c-runtime-library/standard-types.md)返回类型的结构[imaxdiv_t](../../c-runtime-library/standard-types.md) ，包含商和余数。

## <a name="remarks"></a>备注

**Imaxdiv**函数划分*号码*由*denom* ，从而计算商和余数。 **Imaxdiv_t**结构包含商， **intmax_t** **q u o t**，，其余**intmax_t** **rem**.商的符号与数学商的符号相同。 其绝对值是小于数学商的绝对值的最大整数。 如果分母为 0，程序将终止并显示错误消息。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_imaxdiv.c
// Build using: cl /W3 /Tc crt_imaxdiv.c
// This example takes two integers as command-line
// arguments and calls imaxdiv to divide the first
// argument by the second, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x,y;
   imaxdiv_t div_result;

   x = atoll(argv[1]);
   y = atoll(argv[2]);

   printf("The call to imaxdiv(%lld, %lld)\n", x, y);
   div_result = imaxdiv(x, y);
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",
          div_result.quot, div_result.rem);
}
```

在使用命令行参数 `9460730470000000 8766` 进行生成和调用时，代码将生成以下输出：

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
