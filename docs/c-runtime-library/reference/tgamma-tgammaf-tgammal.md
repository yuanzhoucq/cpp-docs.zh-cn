---
title: "tgamma、 tgammaf、 tgammal | Microsoft Docs"
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
  - "tgamma"
  - "tgammaf"
  - "tgammal"
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
  - "tgamma"
  - "tgammaf"
  - "tgammal"
  - "math/tgamma"
  - "math/tgammaf"
  - "math/tgammal"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "tgamma 函数"
  - "tgammaf 函数"
  - "tgammal 函数"
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tgamma、 tgammaf、 tgammal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定指定的值的伽玛函数。  
  
## 语法  
  
```  
double tgamma(  
   double x  
);  
  
float tgamma(  
   float x  
); //C++ only  
  
long double tgamma(  
   long double x  
); //C++ only  
  
float tgammaf(  
   float x  
);  
  
long double tgammal(  
   long double x  
);  
  
```  
  
#### 参数  
 \[in\] `x`  
 若要查找的伽玛值。  
  
## 返回值  
 如果成功，返回的伽玛 `x`。  
  
 如果可能发生范围错误的严重性 `x` 太大或太小，数据类型。 如果，可能会发生域错误或范围错误 `x` \< \= 0。  
  
|问题|返回|  
|--------|--------|  
|x \= ±0|±INFINITY|  
|x \= 负整数|NaN|  
|x \=\-无穷大|NaN|  
|x \= \+ INFINITY|\+ INFINITY|  
|x \= NaN|NaN|  
|域错误|NaN|  
|极点错误|±HUGE\_VAL、 ±HUGE\_VALF 或 ±HUGE\_VALL|  
|溢出范围错误|±HUGE\_VAL、 ±HUGE\_VALF 或 ±HUGE\_VALL|  
|下溢范围错误|舍入后的正确值。|  
  
 错误报告中指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 备注  
 由于 c \+ \+ 允许重载，您可以调用采用并返回浮点型和长双精度类型的重载的 tgamma。 在 C 程序中，tgamma 始终采用并返回一个双精度值。  
  
 如果 x 为自然数，此函数将返回 \(x\-1\) 的阶乘。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`tgamma`, `tgammaf`,  `tgammal`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [lgamma、 lgammaf、 lgammal](../../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)