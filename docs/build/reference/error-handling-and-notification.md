---
title: 错误处理和通知
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, and notification
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
ms.openlocfilehash: 7aae4d68b272a6c12233f283d4b263648062b7c1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418940"
---
# <a name="error-handling-and-notification"></a>错误处理和通知

错误处理和通知的详细信息，请参阅[了解 Helper 函数](understanding-the-helper-function.md)。

挂钩函数的详细信息，请参阅[结构和常量定义](../../build/reference/structure-and-constant-definitions.md)。

如果程序使用延迟加载 Dll，它必须处理错误能够稳定地因为该程序运行期间发生的失败会导致未经处理的异常。 失败处理包含两个部分：

通过挂钩的恢复。
如果你的代码需要恢复或提供有关失败的备用库和/或例程，可以给可以提供或修复此情形的帮助器函数提供的挂钩。 挂钩例程需要返回合适的值，以便处理可以继续 （HINSTANCE 或 FARPROC） 为 0，表示应引发异常。 它还可能会引发自己的异常或**longjmp**超出挂钩。 有通知挂钩和失败挂钩。

通过异常报告。
如果所有所需的处理错误将中止该过程，没有挂钩就不需要，只要用户代码可以处理该异常。

以下主题讨论错误处理和通知：

- [通知挂钩](../../build/reference/notification-hooks.md)

- [失败挂钩](../../build/reference/failure-hooks.md)

- [异常](../../build/reference/exceptions-c-cpp.md)

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)
