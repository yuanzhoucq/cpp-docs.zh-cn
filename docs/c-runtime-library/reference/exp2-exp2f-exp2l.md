---
title: "exp2、 exp2f、 exp2l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "exp2"
  - "exp2f"
  - "exp2l"
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
  - "exp2"
  - "math/exp2"
  - "exp2f"
  - "math/exp2f"
  - "exp2l"
  - "math/exp2l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exp2 函数"
  - "exp2f 函数"
  - "exp2l 函数"
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# exp2、 exp2f、 exp2l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算 2 提升到指定的值 \(即，2ˣ\)。  
  
## 语法  
  
```  
double exp2(  
   double x  
);  
  
float exp2(  
   float x  
);  // C++ only  
  
long double exp2(  
   long double x  
); // C++ only  
  
float exp2f(  
   float x  
);  
  
long double exp2l(  
   long double x  
);  
  
```  
  
#### 参数  
 \[in\] `x`  
 指数的值。  
  
## 返回值  
 如果成功，返回 2 为底的指数 `x` \(2ˣ\)。 否则，可能会返回以下值之一︰  
  
|问题|返回|  
|--------|--------|  
|`x` \= ±0|1|  
|`x` \=\-无穷大|\+0|  
|`x` \= \+ INFINITY|\+ INFINITY|  
|`x` \= NaN|NaN|  
|溢出范围错误|\+ HUGE\_VAL、 \+ HUGE\_VALF，或 \+ HUGE\_VALL|  
|下溢范围错误|正确的结果，舍入后|  
  
 错误报告中指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `exp2` 采用并返回浮点型和长双精度类型。 在 C 程序中， `exp2` 始终采用并返回一个双精度值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`exp`, `expf`, `expl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [exp、expf](../../c-runtime-library/reference/exp-expf.md)   
 [log2，log2f log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)