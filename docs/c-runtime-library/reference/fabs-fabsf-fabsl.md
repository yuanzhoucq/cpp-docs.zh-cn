---
title: "fabs、 fabsf fabsl | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fabsf"
  - "fabs"
  - "fabsl"
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
  - "fabs"
  - "fabsf"
  - "fabsl"
  - "math\fabs"
  - "math\fabsf"
  - "math\fabsl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "绝对值"
  - "fabsf 函数"
  - "计算绝对值"
  - "fabs 函数"
  - "fabsl 函数"
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fabs、 fabsf fabsl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算浮点自变量的绝对值。  
  
## 语法  
  
```  
double fabs(   
   double x   
);  
float fabs(  
   float x   
); // C++ only  
long double fabs(  
   long double x  
); // C++ only  
float fabsf(   
   float x   
);  
long double fabsl(  
   long double x  
);  
```  
  
#### 参数  
 `x`  
 浮点值。  
  
## 返回值  
 `fabs` 函数将返回参数的绝对值 `x`。 无错误返回。  
  
|输入|SEH 异常|Matherr 异常|  
|--------|------------|----------------|  
|± QNAN,IND|无|\_DOMAIN|  
  
## 备注  
 C \+ \+ 允许重载，因此您可以调用的重载 `fabs` 如果包括 \< cmath \> 标头。 在 C 程序中， `fabs` 始终采用并返回一个双精度值。  
  
## 要求  
  
|函数|必需的 C 标头|必需的 c \+ \+ 标头|  
|--------|--------------|--------------------|  
|`fabs`, `fabsf`, `fabsl`|\<math.h\>|\< cmath \> 或 \< h.h \>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参阅示例 [abs](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [abs、 labs、 llabs、 \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [labs、llabs](../../misc/labs-llabs.md)