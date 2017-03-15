---
title: "tan、tanf、tanl、tanh、tanhf、tanhl | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- tanhf
- tanh
- tan
- tanhl
- tanf
- tanl
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
- tanh
- tan
- _tanl
- tanl
- _tanhl
- tanf
- tanhf
- tanhl
dev_langs:
- C++
helpviewer_keywords:
- tanl function
- tanhl function
- _tanl function
- _tanhl function
- tan function
- calculating tangents
- tangent
- tanh function
- tanhf function
- tanf function
- trigonometric functions
- hyperbolic functions
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 94ad2866dc8b2284d674ccfa284646aac9a68efa
ms.lasthandoff: 02/24/2017

---
# <a name="tan-tanf-tanl-tanh-tanhf-tanhl"></a>tan, tanf, tanl, tanh, tanhf, tanhl
计算正切值（`tan`、`tanf` 或 `tanl`）或双曲正切值（`tanh`、`tanhf` 或 `tanhl`）。  
  
## <a name="syntax"></a>语法  
  
```  
double tan(  
   double x   
);  
float tan(  
   float x   
);  // C++ only  
long double tan(  
   long double x  
);  // C++ only  
float tanf(  
   float x   
);  
long double tanl(  
   long double x  
);  
double tanh(  
   double x   
);  
float tanh(  
   float x   
);  // C++ only  
long double tanh(  
   long double x  
);  // C++ only  
float tanhf(  
   float x   
);  
long double tanhl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 角度（以弧度为单位）。  
  
## <a name="return-value"></a>返回值  
 `tan` 函数返回 `x` 的正切值。 如果 `x` 大于等于 263，或小于等于 –263，则结果会丢失基数。  
  
 `tanh` 函数返回 `x` 的双曲正切值。 无错误返回。  
  
|输入|SEH 异常|`Matherr` 异常|  
|-----------|-------------------|-------------------------|  
|± QNAN,IND|无|_DOMAIN|  
|± ∞  (`tan`, `tanf`)|`INVALID`|_DOMAIN|  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此您可以调用 `tan` 和 `tanh` 的重载，这将采用和返回 `float` 或 `long double` 值。 在 C 程序中，`tan` 和 `tanh` 始终采用并返回 `double`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`tan`, `tanf`, `tanl`, `tanh`, `tanhf`, `tanhl`|\<math.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_tan.c  
// This program displays the tangent of pi / 4  
// and the hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tan( pi / 4 );  
   y = tanh( x );  
   printf( "tan( %f ) = %f\n", pi/4, x );  
   printf( "tanh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
tan( 0.785398 ) = 1.000000  
tanh( 1.000000 ) = 0.761594  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
  
-   [System::Math::Tan](https://msdn.microsoft.com/en-us/library/system.math.tan.aspx)  
  
-   [System::Math::Tanh](https://msdn.microsoft.com/en-us/library/system.math.tanh.aspx)  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [_CItan](../../c-runtime-library/citan.md)
