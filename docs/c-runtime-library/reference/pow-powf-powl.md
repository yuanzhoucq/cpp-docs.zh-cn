---
title: "pow、powf、powl | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09b618e557fffadd3bfffb431fc7e89458c4f420
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="pow-powf-powl"></a>pow、powf、powl
计算 `x` 的 `y` 次幂。  
  
## <a name="syntax"></a>语法  
  
```  
double pow(  
   double x,  
   double y   
);  
double pow(  
   double x,  
   int y  
);  // C++ only  
float pow(  
   float x,  
   float y   
);  // C++ only  
float pow(  
   float x,  
   int y  
);  // C++ only  
long double pow(  
   long double x,  
   long double y  
);  // C++ only  
long double pow(  
   long double x,  
   int y  
);  // C++ only  
float powf(  
   float x,  
   float y   
);  
long double powl(  
   long double x,  
   long double y  
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 Base。  
  
 `y`  
 Exponent。  
  
## <a name="return-value"></a>返回值  
 返回 `x`<sup>y</sup> 的值。 在溢出或下溢时不输出错误消息。  
  
|x 和 y 的值|pow 的返回值|  
|-----------------------|-------------------------|  
|`x` \< > 0 且 `y` = 0.0|1|  
|`x` = 0.0 且 `y` = 0.0|1|  
|`x` = 0.0 且 `y` < 0|INF|  
  
## <a name="remarks"></a>备注  
 `pow` 无法识别大于 2<sup>64</sup> 的整型浮点值（如 `1.0E100`）。  
  
 `pow` 具有使用流式处理 SIMD 扩展 2 (SSE2) 的实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
 由于 C++ 允许重载，因此你可以调用 `pow` 的任何不同重载。 在 C 程序中，`pow` 始终采用两个双精度值并返回一个双精度值。  
  
 `pow(int, int)` 将不再可用。 如果使用此重载，则编译器可以发出 C2668。 若要避免此问题，将第一个参数转换为 `double`、`float` 或 `long double`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`pow`, `powf`, `powl`|\<math.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_pow.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.0, y = 3.0, z;  
  
   z = pow( x, y );  
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );  
}  
```  
  
## <a name="output"></a>输出  
  
```  
2.0 to the power of 3.0 is 8.0  
```  
  
## <a name="see-also"></a>请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [exp、 expf，资源管理器](../../c-runtime-library/reference/exp-expf.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [sqrt、sqrtf、sqrtl](../../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)   
 [_CIpow](../../c-runtime-library/cipow.md)