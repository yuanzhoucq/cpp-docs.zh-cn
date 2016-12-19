---
title: "fegetexceptflag | Microsoft Docs"
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
  - "fegetexceptflag"
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
  - "fegetexceptflag"
  - "fenv/fegetexceptflag"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fegetexceptflag 函数"
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fegetexceptflag
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存储指定的浮点异常标志的当前状态。  
  
## 语法  
  
```  
int fegetexceptflag(   
   fexcept_t* pstatus,   
   int excepts   
);  
  
```  
  
#### 参数  
 `pstatus`  
 一个指向 `fexcept_t` 对象，以包含所指定的异常标记的当前值 `excepts`。  
  
 `excepts`  
 要在中存储的浮点异常标志 `pstatus`。  
  
## 返回值  
 如果成功，则返回 0。 否则，返回一个非零值。  
  
## 备注  
 `fegetexceptflag` 函数将存储由指定的浮点异常状态标志的当前状态 `excepts` 中 `fexcept_t` 指向对象 `pstatus`。`pstatus` 必须指向有效 `fexcept_t` 对象或后续的行为是不确定。`fegetexceptflag` 函数支持在 \< v.h \> 中定义这些异常宏︰  
  
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
|`fegetexceptflag`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)