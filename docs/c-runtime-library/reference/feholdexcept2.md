---
title: "feholdexcept | Microsoft Docs"
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
  - "feholdexcept"
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
  - "feholdexcept"
  - "fenv/feholdexcept"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "feholdexcept 函数"
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# feholdexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将当前的浮点环境保存在指定的对象、 清除浮点状态标志，以及如果可能，请将放到不间断模式浮点环境。  
  
## 语法  
  
```  
int feholdexcept(  
   fenv_t *penv  
);  
  
```  
  
#### 参数  
 `penv`  
 指向 `fenv_t` 对象，以包含浮点环境的副本。  
  
## 返回值  
 当且仅当的功能是能够成功启用不间断的浮点异常处理，则返回零。  
  
## 备注  
 `feholdexcept` 函数用于存储当前浮动点环境的状态 `fenv_t` 指向对象 `penv`, ，并设置环境以不会中断执行浮点异常。 这被称为无中断模式。  此模式将继续，直到将环境恢复使用 [fesetenv](../Topic/fesetenv2.md) 或 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)。  
  
 在需要隐藏从调用方的一个或多个浮点异常的子例程的开头，可以使用此函数。 若要报告异常，您可以只需清除不需要的异常使用 [feclearexcept，](../../c-runtime-library/reference/feclearexcept1.md) ，然后结束通过调用的不间断模式 `feupdateenv`。  
  
 若要使用此功能，必须关闭无法通过使用阻止的访问的浮点优化 `#pragma fenv_access(on)` 指令在调用前。 有关详细信息，请参阅[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`feholdexcept`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [fesetenv](../Topic/fesetenv2.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)