---
title: "feraiseexcept | Microsoft Docs"
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
  - "feraiseexcept"
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
apitype: "HeaderDef"
f1_keywords: 
  - "feraiseexcept"
  - "fenv/feraiseexcept"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "feraiseexcept 函数"
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# feraiseexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

引发指定的浮点异常。  
  
## 语法  
  
```  
int feraiseexcept(  
   int excepts  
);  
```  
  
#### 参数  
 `excepts`  
 若要引发浮点异常。  
  
## 返回值  
 如果指定的所有异常都提升成功，返回 0。  
  
## 备注  
 `feraiseexcept` 函数尝试引发由指定的浮点异常 `excepts`。`feraiseexcept` 函数支持在 \< v.h \> 中定义这些异常宏︰  
  
|异常宏|描述|  
|---------|--------|  
|FE\_DIVBYZERO|前面浮点操作; 特性或顾客时出错已创建无穷大值。|  
|FE\_INEXACT|该函数的分布式要舍入存储之前的浮点运算的结果。|  
|FE\_INVALID|在前面的浮点操作中发生域错误。|  
|FE\_OVERFLOW|范围出错;早期的浮点运算结果已太大而无法表示。|  
|FE\_UNDERFLOW|早期的浮点运算结果已太小而无法表示完整的精度; 在denormal 值的创建。|  
|FE\_ALLEXCEPT|所有的按位或支持浮点异常。|  
  
 `excepts` 参数可能为零，一个异常宏的值，或按位或两个或多个支持的异常宏。 如果指定的异常宏之一是 FE\_OVERFLOW 或 FE\_UNDERFLOW，FE\_INEXACT 异常可能会引发的副作用。  
  
 若要使用此功能，必须关闭无法通过使用阻止的访问的浮点优化 `#pragma fenv_access(on)` 指令在调用前。 有关更多信息，请参见[fenv\_access](../../preprocessor/fenv-access.md)。  
  
 **Microsoft 专用︰** 中指定的异常 `excepts` 按顺序 FE\_INVALID，引发 FE\_DIVBYZERO、 FE\_OVERFLOW、 FE\_UNDERFLOW、 FE\_INEXACT。 但是，FE\_INEXACT 可以引发 FE\_OVERFLOW 或 FE\_UNDERFLOW 引发时，即使在未指定 `excepts`。**结束 Microsoft 专用**  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`feraiseexcept`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)