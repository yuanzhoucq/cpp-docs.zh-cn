---
title: div、 ldiv、 lldiv
ms.date: 04/05/2018
apiname:
- div
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
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 0ee1b3b6a5d7b15470ffe1e667b4077d1f9581e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653422"
---
# <a name="div-ldiv-lldiv"></a>div、 ldiv、 lldiv

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

*号码*<br/>
分子。

*denom*<br/>
分母。

## <a name="return-value"></a>返回值

**div**通过使用类型的自变量调用**int**返回类型的结构**div_t**，其中包括商和余数。 类型的参数的返回值**长**是**ldiv_t**，和返回值类型的参数**长****长**是**lldiv_t**。 **div_t**， **ldiv_t**，和**lldiv_t**中定义\<stdlib.h >。

## <a name="remarks"></a>备注

**Div**函数划分*号码*由*denom* ，从而计算商和余数。 [Div_t](../../c-runtime-library/standard-types.md)结构包含商， **q u o t**，，其余**rem**。商的符号与数学商的符号相同。 其绝对值是小于数学商的绝对值的最大整数。 如果分母为 0，程序将终止并显示错误消息。

重载**div**需要类型的自变量**长**或**长****长**仅可供 c + + 代码。 返回类型[ldiv_t](../../c-runtime-library/standard-types.md)并[lldiv_t](../../c-runtime-library/standard-types.md)包含成员**q u o t**并**rem**，它具有相同的含义的成员**div_t**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**div**， **ldiv**， **lldiv**|\<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
