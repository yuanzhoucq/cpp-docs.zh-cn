---
title: "expm1、expm1f、expm1l | Microsoft Docs"
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
  - "expm1l"
  - "expm1"
  - "expm1f"
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
  - "expm1l"
  - "expm1"
  - "expm1f"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "expm1 函数"
  - "expm1f 函数"
  - "expm1l 函数"
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# expm1、expm1f、expm1l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算一个值以 e 为基数的指数，减去一。  
  
## 语法  
  
```  
double expm1(   
   double x   
);  
float expm1(  
   float x  
);  // C++ only  
long double expm1(  
   long double x  
);  // C++ only  
float expm1f(  
   float x  
);  
long double expm1l(  
   long double x  
);  
```  
  
#### 参数  
 `x`  
 浮点指数值。  
  
## 返回值  
 `expm1` 函数返回表示 e<sup>x</sup> \-1 的浮点值（如果成功）。  在溢出中，`expm1` 返回 `HUGE_VAL`，`expm1f` 返回 `HUGE_VALF`，`expm1l` 返回 `HUGE_VALL`，并且 `errno` 设置为 `ERANGE`。  有关返回代码的详细信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 由于 C\+\+ 允许重载，因此您可以调用 `expm1` 的重载，该重载采用和返回 `float` 和 `long double` 值。  在 C 程序中，`expm1` 始终采用并返回 `double`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`expm1`, `expm1f`, `expm1l`|\<math.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅 [平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [exp2、exp2f、exp2l](http://msdn.microsoft.com/zh-cn/a7974629-be1e-4196-a562-6624a0732003)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)