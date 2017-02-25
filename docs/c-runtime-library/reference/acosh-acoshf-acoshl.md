---
title: "acosh、acoshf、acoshl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "acoshf"
  - "acosh"
  - "acoshl"
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
  - "acosh"
  - "acoshf"
  - "acoshl"
  - "math/acosh"
  - "math/acoshf"
  - "math/acoshl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acoshf 函数"
  - "acosh 函数"
  - "acoshl 函数"
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# acosh、acoshf、acoshl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算反双曲余弦。  
  
## 语法  
  
```  
double acosh(  
   double x   
);  
float acosh(  
   float x   
);  // C++ only  
long double acosh(  
   long double x  
);  // C++ only  
float acoshf(  
   float x   
);  
long double acoshl(  
   long double x  
);  
```  
  
#### 参数  
 `x`  
 浮点值。  
  
## 返回值  
 `acosh` 函数返回 `x` 的反双曲余弦。 这些函数在 `x` ≥ 1 的域上有效。 如果 `x` 小于 1，则将 `errno` 设置为 `EDOM` 且结果是 quiet NaN。 如果 `x` 是 quiet NaN、不确定数或无穷大，则将返回相同的值。  
  
|输入|SEH 异常|`_matherr` 异常|  
|--------|------------|-------------------|  
|± QNAN, IND, INF|无|无|  
|x \< 1|无|无|  
  
## 备注  
 使用 C\+\+ 时，你可以调用采用并返回 `acosh` 或 `float` 值的 `long double` 重载。 在 C 程序中，`acosh` 始终采用并返回 `double`。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`acosh`, `acoshf`, `acoshl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```c  
// crt_acosh.c  
// Compile by using: cl /W4 crt_acosh.c  
// This program displays the hyperbolic cosine of pi / 4  
// and the arc hyperbolic cosine of the result.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = cosh( pi / 4 );  
   y = acosh( x );  
   printf( "cosh( %f ) = %f\n", pi/4, x );  
   printf( "acosh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
cosh( 0.785398 ) = 1.324609 acosh( 1.324609 ) = 0.785398  
```  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [长双精度](../../misc/long-double.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [asinh、asinhf、asinhl](../../c-runtime-library/reference/asinh-asinhf-asinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [atanh、atanhf、atanhl](../../c-runtime-library/reference/atanh-atanhf-atanhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)