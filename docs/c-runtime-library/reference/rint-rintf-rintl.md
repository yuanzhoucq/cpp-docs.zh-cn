---
title: "rint, rintf, rintl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "rintf"
  - "rintl"
  - "rint"
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
  - "rintf"
  - "rintl"
  - "rint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rintf 函数"
  - "rint 函数"
  - "rintl 函数"
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# rint, rintf, rintl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将浮点值舍入到最接近的整数（采用浮点格式）。  
  
## 语法  
  
```  
double rint( double x ); float rint( float x );  // C++ only long double rint( long double x );  // C++ only float rintf( float x );  long double rintl( long double x );    
```  
  
#### 参数  
 `x`  
 要舍入的浮点值。  
  
## 返回值  
 `rint` 函数将返回表示最接近 `x` 的整数的浮点值。  与 `nearbyint` 函数相同，根据浮点舍入模式的当前设置对中间值进行舍入。  与 `nearbyint` 函数不同，如果结果不同于参数中的值，则 `rint` 函数可能会引起 `FE_INEXACT` 浮点异常。  无错误返回。  
  
|输入|SEH 异常|`_matherr` 异常|  
|--------|------------|-------------------|  
|± ∞、QNAN、IND|无|无|  
|非规格化数|EXCEPTION\_FLT\_UNDERFLOW|无|  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `float` 和 `long double` 值的 `rint` 重载。  在 C 程序中，`rint` 始终采用并返回 `double`。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`rint`, `rintf`,`rintl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_rint.c  
// Build with: cl /W3 /Tc crt_rint.c  
// This example displays the rounded results of  
// the floating-point values 2.499999, -2.499999,   
// 2.8, -2.8, 2.5 and -2.5.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.499999;  
   float y = 2.8f;  
   long double z = 2.5;  
  
   printf("rint(%f) is %.0f\n", x, rint (x));  
   printf("rint(%f) is %.0f\n", -x, rint (-x));  
   printf("rintf(%f) is %.0f\n", y, rintf(y));  
   printf("rintf(%f) is %.0f\n", -y, rintf(-y));  
   printf("rintl(%Lf) is %.0Lf\n", z, rintl(z));  
   printf("rintl(%Lf) is %.0Lf\n", -z, rintl(-z));  
}  
```  
  
  **rint\(2.499999\) 等于 2**  
**rint\(\-2.499999\) 等于 \-2**  
**rintf\(2.800000\) 等于 3**  
**rintf\(\-2.800000\) 等于 \-3**  
**rintl\(2.500000\) 等于 3**  
**rintl\(\-2.500000\) 等于 \-3**   
## .NET Framework 等效项  
 [System::Math::Round](https://msdn.microsoft.com/en-us/library/system.math.round.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [lrint、lrintf、lrintl、llrint、llrintf、llrintl](http://msdn.microsoft.com/zh-cn/312fd869-a9c0-4107-bb23-ab8299d04385)   
 [lround、lroundf、lroundl、llround、llroundf、llroundl](../../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)   
 [nearbyint、nearbyintf、nearbyintl](http://msdn.microsoft.com/zh-cn/15111e73-331d-41d1-81b7-3e10df894848)   
 [rint](../../c-runtime-library/reference/rint-rintf-rintl.md)