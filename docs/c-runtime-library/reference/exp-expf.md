---
title: "exp、 expf、 资源管理器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: bce9249134b9d0e3716d8b79a0bc0642c64fc5e6
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="exp-expf-expl"></a>exp、 expf，资源管理器
计算指数。  
  
## <a name="syntax"></a>语法  
  
```  
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
 `x`  
 浮点值到 exponentiate 自然对数底*e*通过。  
  
## <a name="return-value"></a>返回值  
 `exp`函数返回的浮点参数的指数值*x*，如果成功。 结果是，即*e*<sup>*x*</sup>，其中*e*是自然对数的底。 在溢出时，在函数返回 INF （无穷大） 和下溢，`exp`返回 0。  
  
|输入|SEH 异常|Matherr 异常|  
|-----------|-------------------|-----------------------|  
|± Quiet NaN、 不确定|无|_DOMAIN|  
|± 无穷大|INVALID|_DOMAIN|  
|x ≥ 7.097827e+002|INEXACT+OVERFLOW|OVERFLOW|  
|X ≤ -7.083964e+002|INEXACT+UNDERFLOW|UNDERFLOW|  
  
 `exp`函数具有使用流式处理 SIMD 扩展 2 (SSE2) 实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## <a name="remarks"></a>备注  
 C + + 允许重载，因此您可以调用的重载`exp`采用**float**或**长双精度**自变量。 在 C 程序中，`exp`始终采用并返回**double**。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的 C 标头|必需的 C++ 标头|  
|--------------|---------------------|---|  
|`exp`, `expf`|\<math.h>|\<cmath> 或 \<math.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
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
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [_CIexp](../../c-runtime-library/ciexp.md)
