---
title: "ldiv、lldiv | Microsoft Docs"
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
  - "ldiv"
  - "lldiv"
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
  - "ldiv"
  - "lldiv"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "计算商"
  - "计算余数"
  - "ldiv 函数"
  - "lldiv 函数"
  - "商, 计算"
  - "余数计算"
ms.assetid: 68ab5d83-27a4-479c-9d52-d055eb139eca
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ldiv、lldiv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算两个整数商和余数作为一个操作。  
  
## 语法  
  
```  
ldiv_t ldiv(  
   long numer,  
   long denom   
);  
lldiv_t lldiv(  
   long long numer,  
   long long denom   
);  
```  
  
#### 参数  
 `numer`  
 枚举器。  
  
 `denom`  
 分母。  
  
## 返回值  
 `ldiv` 返回一个包括商和余数类型的 [ldiv\_t](../../c-runtime-library/standard-types.md) 结构。  `lldiv` 返回一个包括商和余数类型的 [ldiv\_t](../../c-runtime-library/standard-types.md) 结构。  
  
## 备注  
 `ldiv`和 `lldiv` 函数将 `numer`除以`denom` 从而计算商和余数。  该商的符号与数学商的符号相同。  商的绝对值是最大的整数，这个整数小于数学商的绝对值。  如果分母为 0，则程序终止并会出现一条错误消息。  `ldiv` 的参数和返回的结构成员都是`long`类型 ，并且，`lldiv` 的参数和返回的结构成员是 `long long`类型。除此之外，`ldiv` 和 `lldiv` 与`div`相同。  
  
 `ldiv_t` 和 `lldiv_t` 结构在 \<stdlib.h\>中被定义。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`ldiv`, `lldiv`|\<stdlib.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_ldiv.c  
  
#include <stdlib.h>  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   long x = 5149627, y = 234879;  
   ldiv_t div_result;  
  
   div_result = ldiv( x, y );  
   printf( "For %ld / %ld, the quotient is ", x, y );  
   printf( "%ld, and the remainder is %ld\n",   
            div_result.quot, div_result.rem );  
}  
```  
  
## Output  
  
```  
For 5149627 / 234879, the quotient is 21, and the remainder is 217168  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)