---
title: "fegetenv | Microsoft Docs"
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
  - "fetegenv"
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
  - "fegetenv"
  - "fenv/fegetenv"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fetegenv 函数"
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fegetenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将当前的浮点环境存储在指定的对象。  
  
## 语法  
  
```  
int fegetenv(  
   fenv_t *penv  
);  
  
```  
  
#### 参数  
 `penv`  
 指向 `fenv_t` 对象，以包含当前浮点环境的值。  
  
## 返回值  
 返回 0，如果浮点环境已成功存储在 `penv`。 否则，返回一个非零值。  
  
## 备注  
 `fegetenv` 函数所指向的对象中存储当前的浮点环境 `penv`。 浮点点环境是状态标志和影响浮点计算的控件模式的组。 这包括舍入方向模式和浮点异常的状态标志。 如果 `penv` 不指向有效 `fenv_t` 对象，后续的行为是不确定。  
  
 若要使用此功能，必须关闭无法通过使用阻止的访问的浮点优化 `#pragma fenv_access(on)` 指令在调用前。 有关详细信息，请参阅[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`fegetenv`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetenv](../../c-runtime-library/reference/fesetenv1.md)