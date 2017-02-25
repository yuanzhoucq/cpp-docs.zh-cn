---
title: "tan, tanf, tanl, tanh, tanhf, tanhl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "tanhf"
  - "tanh"
  - "tan"
  - "tanhl"
  - "tanf"
  - "tanl"
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
  - "tanh"
  - "tan"
  - "_tanl"
  - "tanl"
  - "_tanhl"
  - "tanf"
  - "tanhf"
  - "tanhl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tanl 函数"
  - "tanhl 函数"
  - "_tanl 函数"
  - "_tanhl 函数"
  - "tan 函数"
  - "计算正切值"
  - "正切值"
  - "tanh 函数"
  - "tanhf 函数"
  - "tanf 函数"
  - "三角函数"
  - "双曲函数"
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# tan, tanf, tanl, tanh, tanhf, tanhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算正切值 \(`tan`、`tanf`或 `tanl`\)，或者双曲线的正切值 \(`tanh`、`tanhf`或 `tanhl`\)。  
  
## 语法  
  
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
  
#### 参数  
 `x`  
 弧度上的角度。  
  
## 返回值  
 `tan` 函数返回 `x` 的正切值。  如果 `x` 大于等于 263 或者小于等于– 263，将出现在结果中有效位丢失。  
  
 `tanh` 函数返回 `x` 的双曲线的正切值。  无错误返回。  
  
|输入|SEH 异常|`Matherr` 异常|  
|--------|------------|------------------|  
|± QNAN,IND|无|\_DOMAIN|  
|± ∞  \(`tan`, `tanf`\)|`INVALID`|\_DOMAIN|  
  
## 备注  
 由于 C\+\+ 允许重载，您可以调用 `tan` 和 `tanh` 的重载，该重载采用和返回 `float` 或 `long double` 值。  在 C 程序中，`tan` 和 `tanh` 始终采用并返回 `double`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`tan`, `tanf`, `tanl`, `tanh`, `tanhf`, `tanhl`|\<math.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
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
  
  **tan\( 0.785398 \) \= 1.000000**  
**tanh\( 1.000000 \) \= 0.761594**   
## .NET Framework 等效项  
  
-   [System::Math::Tan](https://msdn.microsoft.com/en-us/library/system.math.tan.aspx)  
  
-   [System::Math::Tanh](https://msdn.microsoft.com/en-us/library/system.math.tanh.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [长双精度](../../misc/long-double.md)   
 [acos、acosf、acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin、asinf、asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)