---
title: "lgamma、 lgammaf、 lgammal | Microsoft Docs"
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
  - "lgamma"
  - "lgammaf"
  - "lgammal"
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
  - "lgamma"
  - "lgammaf"
  - "lgammal"
  - "math/lgamma"
  - "math/lgammaf"
  - "math/lgammal"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "lgamma 函数"
  - "lgammal 函数"
  - "lgammaf 函数"
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# lgamma、 lgammaf、 lgammal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定指定的值的伽玛函数的绝对值的自然对数。  
  
## 语法  
  
```  
double lgamma(  
   double x  
);  
  
float lgamma(  
   float x  
); //C++ only  
  
long double lgamma(  
   long double x  
); //C++ only  
  
float lgammaf(  
   float x  
);  
  
long double lgammal(  
   long double x  
);  
  
```  
  
#### 参数  
 \[in\] `x`  
 要计算的值。  
  
## 返回值  
 如果成功，返回的伽玛函数的绝对值的自然对数 `x.`  
  
|问题|返回|  
|--------|--------|  
|`x` \= NaN|NaN|  
|`x` \= ±0|\+ INFINITY|  
|`x`\= 负整数|\+ INFINITY|  
|±INFINITY|\+ INFINITY|  
|极点错误|\+ HUGE\_VAL、 \+ HUGE\_VALF，或 \+ HUGE\_VALL|  
|溢出范围错误|±HUGE\_VAL、 ±HUGE\_VALF 或 ±HUGE\_VALL|  
  
 错误报告中指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `lgamma` 采用并返回浮点型和长双精度类型。 在 C 程序中， `lgamma` 始终采用并返回一个双精度值。  
  
 如果 x 是有理数，此函数返回的阶乘的对数 \(`x`\-1\)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`lgamma`, `lgammaf`,  `lgammal`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [tgamma、 tgammaf、 tgammal](../../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)