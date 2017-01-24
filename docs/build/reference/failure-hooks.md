---
title: "失败挂钩 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL 的延迟加载, 失败挂钩"
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 失败挂钩
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

失败挂钩和[通知挂钩](../../build/reference/notification-hooks.md)的启用方式相同。  挂钩例程需返回一个合适的值，以便处理能继续进行（HINSTANCE 或 FARPROC），或返回 0 指示将引发异常。  
  
 引用用户定义函数的指针变量为：  
  
```  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 **DelayLoadInfo** 结构包含准确报告错误所需的所有相关数据，包括来自 `GetLastError` 的值。  
  
 如果通知是 **dliFailLoadLib**，挂钩函数可以返回：  
  
-   0，如果它不能处理失败。  
  
-   HMODULE，如果失败挂钩修复了问题并且自己加载了库。  
  
 如果通知是 **dliFailGetProc**，挂钩函数可以返回：  
  
-   0，如果它不能处理失败。  
  
-   一个有效的进程地址（导入函数地址），如果失败挂钩自已成功地获取了地址。  
  
## 请参阅  
 [错误处理和通知](../../build/reference/error-handling-and-notification.md)