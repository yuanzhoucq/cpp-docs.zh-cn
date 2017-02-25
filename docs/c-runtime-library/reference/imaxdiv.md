---
title: "imaxdiv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "imaxdiv"
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
  - "imaxdiv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "imaxdiv 函数"
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# imaxdiv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

作为单个运算，计算任意大小的两个整数值的商和余数。  
  
## 语法  
  
```  
imaxdiv_t imaxdiv(   
   intmax_t numer,  
   intmax_t denom   
);   
```  
  
#### 参数  
 `numer`  
 枚举器。  
  
 `denom`  
 分母。  
  
## 返回值  
 `imaxdiv`（使用 [intmax\_t](../../c-runtime-library/standard-types.md) 类型的参数调用）返回由商和余数组成的 [imaxdiv\_t](../../c-runtime-library/standard-types.md) 类型的结构。  
  
## 备注  
 `imaxdiv` 函数将 `numer` 除以 `denom` 从而计算商和余数。  `imaxdiv_t` 结构包含商（`intmax_t` `quot`）和余数（`intmax_t` `rem`）。  该商的符号与数学商的符号相同。  其绝对值是最大的整数，小于数学商的绝对值。  如果分母为 0，则程序终止并会出现一条错误消息。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`imaxdiv`|\<inttypes.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_imaxdiv.c  
// Build using: cl /W3 /Tc crt_imaxdiv.c  
// This example takes two integers as command-line  
// arguments and calls imaxdiv to divide the first   
// argument by the second, then displays the results.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <inttypes.h>  
  
int main(int argc, char *argv[])  
{  
   intmax_t x,y;  
   imaxdiv_t div_result;  
  
   x = atoll(argv[1]);  
   y = atoll(argv[2]);  
  
   printf("The call to imaxdiv(%lld, %lld)\n", x, y);  
   div_result = imaxdiv(x, y);  
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",  
          div_result.quot, div_result.rem);  
}  
```  
  
 如果通过命令行参数 `9460730470000000 8766` 生成然后调用，代码就会生成此输出：  
  
  **调用 imaxdiv\(9460730470000000, 8766\)**  
**结果为商 1079252848505 余 5170**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)