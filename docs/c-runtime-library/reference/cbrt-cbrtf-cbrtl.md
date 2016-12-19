---
title: "cbrt、cbrtf、cbrtl | Microsoft Docs"
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
  - "cbrt"
  - "cbrtf"
  - "cbrtl"
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
  - "cbrtl"
  - "cbrt"
  - "cbrtf"
dev_langs: 
  - "C++"
ms.assetid: ab51d916-3db2-4beb-b46a-28b4062cd33f
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cbrt、cbrtf、cbrtl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算立方根。  
  
## 语法  
  
```  
double cbrt(    double x  ); float cbrt(    float x  );  // C++ only long double cbrt(    long double x );  // C++ only float cbrtf(    float x  ); long double cbrtl(    long double x );  
```  
  
#### 参数  
 `x`  
 浮点值  
  
## 返回值  
 `cbrt` 函数返回 `x` 的立方根。  
  
|输入|SEH 异常|`_matherr` 异常|  
|--------|------------|-------------------|  
|± ∞、QNAN、IND|无|无|  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用 `float` 或 `long double` 类型的 `cbrt` 重载。  在 C 程序中，`cbrt` 始终采用并返回 `double`。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`cbrt`, `cbrtf`, `cbrtl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```c  
// crt_cbrt.c  
// Compile using: cl /W4 crt_cbrt.c  
// This program calculates a cube root.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double question = -64.64;  
   double answer;  
  
   answer = cbrt(question);  
   printf("The cube root of %.2f is %.6f\n", question, answer);  
}  
```  
  
  **\-64.64 的立方根等于 \-4.013289**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [exp、expf](../../c-runtime-library/reference/exp-expf.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)