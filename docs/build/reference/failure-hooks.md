---
title: 失败挂钩 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be598a77ca48eeee03360a3b598b0567abc6ee4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371780"
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