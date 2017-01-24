---
title: "hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_hypotf"
  - "hypot"
  - "hypotf"
  - "_hypot"
  - "_hypotl"
  - "hypotl"
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
  - "hypotf"
  - "hypotl"
  - "_hypotl"
  - "hypot"
  - "_hypot"
  - "_hypotf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_hypot 函数"
  - "计算斜边"
  - "hypot 函数"
  - "斜边计算"
  - "hypotf 函数"
  - "hypotl 函数"
  - "三角形, 计算斜边"
ms.assetid: 6a13887f-bd53-43fc-9d77-5b42d6e49925
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算 直角三角形的斜边。  
  
## 语法  
  
```  
double hypot(   
   double x,  
   double y   
);  
float hypotf(   
   float x,  
   float y   
);  
long double hypotl(  
   long double x,  
   long double y  
);  
double _hypot(   
   double x,  
   double y   
);  
float _hypotf(   
   float x,  
   float y   
);  
long double _hypotl(  
   long double x,  
   long double y  
);  
```  
  
#### 参数  
 `x`, `y`  
 浮点值  
  
## 返回值  
 如果成功，`hypot` 返回根个字符串的长度；在溢出，`hypot` 返回 INF \(无穷大\)，并且 `errno` 变量设置为 `ERANGE`。  可以使用 `_matherr` 修改错误处理。  
  
 有关返回代码的详细信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `hypot` 函数求值直角三角形的长度，给出的两边为 `x` 和 `y` \(换言之，根的长度 `x`<sup>2</sup> \+ `y`<sup>2</sup>\)。  
  
 这个会导致下划线的函数已经提供与以前标准具有兼容性的版本了。  它们的行为与没有前导下划线的版本相同。  建议使用版本，而不会导致下划线的新代码。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`hypot`, `hypotf`, `hypotl`, `_hypot`, `_hypotf`, `_hypotl`|\<math.h\>|  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_hypot.c  
// This program prints the hypotenuse of a right triangle.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 3.0, y = 4.0;  
  
   printf( "If a right triangle has sides %2.1f and %2.1f, "  
           "its hypotenuse is %2.1f\n", x, y, _hypot( x, y ) );  
}  
```  
  
  **如果直角三角形具有边 3.0 和 4.0，它的直角边是 5.0**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)