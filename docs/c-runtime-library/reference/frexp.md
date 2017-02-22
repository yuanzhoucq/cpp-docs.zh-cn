---
title: "frexp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "frexp"
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
  - "frexp"
  - "_frexpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_frexpl 函数"
  - "指数, 浮点数字"
  - "浮点函数, 尾数和指数"
  - "frexp 函数"
  - "frexpl 函数"
  - "尾数, 浮点值变量"
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# frexp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取一个浮点数的尾数和指数。  
  
## 语法  
  
```  
double frexp(  
   double x,  
   int *expptr   
);  
float frexp(  
   float x,  
   int * expptr  
);  // C++ only  
long double frexp(  
   long double x,  
   int * expptr  
);  // C++ only  
```  
  
#### 参数  
 `x`  
 浮点值。  
  
 `expptr`  
 指向存储的整数指数的指针。  
  
## 返回值  
 `frexp`返回尾数。  如果 `x` 为 0，则函数返回尾数和指数都为 0。  如果 `expptr` 为 `NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回0 。  
  
## 备注  
 `frexp` 函数将浮点分解浮点值 \(`m`\) 为尾数 \(`x`\)和指数 \(`n`\)，此绝对值 `m` 大于或等于 0.5 并且小于 1.0 和 `x` \= `m`\*2。<sup>n</sup> 整数的指数 `n` 存储的位置指向 `expptr`。  
  
 C\+\+ 允许重载，因此可以调用 `frexp` 重载函数。  在 C 程序中，`frexp` 始终采用一个双精度值和一个整型并返回一个双精度值。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`frexp`|\<math.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_frexp.c  
// This program calculates frexp( 16.4, &n )  
// then displays y and n.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y;  
   int n;  
  
   x = 16.4;  
   y = frexp( x, &n );  
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );  
}  
```  
  
  **frexp\( 16.400000, &n \) \= 0.512500, n \= 5**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)   
 [modf、 modff modfl](../../c-runtime-library/reference/modf-modff-modfl.md)