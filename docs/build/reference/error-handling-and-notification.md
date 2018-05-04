---
title: 错误处理和通知 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2edec23da89766a45545566b0a689001d3ca75f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="error-handling-and-notification"></a>错误处理和通知
错误处理和通知的详细信息，请参阅[了解 Helper 函数](understanding-the-helper-function.md)。  
  
 挂钩函数的详细信息，请参阅[结构和常量定义](../../build/reference/structure-and-constant-definitions.md)。  
  
 如果程序使用延迟加载 Dll，它必须由于在程序运行时发生的失败将导致未经处理的异常能够可靠地处理错误。 失败处理是由两部分组成：  
  
 通过挂钩的恢复。  
 如果你的代码需要恢复或提供备用库和/或例程失败，则可以向可以提供或纠正此情况的帮助器函数提供的挂钩。 挂钩例程需要将返回一个适合的值，以便处理可以继续 （HINSTANCE 或 FARPROC） 或为 0 指示应引发异常。 它可能还会引发自己的异常或**longjmp**外挂钩。 有通知挂钩和失败挂钩。  
  
 通过异常报告。  
 如果所有所需的处理的错误是中止该过程，没有挂钩是必需的只要用户代码可以处理的异常。  
  
 以下主题讨论错误处理和通知：  
  
-   [通知挂钩](../../build/reference/notification-hooks.md)  
  
-   [失败挂钩](../../build/reference/failure-hooks.md)  
  
-   [异常](../../build/reference/exceptions-c-cpp.md)  
  
## <a name="see-also"></a>请参阅  
 [延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)