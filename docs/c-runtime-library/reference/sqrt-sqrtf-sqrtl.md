---
title: "sqrt、sqrtf、sqrtl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "sqrtl"
  - "sqrtf"
  - "sqrt"
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
  - "sqrt"
  - "sqrtf"
  - "_sqrtl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_sqrtl 函数"
  - "计算平方根"
  - "sqrt 函数"
  - "sqrtf 函数"
  - "sqrtl 函数"
  - "平方根, 计算"
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# sqrt、sqrtf、sqrtl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算平方根。  
  
## 语法  
  
```  
double sqrt(    double x  ); float sqrt(    float x  );  // C++ only long double sqrt(    long double x );  // C++ only float sqrtf(    float x  ); long double sqrtl(    long double x  );  
```  
  
#### 参数  
 `x`  
 非负浮点值  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用 `float` 或 `long double` 类型的 `sqrt` 重载。  在 C 程序中，`sqrt` 始终采用并返回 `double`。  
  
## 返回值  
 `sqrt` 函数返回 `x` 的平方根。  默认情况下，如果 `x` 为负，则 `sqrt` 将返回不定的 NaN。  
  
|输入|SEH 异常|`_matherr` 异常|  
|--------|------------|-------------------|  
|± QNAN,IND|无|\_DOMAIN|  
|\- ∞|无|\_DOMAIN|  
|x\<0|无|\_DOMAIN|  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`sqrt`, `sqrtf`, `sqrtl`|\<math.h\>|\<cmath\>|  
  
 有关兼容性信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_sqrt.c  
// This program calculates a square root.  
  
#include <math.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   double question = 45.35, answer;  
   answer = sqrt( question );  
   if( question < 0 )  
      printf( "Error: sqrt returns %f\n", answer );  
   else  
      printf( "The square root of %.2f is %.2f\n", question, answer );  
}  
```  
  
  **45.35 的平方根等于 6.73**   
## .NET Framework 等效项  
 [System::Math::Sqrt](https://msdn.microsoft.com/en-us/library/system.math.sqrt.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [exp、expf](../../c-runtime-library/reference/exp-expf.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)   
 [\_CIsqrt](../../c-runtime-library/cisqrt.md)