---
title: "错误处理和通知 | Microsoft Docs"
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
  - "错误处理, 和通知"
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误处理和通知
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有关错误处理和通知的更多信息，请参见[了解 Helper 函数](http://msdn.microsoft.com/zh-cn/6279c12c-d908-4967-b0b3-cabfc3e91d3d)。  
  
 有关挂钩函数的更多信息，请参见[结构和常数定义](../../build/reference/structure-and-constant-definitions.md)  
  
 如果程序使用延迟加载的 DLL，则它必须能够稳定地处理错误，这是因为在程序运行时发生的失败将导致未经处理的异常。  失败处理由两部分组成：  
  
 通过挂钩恢复。  
 如果发生失败时，代码需要恢复或提供备用库和\/或例程，可以给 Helper 函数提供一个能供给或弥补这种情况的挂钩。  挂钩例程需返回一个合适的值，以便处理能继续进行（HINSTANCE 或 FARPROC），或者返回 0 指示将引发异常。  它也可以引发自己的异常或者通过 **longjmp** 脱离挂钩。  挂钩有通知挂钩和失败挂钩。  
  
 通过异常报告。  
 如果处理错误所需做的只是中止过程，那么只要用户代码能处理异常，挂钩就不需要。  
  
 下列主题论述错误处理和通知：  
  
-   [通知挂钩](../../build/reference/notification-hooks.md)  
  
-   [失败挂钩](../../build/reference/failure-hooks.md)  
  
-   [异常](../../build/reference/exceptions-c-cpp.md)  
  
## 请参阅  
 [链接器的延迟加载 DLL 支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)