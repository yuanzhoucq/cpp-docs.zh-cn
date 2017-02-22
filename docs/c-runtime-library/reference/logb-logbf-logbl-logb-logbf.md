---
title: "logb、logbf、logbl、_logb、_logbf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "logb"
  - "_logb"
  - "_logbl"
  - "logbf"
  - "logbl"
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
  - "logb"
  - "logbl"
  - "_logb"
  - "_logbf"
  - "logbf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_logb 函数"
  - "_logbf 函数"
  - "指数, 浮点数字"
  - "指数和尾数"
  - "浮点函数"
  - "浮点函数, 尾数和指数"
  - "logb 函数"
  - "logbf 函数"
  - "logbl 函数"
  - "尾数, 浮点值变量"
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# logb、logbf、logbl、_logb、_logbf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提取浮点参数的指数值。  
  
## 语法  
  
```  
double logb(  
   double x   
);  
float logb(  
   float x   
); // C++ only  
long double logb(  
   long double x   
); // C++ only   
float logbf(  
   float x   
);  
long double logbl(  
   long double x   
);  
double _logb(  
   double x   
);  
float _logbf(  
   float x   
);  
```  
  
#### 参数  
 x  
 一个浮点值。  
  
## 返回值  
 `logb` 返回作为表示浮点值的有符号整数`x` 的无偏指数值。  
  
## 备注  
 `logb` 函数提取浮点参数 `x`的指数值，就像 `x` 来表示无限范围。  如果自变量 `x` 被规格化，则将其视为规范化。  
  
 由于 C\+\+ 允许重载，因此您可以调用 `logb` 的重载，该重载采用和返回 `float` 或 `long double` 值。  在 C 程序中，`logb` 始终采用并返回 `double`。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± QNAN,IND|无|\_DOMAIN|  
|± 0|ZERODIVIDE|\_SING|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_logb`|\<float.h\>|  
|`logb`, `logbf`, `logbl`, `_logbf`|\<math.h\>|  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)