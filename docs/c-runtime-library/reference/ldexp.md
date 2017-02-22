---
title: "ldexp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ldexp"
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
  - "ldexp"
  - "_ldexpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "计算实数"
  - "复合实数"
  - "指数, 浮点数字"
  - "浮点函数, 尾数和指数"
  - "ldexp 函数"
  - "尾数, 浮点值变量"
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# ldexp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将浮点数乘以二的整数幂。  
  
## 语法  
  
```  
double ldexp(    double x,    int exp  ); float ldexp(    float x,    int exp );  // C++ only long double ldexp(    long double x,    int exp );  // C++ only  float ldexpf(    float x,    int exp );  long double ldexpl(    long double x,    int exp );   
```  
  
#### 参数  
 `x`  
 浮点值。  
  
 `exp`  
 整数指数。  
  
## 返回值  
 如果成功，`ldexp` 函数将返回 `x` \* 2<sup>exp</sup> 的值。  溢出时，根据 `x` 的符号，`ldexp` 将返回 \+\/– `HUGE_VAL`；将 `errno` 值设置为 `ERANGE`。  
  
 有关 `errno` 和可能的错误返回值的详细信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用 `float` 或 `long double` 类型的 `ldexp` 重载。  在 C 程序中，`ldexp` 始终采用 `double` 和 `int` 并返回 `double`。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`ldexp`, `ldexpf`, `ldexpl`|\<math.h\>|\<cmath\>|  
  
 有关兼容性信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_ldexp.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 4.0, y;  
   int p = 3;  
  
   y = ldexp( x, p );  
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );  
}  
```  
  
## 输出  
  
```  
4.0 times two to the power of 3 is 32.0  
```  
  
## .NET Framework 等效项  
 [System::Math::Pow](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [modf、 modff modfl](../../c-runtime-library/reference/modf-modff-modfl.md)