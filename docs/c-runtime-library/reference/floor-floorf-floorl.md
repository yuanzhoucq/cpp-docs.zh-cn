---
title: "floor、floorf、floorl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "floorf"
  - "floorl"
  - "floor"
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
  - "floor"
  - "floorl"
  - "_floorl"
  - "floorf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "计算值的下限"
  - "floor 函数"
  - "floorf 函数"
  - "floorl 函数"
ms.assetid: e9955f70-d659-414f-8050-132e13c8ff36
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# floor、floorf、floorl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算值的floor值  
  
## 语法  
  
```  
double floor(  
   double x  
);  
float floor(  
   float x   
); // C++ only  
long double floor(  
   long double x  
); // C++ only  
float floorf(  
   float x  
);  
long double floorl(  
   long double x  
);  
```  
  
#### 参数  
 `x`  
 浮点值。  
  
## 返回值  
 `floor` 函数返回表示最大整数的浮点值，该值小于或等于 `x`。  无错误返回。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± QNAN,IND|无|\_DOMAIN|  
  
 `floor` 具有使用Streaming SIMD Extensions 2\(SSE2\)的实现。  有关使用SSE2实现的信息和限制，请参见 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## 备注  
 C\+\+ 允许重载，因此您可以调用 `floor` 的重载，该重载采用和返回 `float`和`long double` 值。  在 C 程序中，`floor` 始终采用并返回 `double`。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`floor`, `floorf`, `floorl`|\<math.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_floor.c  
// This example displays the largest integers  
// less than or equal to the floating-point values 2.8  
// and -2.8. It then shows the smallest integers greater  
// than or equal to 2.8 and -2.8.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double y;  
  
   y = floor( 2.8 );  
   printf( "The floor of 2.8 is %f\n", y );  
   y = floor( -2.8 );  
   printf( "The floor of -2.8 is %f\n", y );  
  
   y = ceil( 2.8 );  
   printf( "The ceil of 2.8 is %f\n", y );  
   y = ceil( -2.8 );  
   printf( "The ceil of -2.8 is %f\n", y );  
}  
```  
  
  **2.8的floor值是2.000000。**  
**\-2.8的floor值是\-3.000000。**  
**2.8的ceil值为 3.000000**  
**\-2.8的ceil值为 \-2.000000**   
## .NET Framework 等效项  
 [System::Math::Floor](https://msdn.microsoft.com/en-us/library/system.math.floor.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)