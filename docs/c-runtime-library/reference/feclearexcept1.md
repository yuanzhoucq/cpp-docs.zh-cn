---
title: "feclearexcept1 | Microsoft Docs"
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
  - "feclearexcept"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "feclearexcept"
  - "fenv/feclearexcept"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "feclearexcept 函数"
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# feclearexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尝试清除参数所指定的浮点异常标记。  
  
## 语法  
  
```  
int feclearexcept(  
   int excepts  
);  
```  
  
#### 参数  
 `excepts`  
 要清除的异常状态标志。  
  
## 返回值  
 返回为零 `excepts` 为零，或者如果已成功清除所有指定的异常。 否则，返回一个非零值。  
  
## 备注  
 `feclearexcept` 函数将尝试清除浮点点由指定的异常状态标志 `excepts`。 该函数支持在 v.h 中定义这些异常宏︰  
  
|异常宏|描述|  
|---------|--------|  
|FE\_DIVBYZERO|前面浮点操作; 特性或顾客时出错已创建无穷大值。|  
|FE\_INEXACT|该函数的分布式要舍入存储之前的浮点运算的结果。|  
|FE\_INVALID|在前面的浮点操作中发生域错误。|  
|FE\_OVERFLOW|范围出错;早期的浮点运算结果已太大而无法表示。|  
|FE\_UNDERFLOW|早期的浮点运算结果已太小而无法表示完整的精度; 在denormal 值的创建。|  
|FE\_ALLEXCEPT|所有的按位或支持浮点异常。|  
  
 `excepts` 参数可能为零或一个或多个支持的异常宏的按位 OR。 任何其他参数值的结果为 undefined。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`feclearexcept`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)