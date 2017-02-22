---
title: "log、logf、log10、log10f | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "log10f"
  - "logf"
  - "log10"
  - "log"
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
  - "logf"
  - "_log10l"
  - "log"
  - "_logl"
  - "log10f"
  - "log10"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "计算对数"
  - "log10f 函数"
  - "log10 函数"
  - "log 函数"
  - "logf 函数"
  - "对数"
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# log、logf、log10、log10f
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算对数。  
  
## 语法  
  
```  
  
      double log(  
   double x   
);  
float log(  
   float x  
);  // C++ only  
long double log(  
   long double x  
);  // C++ only  
float logf(  
   float x   
);  
double log10(  
   double x  
);  
float log10(  
   float x  
);  // C++ only  
long double log10(  
   long double x  
);  // C++ only  
float log10f (  
   float x  
);  
```  
  
#### 参数  
 *x*  
 对数中找到的值。  
  
## 返回值  
 如果成功，则 **日志** 函数返回 *x* 的自然对数（以e为底数）。  log10 函数返回 10 为底的对数。  如果 *x* 为负，默认情况下这些函数返回一个不定数。  如果 *x* 为 0， 则返回 INF \(无穷大\)。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± QNAN,IND|无|\_DOMAIN|  
|± 0|ZERODIVIDE|\_SING|  
|x \< 0|无效|\_DOMAIN|  
  
 **log** 和 `log10` 具有使用 Streaming SIMD Extensions 2\(SSE2\) 的实现方法。  有关使用 SSE2 实现的信息和限制，请参阅 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## 备注  
 C\+\+ 允许重载，因此可以调用 **log** 和 `log10` 的重载函数。  在 C 程序中，**log** 和`log10` 始终采用并返回一个双精度数。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**log**, `logf`, `log10`, `log10f`|\<math.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_log.c  
/* This program uses log and log10  
 * to calculate the natural logarithm and  
 * the base-10 logarithm of 9,000.  
 */  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 9000.0;  
   double y;  
  
   y = log( x );  
   printf( "log( %.2f ) = %f\n", x, y );  
   y = log10( x );  
   printf( "log10( %.2f ) = %f\n", x, y );  
}  
```  
  
## Output  
  
```  
log( 9000.00 ) = 9.104980  
log10( 9000.00 ) = 3.954243  
```  
  
 若要产生其他基数的对数，使用数学关系：log base b of a \=\= natural log \(a\) \/ natural log \(b\) 。  
  
```  
// logbase.cpp  
#include <math.h>  
#include <stdio.h>  
  
double logbase(double a, double base)  
{  
   return log(a) / log(base);  
}  
  
int main()  
{  
   double x = 65536;  
   double result;  
  
   result = logbase(x, 2);  
   printf("Log base 2 of %lf is %lf\n", x, result);  
}  
```  
  
## Output  
  
```  
Log base 2 of 65536.000000 is 16.000000  
```  
  
## .NET Framework 等效项  
  
-   [System::Math::Log](https://msdn.microsoft.com/en-us/library/system.math.log.aspx)  
  
-   [System::Math::Log10](https://msdn.microsoft.com/en-us/library/system.math.log10.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [exp、expf](../../c-runtime-library/reference/exp-expf.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)   
 [\_CIlog](../../c-runtime-library/cilog.md)   
 [\_CIlog10](../../c-runtime-library/cilog10.md)