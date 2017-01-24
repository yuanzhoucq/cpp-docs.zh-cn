---
title: "fmin、 fminf、 fminl | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fmin"
  - "fminf"
  - "fminl"
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
  - "fmin"
  - "fminf"
  - "fminl"
  - "math/fmin"
  - "math/fminf"
  - "math/fminl"
helpviewer_keywords: 
  - "fmin 函数"
  - "fminf 函数"
  - "fminl 函数"
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fmin、 fminf、 fminl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定两个指定的值的较小者。  
  
## 语法  
  
```  
double fmin(  
   double x,   
   double y  
);  
  
float fmin(  
   float x,   
   float y  
); //C++ only  
  
long double fmin(  
   long double x,   
   long double y  
); //C++ only  
  
float fminf(  
   float x,   
   float y  
);  
  
long double fminl(  
   long double x,   
   long double y  
);  
  
```  
  
#### 参数  
 `x`  
 要比较的第一个值。  
  
 `y`  
 要比较的第二个值。  
  
## 返回值  
 如果成功，返回较小的 `x` 或 `y`。  
  
|输入|结果|  
|--------|--------|  
|`x` 为 NaN|`y`|  
|`y` 为 NaN|`x`|  
|`x` 和 `y` 是 NaN|nan|  
  
 该函数不会导致 [\_matherr](../../c-runtime-library/reference/matherr.md) 要调用会导致任何浮点异常，或更改的值 `errno`。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `fmin` 采用并返回浮点型和长双精度类型。 在 C 程序中， `fmin` 始终采用并返回一个双精度值。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`fmin`, `fminf`,  `fminl`|C: \< h.h \><br /><br /> C \+ \+: \< h.h \> 或 \< cmath \>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)