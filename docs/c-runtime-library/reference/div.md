---
title: "div | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "div"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "div"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "div 函数"
  - "整数除操作"
  - "商"
  - "商, 计算"
  - "余数计算"
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# div
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算两个整数的商和余数。  
  
## 语法  
  
```  
div_t div(   
   int numer,  
   int denom   
);  
ldiv_t div(  
   long numer,  
   long denom  
); /* C++ only */   
lldiv_t div(  
   long long numer,  
   long long denom  
); /* C++ only */  
```  
  
#### 参数  
 `numer`  
 枚举器。  
  
 `denom`  
 分母。  
  
## 返回值  
 `div` 由使用`int` 类型的参数调用，返回 `div_t`类型的结构，它包含商和余数。  `long`类型参数的超加载返回值是 `ldiv_t`。  `div_t` 和 `ldiv_t` 在 STDLIB.H. 定义。  
  
## 备注  
 `div` 函数将 `numer` 除以 `denom` 从而计算商和余数。   [div\_t](../../c-runtime-library/standard-types.md) 结构包含商，`int` `quot`和余数，`int` `rem`。  该商的符号与数学商的符号相同。  其绝对值是最大的整数，小于数学商的绝对值。  如果分母为 0，则程序终止并会出现一条错误消息。  
  
 采用`long` 或 `long long` 类型参数的超加载只有在 C\+\+ 代码中才可用。  返回 [ldiv\_t](../../c-runtime-library/standard-types.md) 类型包含成员 `long` `quot` 和 `long`，`rem`，并返回 [lldiv\_t](../../c-runtime-library/standard-types.md) 类型包含成员 `long long quot` 和 `long long rem`，它们与 `div_t`成员具有相同的含义。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`div`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_div.c  
// arguments: 876 13  
  
// This example takes two integers as command-line  
// arguments and displays the results of the integer  
// division. This program accepts two arguments on the  
// command line following the program name, then calls  
// div to divide the first argument by the second.  
// Finally, it prints the structure members quot and rem.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <math.h>  
  
int main( int argc, char *argv[] )  
{  
   int x,y;  
   div_t div_result;  
  
   x = atoi( argv[1] );  
   y = atoi( argv[2] );  
  
   printf( "x is %d, y is %d\n", x, y );  
   div_result = div( x, y );  
   printf( "The quotient is %d, and the remainder is %d\n",  
           div_result.quot, div_result.rem );  
}  
```  
  
  **x 是 876，y 是 13**  
**商是 67，余数为 5**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)