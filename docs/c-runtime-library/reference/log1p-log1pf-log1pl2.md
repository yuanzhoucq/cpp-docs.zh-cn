---
title: "log1p，log1pf log1pl2 | Microsoft Docs"
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
  - "log1p"
  - "log1pf"
  - "log1pl"
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
  - "log1p"
  - "log1pf"
  - "log1pl"
  - "math/log1p"
  - "math/log1pf"
  - "math/log1pl"
helpviewer_keywords: 
  - "log1p 函数"
  - "log1pf 函数"
  - "log1pl 函数"
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# log1p，log1pf log1pl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算 1 加上指定的值的自然对数。  
  
## 语法  
  
```  
double log1p(  
   double x  
);  
  
float log1p(  
   float x  
); //C++ only  
  
long double log1p(  
   long double x  
); //C++ only  
  
float log1pf(  
   float x  
);  
  
long double log1pl(  
   long double x  
);  
  
```  
  
#### 参数  
 `x`  
 浮点参数。  
  
## 返回值  
 如果成功，返回的自然 \(以 e 为底\) 日志 \(`x`\+ 1\)。  
  
 否则，可能会返回以下值之一︰  
  
|输入|结果|SEH 异常|errno|  
|--------|--------|------------|-----------|  
|inf \+|inf \+|||  
|非规格化数|与输入相同|下溢||  
|±0|与输入相同|||  
|\-1|\-inf|DIVBYZERO|ERANGE|  
|\< \-1|nan|无效|EDOM|  
|\-inf|nan|无效|EDOM|  
|±SNaN|与输入相同|无效||  
|±QNaN，无限期|与输入相同|||  
  
 `errno` 如果值设置为 ERANGE `x` \=\-1。`errno` 如果值设置为 EDOM `x` \< − 1。  
  
## 备注  
 `log1p` 函数可能会比使用日志更精确 \(`x`\+ 1\) x 何时接近于 0。  
  
 由于 c \+ \+ 允许重载，你可以调用的重载 `log1p` 采用并返回浮点型和长双精度类型。 在 C 程序中， `log1p` 始终采用并返回一个双精度值。  
  
 如果 `x` 是自然数，此函数将返回的阶乘的对数 \(`x`\-1\)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`log1p`, `log1pf`,  `log1pl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log2，log2f log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)