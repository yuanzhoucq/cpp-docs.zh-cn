---
title: "exp、expf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "expf"
  - "exp"
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
  - "_expl"
  - "expf"
  - "exp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "指数计算"
  - "expf 函数"
  - "计算指数"
  - "exp 函数"
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# exp、expf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算指数。  
  
## 语法  
  
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
```  
  
#### 参数  
 `x`  
 浮点值。  
  
## 返回值  
 如果成功，`exp` 函数返回浮点参数 `x` 的指数值。  即结果是e的 `x` 次幂，e是自然对数的底数。  对于溢出，函数返回 INF \(无穷大\) 和对于下溢，`exp` 返回 0。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± QNAN,IND|无|\_DOMAIN|  
|± ∞|无效|\_DOMAIN|  
|x ≥ 7.097827e\+002|不精确\+溢出|溢出。|  
|x ≤ \-7.083964e\+002|INEXACT\+UNDERFLOW|UNDERFLOW|  
  
 `exp` 具有使用Streaming SIMD Extensions 2\(SSE2\)的实现。  有关使用 SSE2 实现的信息和限制，请参阅 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## 备注  
 C\+\+ 允许重载，因此可以调用 `exp` 重载函数。  在 C 程序中，`exp` 始终采用并返回double值。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`exp`, `expf`|\<math.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
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
  
  **exp\( 2.302585 \) \= 10.000000**   
## .NET Framework 等效项  
 [System::Math::Exp](https://msdn.microsoft.com/en-us/library/system.math.exp.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [\_CIexp](../../c-runtime-library/ciexp.md)