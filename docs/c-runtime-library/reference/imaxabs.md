---
title: "imaxabs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "imaxabs"
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
  - "imaxabs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "imaxabs 函数"
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# imaxabs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算所有大小整数的绝对值。  
  
## 语法  
  
```  
intmax_t imaxabs(  
   intmax_t n   
);  
```  
  
#### 参数  
 *n*  
 整数值。  
  
## 返回值  
 `imaxabs` 函数返回参数的绝对值。  无错误返回。  
  
> [!NOTE]
>  由于可使用 `intmax_t` 表示的负整数的范围大于可表示的正整数的范围，因此可向 `imaxabs` 提供不能转换的参数。  如果参数的绝对值不能由返回类型表示，则不定义 `imaxabs` 行为。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`imaxabs`|\<inttypes.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_imaxabs.c  
// Build using: cl /W3 /Tc crt_imaxabs.c  
// This example calls imaxabs to compute an  
// absolute value, then displays the results.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <inttypes.h>  
  
int main(int argc, char *argv[])  
{  
   intmax_t x = LLONG_MIN + 2;  
  
   printf("The absolute value of %lld is %lld\n", x, imaxabs(x));  
}  
```  
  
  **\-9223372036854775806 的绝对值是 9223372036854775806**   
## .NET Framework 等效项  
 [System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [abs、 labs、 llabs、 \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [labs、llabs](../../misc/labs-llabs.md)