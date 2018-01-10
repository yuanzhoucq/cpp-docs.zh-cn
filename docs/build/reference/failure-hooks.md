---
title: "失败挂钩 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1609b713fef253e8beab270ee2ed048466da6504
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="failure-hooks"></a>失败挂钩
失败挂钩的启用方式与[通知挂钩](../../build/reference/notification-hooks.md)。 挂钩例程需要将返回一个适合的值，以便处理可以继续 （HINSTANCE 或 FARPROC） 或为 0 指示应引发异常。  
  
 指的是用户定义函数的指针变量是：  
  
```  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 **DelayLoadInfo**结构包含准确报告错误，包括从值所需的所有相关数据`GetLastError`。  
  
 如果通知为**dliFailLoadLib**，挂钩函数可以返回：  
  
-   如果为 0，它无法处理失败。  
  
-   HMODULE，如果失败挂钩解决问题并将加载在库自身。  
  
 如果通知为**dliFailGetProc**，挂钩函数可以返回：  
  
-   如果为 0，它无法处理失败。  
  
-   有效的进程地址 （导入函数地址），如果失败挂钩成功地获取本身的地址。  
  
## <a name="see-also"></a>请参阅  
 [错误处理和通知](../../build/reference/error-handling-and-notification.md)