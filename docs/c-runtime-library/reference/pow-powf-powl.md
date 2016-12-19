---
title: "pow、powf、powl | Microsoft Docs"
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
  - "powl"
  - "pow"
  - "powf"
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
  - "powl"
  - "pow"
  - "_powl"
  - "powf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_powl 函数"
  - "计算指数"
  - "指数计算"
  - "幂"
  - "pow 函数"
  - "幂, 计算"
  - "powf 函数"
  - "powl 函数"
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pow、powf、powl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算`x`提升到`y`。  
  
## 语法  
  
```  
double pow(  
   double x,  
   double y   
);  
double pow(  
   double x,  
   int y  
);  // C++ only  
float pow(  
   float x,  
   float y   
);  // C++ only  
float pow(  
   float x,  
   int y  
);  // C++ only  
long double pow(  
   long double x,  
   long double y  
);  // C++ only  
long double pow(  
   long double x,  
   int y  
);  // C++ only  
float powf(  
   float x,  
   float y   
);  
long double powl(  
   long double x,  
   long double y  
);  
```  
  
#### 参数  
 `x`  
 基数。  
  
 `y`  
 指数。  
  
## 返回值  
 返回 `x`<sup>y</sup>的值。  错误消息在溢出或下溢时不打印。  
  
|x 和 y 的值|返回pow的值|  
|--------------|-------------|  
|`x`\<\>0 和`y` \= 0.0|1|  
|`x` \= 0.0 和 `y` \= 0.0|1|  
|`x` \= 0.0 和 `y`\< 0|INF|  
  
## 备注  
 `pow` 无法识别大于 2<sup>64</sup>的集成浮点值 \(例如，`1.0E100`\)。  
  
 `pow` 具有使用Streaming SIMD Extensions 2\(SSE2\)的实现。  有关使用SSE2实现的信息和限制，请参见 [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
 由于 C\+\+ 允许重载，可以调用`pow`的任意重载函数。  在 C 程序中，`pow` 始终采用两个双精度值并返回一个双精度值。  
  
 `pow(int, int)`重载不再可用。  如果使用此重载，编译器会发出 C2668。  若要避免此问题，请将第一个参数转换为`double`、`float`或 `long double`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`pow`, `powf`, `powl`|\<math.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_pow.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.0, y = 3.0, z;  
  
   z = pow( x, y );  
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );  
}  
```  
  
## Output  
  
```  
2.0 to the power of 3.0 is 8.0  
```  
  
## .NET Framework 等效项  
 [System::Math::Pow](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [exp、expf](../../c-runtime-library/reference/exp-expf.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [sqrt、sqrtf、sqrtl](../../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)   
 [\_CIpow](../../c-runtime-library/cipow.md)