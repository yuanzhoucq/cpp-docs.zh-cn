---
title: "feupdateenv | Microsoft Docs"
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
  - "feupdateenv"
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
  - "feupdateenv"
  - "fenv/feupdateenv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "feupdateenv 函数"
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# feupdateenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

保存当前引发浮点异常、 还原指定的浮点环境状态，并会引发已保存的浮点异常。  
  
## 语法  
  
```  
int feupdateenv(  
   const fenv_t* penv  
);  
```  
  
#### 参数  
 `penv`  
 指向 `fenv_t` 对象，其中包含浮点环境作为集通过调用 [fegetenv](../Topic/fegetenv2.md) 或 [feholdexcept](../Topic/feholdexcept1.md)。 此外可以通过使用 FE\_DFL\_ENV 宏指定默认启动浮点环境。  
  
## 返回值  
 如果所有的操作已成功完成，则返回 0。 否则，返回一个非零值。  
  
## 备注  
 `feupdateenv` 函数执行了多个操作。 首先，它将自动存储在存储当前的浮点异常状态标志。 然后，它设置中存储的值从当前的浮点环境 `fenv_t` 指向对象 `penv`。 如果 `penv` 不是 FE\_DFL\_ENV 或不指向有效 `fenv_t` 对象，后续的行为是不确定。 最后， `feupdateenv` 引发本地存储的浮点异常。  
  
 若要使用此功能，必须关闭无法通过使用阻止的访问的浮点优化 `#pragma fenv_access(on)` 指令在调用前。 有关详细信息，请参阅[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`feupdateenv`|\<fenv.h\>|\<cfenv\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)