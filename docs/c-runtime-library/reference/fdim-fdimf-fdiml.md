---
title: "fdim、 fdimf、 fdiml | Microsoft Docs"
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
  - "fdim"
  - "fdimf"
  - "fdiml"
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
  - "fdim"
  - "fdimf"
  - "fdiml"
  - "math/fdim"
  - "math/fdimf"
  - "math/fdiml"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fdim 函数"
  - "fdimf 函数"
  - "fdiml 函数"
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# fdim、 fdimf、 fdiml
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定第一个和第二个值之间的正数差异。  
  
## 语法  
  
```  
double fdim(  
   double x,   
   double y  
);  
  
float fdim(  
   float x,   
   float y  
); //C++ only  
  
long double fdim(  
   long double x,   
   long double y  
); //C++ only  
  
float fdimf(  
   float x,   
   float y  
);  
  
long double fdiml(  
   long double x,   
   long double y  
);  
  
```  
  
#### 参数  
 \[in\] `x`  
 第一个值。  
  
 \[in\] `y`  
 第二个值。  
  
## 返回值  
 返回正差额 `x` 和 `y`:  
  
|返回值|方案|  
|---------|--------|  
|x y|如果 x \> y|  
|0|如果 x \< \= y|  
  
 否则，可能会返回以下错误之一︰  
  
|问题|返回|  
|--------|--------|  
|溢出范围错误|\+ HUGE\_VAL、 \+ HUGE\_VALF，或 \+ HUGE\_VALL|  
|下溢范围错误|正确的值 （舍入后）|  
|`x` 或 `y` 为 NaN|NaN|  
  
 错误报告中指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `fdim` 采用并返回浮点型和长双精度类型。 在 C 程序中， `fdim` 始终采用并返回一个双精度值。  
  
 除了 NaN 处理中，此函数相当于 [fmax、 fmaxf、 fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)\(`x`\-`y,` 0\)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`fdim`, `fdimf`,  `fdiml`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmax、 fmaxf、 fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)   
 [abs、 labs、 llabs、 \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)