---
title: "_cabs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cabs"
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
  - "cabsl"
  - "_cabs"
  - "_cabsl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cabs 函数"
  - "_cabsl 函数"
  - "绝对值"
  - "cabs 函数"
  - "cabsl 函数"
  - "计算绝对值"
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _cabs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算复数的绝对值。  
  
## 语法  
  
```  
double _cabs(   
   struct _complex z   
);  
```  
  
#### 参数  
 `z`  
 复数。  
  
## 返回值  
 如果成功，`_cabs` 返回绝对值参数。  溢出，`_cabs` 返回 `HUGE_VAL` 并将 `errno` 设置为 `ERANGE`。  您可以更改与 [\_matherr](../../c-runtime-library/reference/matherr.md)中的错误处理。  
  
## 备注  
 `_cabs` 函数计算复数的绝对值，必须为类型[\_complex](../../c-runtime-library/standard-types.md)结构。  结构 `z` 由实际组件 `x` 和假设组件的 `y`组成。  对 `_cabs` 的调用将产生表达式的等效值 `sqrt`\( `z.x``*``z.x` `+` `z.y`\*`z.y` \)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_cabs`|\<math.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_cabs.c  
/* Using _cabs, this program calculates  
 * the absolute value of a complex number.  
 */  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct _complex number = { 3.0, 4.0 };  
   double d;  
  
   d = _cabs( number );  
   printf( "The absolute value of %f + %fi is %f\n",  
           number.x, number.y, d );  
}  
```  
  
  **The absolute value of 3.000000 \+ 4.000000i is 5.000000**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [abs、 labs、 llabs、 \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [fabs、 fabsf fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [labs、llabs](../../misc/labs-llabs.md)