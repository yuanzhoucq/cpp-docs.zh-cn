---
title: "fesetexceptflag | Microsoft Docs"
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
  - "fesetexceptflag"
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
  - "fesetexceptflag"
  - "fenv/fesetexceptflag"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fesetexceptflag 函数"
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fesetexceptflag
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当前的浮点环境中设置指定的浮点状态标志。  
  
## 语法  
  
```  
int fesetexceptflag(  
     const fexcept_t *pstatus,  
     int excepts  
);  
  
```  
  
#### 参数  
 `pstatus`  
 指向  `fexcept_t` 对象，其中包含要设置为异常状态标志的值。 该对象可以设置到的以前调用 [fegetexceptflag](../Topic/fegetexceptflag1.md)。  
  
 `excepts`  
 要设置的浮点异常状态标志。  
  
## 返回值  
 如果所有指定的异常状态标志设置成功，返回 0。 否则，返回一个非零值。  
  
## 备注  
 `fesetexceptflag` 函数设置由指定的浮点异常状态标志的状态 `excepts` 设置的相应值 `fexcept_t` 指向对象 `pstatus`。  它不会引发异常。`pstatus` 指针必须指向有效 `fexcept_t` 对象或后续的行为是不确定。`fesetexceptflag` 函数支持这些异常宏的值在 `excepts`, 在 \< v.h \> 中定义︰  
  
|异常宏|描述|  
|---------|--------|  
|FE\_DIVBYZERO|前面浮点操作; 特性或顾客时出错已创建无穷大值。|  
|FE\_INEXACT|该函数的分布式要舍入存储之前的浮点运算的结果。|  
|FE\_INVALID|在前面的浮点操作中发生域错误。|  
|FE\_OVERFLOW|范围出错;早期的浮点运算结果已太大而无法表示。|  
|FE\_UNDERFLOW|早期的浮点运算结果已太小而无法表示完整的精度; 在denormal 值的创建。|  
|FE\_ALLEXCEPT|所有的按位或支持浮点异常。|  
  
 `excepts` 参数可能为零，一个受支持的浮点异常宏，或按位或两个或多个宏。 未定义任何其他参数值的效果。  
  
 若要使用此功能，必须关闭无法通过使用阻止的访问的浮点优化 `#pragma fenv_access(on)` 指令在调用前。 有关详细信息，请参阅[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`fesetexceptflag`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetexceptflag](../../c-runtime-library/reference/fegetexceptflag2.md)