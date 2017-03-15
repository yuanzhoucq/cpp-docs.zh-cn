---
title: "scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "scalblnl"
  - "scalbnl"
  - "scalbnf"
  - "scalblnf"
  - "scalbn"
  - "scalbln"
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
  - "scalblnf"
  - "scalbnl"
  - "scalblnl"
  - "scalbln"
  - "scalbn"
  - "scalbnf"
dev_langs: 
  - "C++"
ms.assetid: df2f1543-8e39-4af4-a5cf-29307e64807d
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将浮点数乘以 FLT\_RADIX 的整数幂。  
  
## 语法  
  
```  
double scalbn(    double x,    int exp  ); float scalbn(    float x,    int exp );  // C++ only long double scalbn(    long double x,    int exp );  // C++ only  float scalbnf(    float x,    int exp );  long double scalbnl(    long double x,    int exp ); double scalbln(    double x,    long exp  ); float scalbln(    float x,    long exp );  // C++ only long double scalbln(    long double x,    long exp );  // C++ only  float scalblnf(    float x,    long exp );  long double scalblnl(    long double x,    long exp );  
```  
  
#### 参数  
 `x`  
 浮点值。  
  
 `exp`  
 整数指数。  
  
## 返回值  
 如果成功，`scalbn` 函数将返回 `x` \* `FLT_RADIX`<sup>exp</sup> 的值。  溢出时（根据 `x` 的符号），`scalbn` 将返回 \+\/– `HUGE_VAL`；将 `errno` 值设置为 `ERANGE`。  
  
 有关 `errno` 和可能的错误返回值的详细信息，请参阅 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 在 \<float.h\> 中将 `FLT_RADIX` 定义为本机浮点基数；在二进制系统上，它具有值 2，并且 `scalbn` 等效于 [ldexp](../../c-runtime-library/reference/ldexp.md)。  
  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `float` 或 `long double` 类型的 `scalbn` 和 `scalbln` 重载。  在 C 程序中，`scalbn` 始终采用 `double` 和 `int` 并返回 `double`；`scalbln` 始终采用 `double` 和 `long` 并返回 `double`。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`scalbn`, `scalbnf`, `scalbnl`, `scalbln`, `scalblnf`, `scalblnl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_scalbn.c  
// Compile using: cl /W4 crt_scalbn.c  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 6.4, y;  
   int p = 3;  
  
   y = scalbn( x, p );  
   printf( "%2.1f times FLT_RADIX to the power of %d is %2.1f\n", x, p, y );  
}  
```  
  
## 输出  
  
```  
6.4 times FLT_RADIX to the power of 3 is 51.2  
```  
  
## .NET Framework 等效项  
 [System::Math::Pow](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)   
 [modf、 modff modfl](../../c-runtime-library/reference/modf-modff-modfl.md)