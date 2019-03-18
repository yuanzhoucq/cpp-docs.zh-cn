---
title: 通知挂钩
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
ms.openlocfilehash: 884d8e8479b7cad28d99e19adfac4d05dbeec5f5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818305"
---
# <a name="notification-hooks"></a>通知挂钩

通知挂钩将调用之前帮助器例程中执行以下操作：

- 若要查看已加载，检查库存储句柄。

- **LoadLibrary**调用以尝试加载的 dll。

- **GetProcAddress**调用以尝试获取过程的地址。

- 返回到延迟导入负载转换 （thunk）。

启用通知挂钩：

- 通过提供新的定义的指针 **__pfnDliNotifyHook2**初始化为指向您自己的函数接收通知。

   \- 或 -

- 通过设置指针 **__pfnDliNotifyHook2**到您的挂钩函数之前对该程序的 DLL 的任何调用延迟加载。

如果通知是**dliStartProcessing**，挂钩函数可以返回：

- NULL

   默认帮助器处理加载的 DLL。 这可用于调用只是供您参考。

- 函数指针

   绕过默认延迟加载处理。 这样可以提供自己负载的处理程序。

如果通知是**dliNotePreLoadLibrary**，挂钩函数可以返回：

- 如果为 0，它只是需要信息性通知。

- 有关加载的 DLL，如果它加载 DLL 本身 HMODULE。

如果通知是**dliNotePreGetProcAddress**，挂钩函数可以返回：

- 如果为 0，它只是需要信息性通知。

- 导入的函数的地址，如果挂钩函数获取本身的地址。

如果通知是**dliNoteEndProcessing**，挂钩函数的返回值将被忽略。

如果此指针进行初始化 （非零），延迟加载 helper 将调用该函数在执行过程的某些通知点处。 函数指针具有以下定义：

```C
// The "notify hook" gets called for every call to the
// delay load helper.  This allows a user to hook every call and
// skip the delay load helper entirely.
//
// dliNotify == {
//  dliStartProcessing |
//  dliNotePreLoadLibrary  |
//  dliNotePreGetProc |
//  dliNoteEndProcessing}
//  on this call.
//
ExternC
PfnDliHook   __pfnDliNotifyHook2;

// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

通知传入**DelayLoadInfo**挂钩函数以及通知值的结构。 此数据与使用延迟加载 helper 例程的完全相同。 通知值将是中定义的值之一[结构和常量定义](structure-and-constant-definitions.md)。

## <a name="see-also"></a>请参阅

[错误处理和通知](error-handling-and-notification.md)
