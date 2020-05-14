---
title: 动态链接到 MFC 的规则 MFC DLL 的模块状态
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: cedce676f5586369446c9856fd33e4d16c237b27
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220577"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>动态链接到 MFC 的规则 MFC DLL 的模块状态

通过将规则 MFC DLL 动态链接到 MFC DLL 的功能可以实现一些非常复杂的配置。 例如，规则 MFC DLL 和使用它的可执行文件可以动态链接到 MFC DLL 和任何 MFC 扩展 DLL。

此配置会对 MFC 全局数据（例如指向当前 `CWinApp` 对象的指针和句柄映射）造成问题。

在 MFC 版本 4.0 之前，此全局数据驻留在 MFC DLL 本身中，由进程中的所有模块共享。 因为使用 Win32 DLL 的每个进程都会获取自己的 DLL 数据副本，所以此方案提供了一种简单方法来跟踪每个进程的数据。 此外，由于 AFXDLL 模型假定在进程中只有一个 `CWinApp` 对象和一组句柄映射，因此可以在 MFC DLL 本身中跟踪这些项。

但通过将规则 MFC DLL 动态链接到 MFC DLL 的功能，现在一个进程中可以有两个或更多 `CWinApp` 对象，还可以有两组或更多句柄映射。 MFC 如何跟踪应使用的内容？

解决方案是为每个模块（应用程序或规则 MFC DLL）提供其自己的这些全局状态信息的副本。 因此，在规则 MFC DLL 中对 AfxGetApp  的调用会返回指向 DLL 中的 `CWinApp` 对象（而不是可执行文件中的对象）的指针。 MFC 全局数据的这一每模块副本称为模块状态，在 [MFC 技术说明 58](../mfc/tn058-mfc-module-state-implementation.md) 中进行了介绍。

MFC 公共窗口过程会自动切换到正确的模块状态，因此无需在规则 MFC DLL 中实现的任何消息处理程序中考虑它。 但是，当可执行文件调入规则 MFC DLL 时，需要将当前模块状态显式设置为 DLL 的模块状态。 为此，请在从 DLL 导出的每个函数中使用 AFX_MANAGE_STATE  宏。 这通过将以下代码行添加到从 DLL 导出的函数的开头来实现：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)

- [动态链接到 MFC 的规则 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL](extension-dlls-overview.md)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)
