---
title: "div | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2090ca5e08af74854177f02d6313d6c1304ed2c6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="div"></a>div
计算两个整数值的商和余数。  
  
## <a name="syntax"></a>语法  
  
```  
div_t div(   
   int numer,  
   int denom   
);  
ldiv_t div(  
   long numer,  
   long denom  
); /* C++ only */   
lldiv_t div(  
   long long numer,  
   long long denom  
); /* C++ only */  
```  
  
#### <a name="parameters"></a>参数  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## <a name="return-value"></a>返回值  
 使用 `div` 类型的参数调用的 `int` 将返回 `div_t` 类型的结构，其包含商和余数。 具有 `long` 类型参数的重载的返回值为 `ldiv_t`。 `div_t` 和 `ldiv_t` 均是在 STDLIB.H. 中定义的。  
  
## <a name="remarks"></a>备注  
 `div` 函数将`numer` 除以 `denom`，从而计算商和余数。 [div_t](../../c-runtime-library/standard-types.md) 结构包含商、`int quot` 和余数 `int rem`。 商的符号与数学商的符号相同。 其绝对值是小于数学商的绝对值的最大整数。 如果分母为 0，程序将终止并显示错误消息。  
  
 采用 `long` 或 `long long` 类型参数的重载仅可供 C++ 代码使用。 返回类型 [ldiv_t](../../c-runtime-library/standard-types.md) 包含成员 `long quot` 和 `long rem`，而返回类型 [lldiv_t](../../c-runtime-library/standard-types.md) 包含成员 `long long quot` 和 `long long rem`，其与 `div_t` 的成员具有相同的含义。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`div`|\<stdlib.h>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
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
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)