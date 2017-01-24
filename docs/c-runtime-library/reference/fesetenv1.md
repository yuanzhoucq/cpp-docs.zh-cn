---
title: "fesetenv | Microsoft Docs"
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
  - "fesetenv"
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
  - "fesetenv"
  - "fenv/fesetenv"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fesetenv 函数"
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fesetenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置当前的浮点环境。  
  
## 语法  
  
```  
int fesetenv(  
   const fenv_t *penv  
);  
  
```  
  
#### 参数  
 `penv`  
 指向 `fenv_t` 对象，其中包含浮点环境作为集通过调用 [fegetenv](../Topic/fegetenv2.md) 或 [feholdexcept](../Topic/feholdexcept1.md)。 此外可以通过使用 FE\_DFL\_ENV 宏指定默认启动浮点环境。  
  
## 返回值  
 如果环境已成功设置，则返回 0。 否则，返回一个非零值。  
  
## 备注  
 `fesetenv` 函数将设置从存储中的值的当前浮点环境 `fenv_t` 指向对象 `penv`。 浮点点环境是状态标志和影响浮点计算的控件模式的组。 这包括舍入模式和浮点异常的状态标志。 如果 `penv` 不是 FE\_DFL\_ENV 或不指向有效 `fenv_t` 对象，后续的行为是不确定。  
  
 对此函数调用设置的异常中的状态标志 `penv` 对象，但它不会引发这些异常。  
  
 若要使用此功能，必须关闭无法通过使用阻止的访问的浮点优化 `#pragma fenv_access(on)` 指令在调用前。 有关详细信息，请参阅[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`fesetenv`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)