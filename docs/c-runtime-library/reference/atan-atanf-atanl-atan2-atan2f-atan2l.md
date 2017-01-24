---
title: "atan、atanf、atanl、atan2、atan2f、atan2l | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "atan2f"
  - "atan2l"
  - "atan2"
  - "atanf"
  - "atan"
  - "atanl"
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
  - "atan"
  - "atan2l"
  - "atan2"
  - "atanl"
  - "atanf"
  - "atan2f"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "反正切函数"
  - "atan 函数"
  - "atan2 函数"
  - "atan2f 函数"
  - "atan2l 函数"
  - "atanf 函数"
  - "atanl 函数"
  - "三角函数"
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atan、atanf、atanl、atan2、atan2f、atan2l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算`x`的反正切值 \(`atan`、`atanf`和 `atanl`\) 或`y`\/`x` 的反正切值 \(`atan2`、`atan2f`和 `atan2l`\)。  
  
## 语法  
  
```  
double atan(   
   double x   
);  
float atan(  
   float x   
);  // C++ only  
long double atan(  
   long double x  
);  // C++ only  
double atan2(   
   double y,   
   double x   
);  
float atan2(  
   float y,  
   float x  
);  // C++ only  
long double atan2(  
   long double y,  
   long double x  
);  // C++ only  
float atanf(   
   float x   
);  
long double atanl(  
   long double x  
);  
float atan2f(  
   float y,  
   float x  
);  
long double atan2l(  
   long double y,  
   long double x  
);  
```  
  
#### 参数  
 `x`, `y`  
 任何数量。  
  
## 返回值  
 `atan` 返回 `x` –π\/2 到π\/2弧度范围内的反正切值。  `atan2` 返回 `y/x` –π\/2 到π\/2弧度范围内的反正切值。  如果 `x` 为0，则 `atan`返回0 。  如果 `atan2` 的参数都是 0，则函数返回 0。  所有结果以弧度为单位。  
  
 `atan2` 使用两个参数的符号标识确定返回值的象限。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± `QNAN`,`IND`|无|`_DOMAIN`|  
  
## 备注  
 `atan` 函数求`x`的反正切值 \(反正切函数\) 。  `atan2` 计算 `y`\/`x` 反正切值 \(如果 `x` 等于 0，`atan2` 返回π\/2，如果 `y` 为正数的，\-π\/2，如果 `y` 为负或 0，则 `y` 为 0。\)  
  
 `atan` 具有使用Streaming SIMD Extensions 2\(SSE2\)的实现。  有关使用SSE2实现的信息和限制，请参见 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
 由于 C\+\+ 允许重载，可以调用 `atan`和`atan2`重载函数。  在 C 程序中，`atan` 和 `atan2` 始终采用并返回两个。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`atan`, `atan2`, `atanf`, `atan2f`, `atanl`, `atan2l`|\<math.h\>|  
  
## 示例  
  
```  
// crt_atan.c  
// arguments: 5 0.5  
#include <math.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( int ac, char* av[] )   
{  
   double x, y, theta;  
   if( ac != 3 ){  
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );  
      return 1;  
   }  
   x = atof( av[1] );  
   theta = atan( x );  
   printf( "Arctangent of %f: %f\n", x, theta );  
   y = atof( av[2] );  
   theta = atan2( y, x );  
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );   
   return 0;  
}  
```  
  
  **5.000000的反正切值：1.373401**  
**0.500000 \/ 5.000000的反正切值：0.099669**   
## .NET Framework 等效项  
  
-   [System::Math::Atan](https://msdn.microsoft.com/en-us/library/system.math.atan.aspx)  
  
-   [System::Math::Atan2](https://msdn.microsoft.com/en-us/library/system.math.atan2.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [\_CIatan](../../c-runtime-library/ciatan.md)   
 [\_CIatan2](../../c-runtime-library/ciatan2.md)