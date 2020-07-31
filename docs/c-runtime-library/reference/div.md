---
title: div、ldiv、lldiv
ms.date: 04/05/2018
api_name:
- div
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 24432ec1514f6cd2d569fd5752a8ed7118059d6a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234219"
---
# <a name="div-ldiv-lldiv"></a>div、ldiv、lldiv

计算两个整数值的商和余数。

## <a name="syntax"></a>语法

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>参数

*收藏*<br/>
分子。

*denom*<br/>
分母。

## <a name="return-value"></a>返回值

**div**使用类型的参数调用的 div **`int`** 返回**div_t**类型的结构，该结构包含商和余数。 具有类型参数的返回值 **`long`** 为**ldiv_t**，且具有类型的参数的返回值 **`long long`** 为**lldiv_t**。 **div_t**、 **ldiv_t**和**lldiv_t**是在中定义的 \<stdlib.h> 。

## <a name="remarks"></a>备注

**Div**函数通过*denom*将*收藏*除以，从而计算商和余数。 [Div_t](../../c-runtime-library/standard-types.md)结构包含**商、商**和**余数。** 商的符号与数学商的符号相同。 其绝对值是小于数学商的绝对值的最大整数。 如果分母为 0，程序将终止并显示错误消息。

采用类型为或的参数的**div**重载 **`long`** **`long long`** 仅可用于 c + + 代码。 [Ldiv_t](../../c-runtime-library/standard-types.md) **和** [lldiv_t](../../c-runtime-library/standard-types.md)的返回类型**包含成员，它们与** **div_t**的成员具有相同的含义。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**div**、 **ldiv**、 **lldiv**|\<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
