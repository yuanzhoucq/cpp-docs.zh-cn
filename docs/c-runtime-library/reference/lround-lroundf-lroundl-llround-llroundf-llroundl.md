---
title: "lround、lroundf、lroundl、llround、llroundf、llroundl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "llround"
  - "llroundf"
  - "llroundl"
  - "lroundf"
  - "lround"
  - "lroundl"
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
  - "lround"
  - "lroundl"
  - "llroundl"
  - "llround"
  - "lroundf"
  - "llroundf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "llround 函数"
  - "llroundf 函数"
  - "llroundl 函数"
  - "lround 函数"
  - "lroundf 函数"
  - "lroundl 函数"
ms.assetid: cfb88a35-54c6-469f-85af-f7d695dcfdd8
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# lround、lroundf、lroundl、llround、llroundf、llroundl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将浮点值舍入为最接近的整数。  
  
## 语法  
  
```  
long lround(   
   double x   
);  
long lround(  
   float x  
);  // C++ only  
long lround(  
   long double x  
);  // C++ only  
long lroundf(  
   float x  
);  
long lroundl(  
   long double x  
);  
long long llround(   
   double x   
);  
long long llround(  
   float x  
);  // C++ only  
long long llround(  
   long double x  
);  // C++ only  
long long llroundf(  
   float x  
);  
long long llroundl(  
   long double x  
);  
```  
  
#### 参数  
 `x`  
 要舍入的浮点值。  
  
## 返回值  
 `lround` 和 `llround` 函数将最近的 `long` 或 `long long` 整数返回到 `x`。  无论浮点舍入模式的设置如何，中间的值都远离零舍入。  无错误返回。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± `QNAN`, `IND`|无|`_DOMAIN`|  
  
## 备注  
 由于 C\+\+ 允许重载，您可以调用 `lround` 或 `llround` 的重载，该重载采用和返回 `float` 和 `long double` 值。  在 C 程序中，`lround` 和 `llround` 始终采用并返回 `double`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`lround`, `lroundf`, `lroundl`, `llround`, `llroundf`, `llroundl`|\<math.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_lround.c  
// Build with: cl /W3 /Tc crt_lround.c  
// This example displays the rounded results of  
// the floating-point values 2.499999, -2.499999,   
// 2.8, -2.8, 3.5 and -3.5.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.499999;  
   float y = 2.8f;  
   long double z = 3.5;  
  
   printf("lround(%f) is %d\n", x, lround(x));  
   printf("lround(%f) is %d\n", -x, lround(-x));  
   printf("lroundf(%f) is %d\n", y, lroundf(y));  
   printf("lroundf(%f) is %d\n", -y, lroundf(-y));  
   printf("lroundl(%Lf) is %d\n", z, lroundl(z));  
   printf("lroundl(%Lf) is %d\n", -z, lroundl(-z));  
}  
```  
  
  **lround \(2.499999\) 为 2**  
**lround \(\-2.499999\) 为 \-2**  
**lroundf \(2.800000\) 为 3**  
**lroundf \(\-2.800000\) 为 \-3**  
**lroundl \(2.500000\) 为 4**  
**lroundl \(\-2.500000\) 为 \-4**   
## .NET Framework 等效项  
 [System::Math::Round](https://msdn.microsoft.com/en-us/library/system.math.round.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [lrint、lrintf、lrintl、llrint、llrintf、llrintl](http://msdn.microsoft.com/zh-cn/312fd869-a9c0-4107-bb23-ab8299d04385)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)   
 [nearbyint、nearbyintf、nearbyintl](http://msdn.microsoft.com/zh-cn/15111e73-331d-41d1-81b7-3e10df894848)   
 [rint, rintf, rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)