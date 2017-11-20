---
title: "modf、modff、modfl | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- modff
- modf
- modfl
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
dev_langs: C++
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72568970159c1b334232bb81f0295d829a5221af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="modf-modff-modfl"></a>modf、modff、modfl
将浮点值拆分为小数部分和整数部分。  
  
## <a name="syntax"></a>语法  
  
```  
double modf(  
   double x,  
   double * intptr   
);  
float modf(  
   float x,  
   float * intptr  
);  // C++ only  
long double modf(  
   long double x,  
   long double * intptr  
);  // C++ only  
float modff(  
   float x,  
   float * intptr   
);  
long double modfl(  
   long double x,  
   long double * intptr  
);  
```  
  
#### <a name="parameters"></a>参数  
 *x*  
 浮点值。  
  
 `intptr`  
 指向存储整数部分的指针。  
  
## <a name="return-value"></a>返回值  
 此函数返回 *x* 的有符号小数部分。 无错误返回。  
  
## <a name="remarks"></a>备注  
 `modf` 函数将浮点值 `x` 拆分为小数和整数部分，每个部分的符号与 `x` 相同。 返回 `x` 的有符号小数部分。 整数部分作为浮点值存储在 `intptr.` 中  
  
 `modf` 具有使用流式处理 SIMD 扩展 2 (SSE2) 的实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
 C++ 允许重载，因此可以调用采用并返回 `float` 或 `long double` 参数的 `modf` 重载。 在 C 程序中，`modf` 始终采用两个双精度值并返回一个双精度值。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`modf`, `modff`, `modfl`|C：\<math.h><br /><br /> C++：\<cmath> 或 \<math.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_modf.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y, n;  
  
   x = -14.87654321;      /* Divide x into its fractional */  
   y = modf( x, &n );     /* and integer parts            */  
  
   printf( "For %f, the fraction is %f and the integer is %.f\n",   
           x, y, n );  
}  
```  
  
## <a name="output"></a>输出  
  
```  
For -14.876543, the fraction is -0.876543 and the integer is -14  
```  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)