---
title: 失败挂钩
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
ms.openlocfilehash: 2bda1d34c85b1e88c7d278816e30e76537a7523b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463605"
---
# <a name="failure-hooks"></a>失败挂钩

失败挂钩的启用方式与[通知挂钩](../../build/reference/notification-hooks.md)。 挂钩例程需要返回合适的值，以便处理可以继续 （HINSTANCE 或 FARPROC） 为 0，表示应引发异常。

指的是用户定义函数的指针变量是：

```
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

**DelayLoadInfo**结构中包含错误，包括从值的准确报告所需的所有相关数据`GetLastError`。

如果通知是**dliFailLoadLib**，挂钩函数可以返回：

- 如果为 0，它不能处理故障。

- HMODULE，如果失败挂钩解决该问题并加载库本身。

如果通知是**dliFailGetProc**，挂钩函数可以返回：

- 如果为 0，它不能处理故障。

- 有效的进程地址 （导入函数地址），如果失败挂钩成功地获取本身的地址。

## <a name="see-also"></a>请参阅

[错误处理和通知](../../build/reference/error-handling-and-notification.md)