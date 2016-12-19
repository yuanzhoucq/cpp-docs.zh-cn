---
title: "log2，log2f log2l | Microsoft Docs"
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
  - "log2"
  - "log2l"
  - "log2f"
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
dev_langs: 
  - "C"
  - "C++"
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# log2，log2f log2l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定指定的值的二进制 \(2 为底\) 对数。  
  
## 语法  
  
```  
double log2(  
   double x  
);  
  
float log2(  
   float x  
); //C++ only  
  
long double log2(  
   long double x  
); //C++ only  
  
float log2f(  
   float x  
);  
  
long double log2l(  
   long double x  
);  
  
```  
  
#### 参数  
 \[in\] `x`  
 要确定 2 为底的对数的值。  
  
## 返回值  
 如果成功，返回值返回 log2 `x`。  
  
 否则，可能会返回以下值之一︰  
  
|问题|返回|  
|--------|--------|  
|`x` \< 0|NaN|  
|`x` \= ±0|无穷大|  
|`x` \= 1|\+0|  
|\+ INFINITY|\+ INFINITY|  
|NaN|NaN|  
|域错误|NaN|  
|极点错误|\-HUGE\_VAL、 HUGE\_VALF，或\-HUGE\_VALL|  
  
 错误报告中指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 备注  
 如果 x 是一个整数，该函数实质上是返回的最重要的 1 位的从零开始的索引 `x`。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`log2`, `log2f`,  `log2l`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [exp2、 exp2f、 exp2l](../../c-runtime-library/reference/exp2-exp2f-exp2l.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)