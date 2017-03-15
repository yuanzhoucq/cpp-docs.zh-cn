---
title: "fetestexcept1 | Microsoft Docs"
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
  - "fetestexcept"
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
  - "fetestexcept"
  - "fenv/fetestexcept"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fetestexept 函数"
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# fetestexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定指定的浮点异常状态标志的当前设置。  
  
## 语法  
  
```  
int fetestexcept(  
   int excepts  
);  
  
```  
  
#### 参数  
 `excepts`  
 按位或浮点状态标志的测试。  
  
## 返回值  
 如果成功，返回一个包含位或运算的浮点异常宏的当前对应的异常状态标志的位掩码设置。 设置返回 0，如果没有引发的异常。  
  
## 备注  
 使用 fetestexcept 函数来确定哪些异常由浮点运算。 使用 `excepts` 参数来指定要测试的异常状态标志。`fetestexcept` 函数使用在 \< v.h \> 中定义这些异常宏 `excepts` 和返回值︰  
  
|异常宏|描述|  
|---------|--------|  
|FE\_DIVBYZERO|前面浮点操作; 特性或顾客时出错已创建无穷大值。|  
|FE\_INEXACT|该函数的分布式要舍入存储之前的浮点运算的结果。|  
|FE\_INVALID|在前面的浮点操作中发生域错误。|  
|FE\_OVERFLOW|范围出错;早期的浮点运算结果已太大而无法表示。|  
|FE\_UNDERFLOW|早期的浮点运算结果已太小而无法表示完整的精度; 在denormal 值的创建。|  
|FE\_ALLEXCEPT|所有的按位或支持浮点异常。|  
  
 指定 `excepts` 参数可能为 0，一个受支持的浮点异常宏，或按位或两个或多个宏。 任何其他的效果 `excepts` 参数值是不确定。  
  
 若要使用此功能，必须关闭无法通过使用阻止的访问的浮点优化 `#pragma fenv_access(on)` 指令在调用前。 有关更多信息，请参见[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`fetestexcept`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feraiseexcept](../../c-runtime-library/reference/feraiseexcept.md)