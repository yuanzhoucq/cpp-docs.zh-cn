---
title: "atanh、atanhf、atanhl | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "atanhl"
  - "atanhf"
  - "atanh"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "atanhl"
  - "atanhf"
  - "atanh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atanh 函数"
  - "atanhf 函数"
  - "atanhl 函数"
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atanh、atanhf、atanhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算反双曲正切。  
  
## 语法  
  
```  
double atanh(    double x  ); float atanh(    float x  );  // C++ only long double atanh(    long double x );  // C++ only float atanhf(    float x  ); long double atanhl(    long double x );  
```  
  
#### 参数  
 `x`  
 浮点值。  
  
## 返回值  
 `atanh` 函数返回 `x` 的反双曲正切。  如果 `x` 大于 1 或小于 –1，则将 `errno` 设置为 `EDOM` 且结果是 quiet NaN。  如果 `x` 等于 1 或 \-1，则分别返回正无穷或负无穷且将 `errno` 设置为 `ERANGE`。  
  
|输入|SEH 异常|`Matherr` 异常|  
|--------|------------|------------------|  
|± QNAN,IND|无|无|  
|`X` ≥ 1; `x` ≤ \-1|无|无|  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `float` 或 `long double` 值的 `atanh` 重载。  在 C 程序中，`atanh` 始终采用并返回 `double`。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`atanh`, `atanhf`, `atanhl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_atanh.c  
// This program displays the hyperbolic tangent of pi / 4  
// and the arc hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tanh( pi / 4 );  
   y = atanh( x );  
   printf( "tanh( %f ) = %f\n", pi/4, x );  
   printf( "atanh( %f ) = %f\n", x, y );  
}  
```  
  
  **tanh\( 0.785398 \) \= 0.655794**  
**atanh\( 0.655794 \) \= 0.785398**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [长双精度](../../misc/long-double.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)