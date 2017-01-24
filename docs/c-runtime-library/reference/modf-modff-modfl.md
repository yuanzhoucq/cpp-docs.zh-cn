---
title: "modf、 modff modfl | Microsoft Docs"
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
  - "modff"
  - "modf"
  - "modfl"
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
  - "modff"
  - "_modfl"
  - "modf"
  - "modfl"
  - "math/modf"
  - "math/modff"
  - "math/modfl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "modf 函数"
  - "modff 函数"
  - "modfl 函数"
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# modf、 modff modfl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将拆分到小数的浮点值和整数部分。  
  
## 语法  
  
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
  
#### 参数  
 *x*  
 浮点值。  
  
 `intptr`  
 指针，指向存储的整数部分。  
  
## 返回值  
 此函数返回的有符号小数部分 *x*。 无错误返回。  
  
## 备注  
 `modf` 函数分解的浮点值 `x` 为小数和整数部分，其中每个具有相同的符号 `x`。 有符号小数部分 `x` 返回。 整数部分将被视为在浮点值 `intptr.`  
  
 `modf` 提供了使用流式处理 SIMD 扩展 2 \(SSE2\) 的实现。 请参阅 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md) 有关的信息和限制使用 SSE2 实现。  
  
 C \+ \+ 允许重载，因此您可以调用的重载 `modf` 采用并返回 `float` 或 `long double` 参数。 在 C 程序中， `modf` 始终采用两个双精度值并返回一个 double 值。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`modf`, `modff`, `modfl`|C: \< h.h \><br /><br /> C \+ \+:，\< cmath \> 或 \< h.h \>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
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
  
## 输出  
  
```  
For -14.876543, the fraction is -0.876543 and the integer is -14  
```  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)