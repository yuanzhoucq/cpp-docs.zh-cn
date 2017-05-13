---
title: "sin、sinf、sinl、sinh、sinhf、sinhl | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sinl
- sinf
- sinhf
- sinh
- sin
- sinhl
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
- _sinl
- sinf
- sinhl
- sinl
- sin
- sinhf
- _sinhl
dev_langs:
- C++
helpviewer_keywords:
- sinh function
- _sinl function
- _sinhl function
- sinhf function
- sinl function
- calculating sines
- sin function
- trigonometric functions
- sinf function
- sinhl function
- hyperbolic functions
ms.assetid: 737de73e-3590-45f9-8257-dc1c0c489dfc
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 8f33398820df9df9de21e7d24cc35f76f131bd43
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="sin-sinf-sinl-sinh-sinhf-sinhl"></a>sin、sinf、sinl、sinh、sinhf、sinhl
计算正弦值和双曲正弦值。  
  
## <a name="syntax"></a>语法  
  
```  
double sin(  
   double x   
);  
float sin(  
   float x  
);  // C++ only  
long double sin(  
   long double x  
);  // C++ only  
float sinf(  
   float x   
);  
long double sinl(   long double x  
);  
double sinh(  
   double x   
);  
float sinh(  
   float x   
);  // C++ only  
long double sinh(  
   long double x  
);  // C++ only  
float sinhf(  
   float x  
);  
long double sinhl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 角度（以弧度为单位）。  
  
## <a name="return-value"></a>返回值  
 `sin` 函数返回 `x` 的正弦值。 如果`x`是大于或等于 263，或小于或等于-263，会丢失基数结果中。  
  
 `sinh` 函数返回 `x` 的双曲正弦值。 默认情况下，如果结果太大，则 `sinh` 将 `errno` 设置为 `ERANGE`，并返回 ±`HUGE_VAL`。  
  
|输入|SEH 异常|Matherr 异常|  
|-----------|-------------------|-----------------------|  
|± QNAN,IND|无|_DOMAIN|  
|± ∞ (sin、sinf、sinl)|INVALID|_DOMAIN|  
|&#124;x&#124; ≥ 7.104760e+002 (sinh、sinhf、sinhl)|溢出 + 不准确|OVERFLOW|  
  
 有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 由于 C++ 允许重载，因此您可以调用 `sin` 和 `sinh` 的重载，这将采用和返回 `float` 或 `long double` 值。 在 C 程序中，`sin` 和 `sinh` 始终采用并返回 `double`。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`sin`, `sinf`, `sinl`, `sinh`, `sinhf`, `sinhl`|\<math.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_sincos.c  
// This program displays the sine, hyperbolic  
// sine, cosine, and hyperbolic cosine of pi / 2.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = pi / 2;  
   y = sin( x );  
   printf( "sin( %f ) = %f\n", x, y );  
   y = sinh( x );  
   printf( "sinh( %f ) = %f\n",x, y );  
   y = cos( x );  
   printf( "cos( %f ) = %f\n", x, y );  
   y = cosh( x );  
   printf( "cosh( %f ) = %f\n",x, y );  
}  
```  
  
```Output  
sin( 1.570796 ) = 1.000000  
sinh( 1.570796 ) = 2.301299  
cos( 1.570796 ) = 0.000000  
cosh( 1.570796 ) = 2.509178  
```  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [tan、tanf、tanl、tanh、tanhf、tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [_CIsin](../../c-runtime-library/cisin.md)
