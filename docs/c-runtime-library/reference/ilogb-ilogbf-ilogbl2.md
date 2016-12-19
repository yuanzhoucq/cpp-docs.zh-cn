---
title: "ilogb、 ilogbf、 ilogbl | Microsoft Docs"
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
  - "ilogb"
  - "ilogbf"
  - "ilogbl"
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
  - "ilogb"
  - "ilogbf"
  - "ilogbl"
  - "math/ilogb"
  - "math/ilogbf"
  - "math/ilogbl"
helpviewer_keywords: 
  - "ilogb 函数"
  - "ilogbf 函数"
  - "ilogbl 函数"
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ilogb、 ilogbf、 ilogbl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索一个整数，表示指定的值的无偏差的 2 为底指数。  
  
## 语法  
  
```  
int ilogb(  
   double x  
);  
  
int ilogb(  
   float x  
); //C++ only  
  
int ilogb(  
   long double x  
); //C++ only  
  
int ilogbf(  
   float x  
);  
  
int ilogbl(  
   long double x  
);  
  
```  
  
#### 参数  
 \[in\] `x`  
 指定的值。  
  
## 返回值  
 如果成功，返回 2 为底的指数 `x` 作为一个已签名 `int` 值。  
  
 否则，返回 \< h.h \> 中定义的以下值之一︰  
  
|输入|结果|  
|--------|--------|  
|±0|FP\_ILOGB0|  
|±inf，±nan，无限期|FP\_ILOGBNAN|  
  
 错误报告中指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `ilogb` 采用并返回浮点型和长双精度类型。 在 C 程序中， `ilogb` 始终采用并返回一个双精度值。  
  
 调用此函数相当于调用的等效方法 `logb` 函数，则将返回值转换为 `int`。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`ilogb`, `ilogbf`,  `ilogbl`|\<math.h\>|\<cmath\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [logb、logbf、logbl、\_logb、\_logbf](../../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)