---
title: "fmod, fmodf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fmod"
  - "fmodf"
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
  - "fmod"
  - "_fmodl"
  - "fmodf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "计算浮点余数"
  - "fmodf 函数"
  - "fmodf 函数"
  - "浮点数, 计算余数"
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# fmod, fmodf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算浮点余数。  
  
## 语法  
  
```  
double fmod(   
   double x,  
   double y   
);  
float fmod(  
   float x,  
   float y   
);  // C++ only  
long double fmod(  
   long double x,  
   long double y  
);  // C++ only  
float fmodf(   
   float x,  
   float y   
);  
```  
  
#### 参数  
 `x`, `y`  
 浮点值  
  
## 返回值  
 `fmod` 返回 `x` \/ `y` 的浮点余数。  如果 `y` 的值为 0.0，则 `fmod` 将返回安静 NaN。  有关`printf` 系列的安静 NaN 的表示形式 的详细信息，请参阅 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
## 备注  
 `fmod` 函数计算 `x` 除以 `y` 的 `f` 浮点余数，这样  `x` \= `i` `*` `y` \+ `f`，其中 `i` 是整数，`f` 和 `x` 有相同的符号，而且 `f` 的绝对值小于 `y` 的绝对值。  
  
 C\+\+ 允许重载，因此可以调用 `fmod` 重载函数。  在 C 程序中，`fmod` 始终采用两个双精度值并返回一个双精度值。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fmod`, `fmodf`|\<math.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fmod.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = fmod( w, x );  
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );  
}  
```  
  
  **\-10.00 除以 3.00 的余数是 \-1.000000**   
## .NET Framework 等效项  
 [System::Math::IEEERemainder](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [\_CIfmod](../../c-runtime-library/cifmod.md)