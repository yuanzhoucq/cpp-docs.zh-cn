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
ms.openlocfilehash: 3ab51ca8097bd5ec27e8e7cfd8b8f19d76195664
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273321"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>动态链接到 MFC 的规则 MFC DLL 的模块状态

动态链接到 MFC DLL 的正则表达式 MFC DLL 的能力使一些非常复杂的配置。 例如，规则 MFC DLL 并使用它的可执行文件可以同时动态链接到 MFC DLL 和任何 MFC 扩展 Dll。

此配置会引起问题方面 MFC 全局数据，例如当前指向`CWinApp`对象和句柄的映射。

之前 MFC 4.0 版中，此全局数据驻留在 MFC DLL 本身，并且在进程中共享所有模块。 使用 Win32 DLL 的每个进程获取其自己的 DLL 的数据副本，因为此方案提供跟踪每个进程的数据的简单方法。 此外，因为 AFXDLL 模型假定，会有一个`CWinApp`对象和只有一组处理过程中的映射，这些项可以跟踪在 MFC DLL 本身。

但能够动态链接到 MFC DLL 的规则 MFC DLL，则现在可以有两个或多个`CWinApp`进程中的对象，和的句柄映射还两个或多个集。 如何 does MFC 跟踪的应使用哪些功能？

解决方案是为每个模块 （应用程序或规则 MFC DLL） 提供其自己此全局状态信息的副本。 因此，调用**AfxGetApp**常规 MFC DLL 返回一个指向`CWinApp`在 DLL 中，不是可执行文件中的对象。 MFC 中的全局数据的此每个模块的副本称为模块状态和中所述[MFC 技术说明 58](../mfc/tn058-mfc-module-state-implementation.md)。

MFC 公共窗口过程会自动切换到正确的模块的状态，因此不需要担心在规则 MFC DLL 中实现任何消息处理程序。 但当可执行文件调用到规则 MFC DLL 时，需要显式将当前模块状态设置为 dll。 若要执行此操作，请使用**AFX_MANAGE_STATE**从 DLL 导出的每个函数中的宏。 这是通过将以下代码行添加到从 DLL 导出的函数的开头：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [管理 MFC 模块状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)

- [动态链接到 MFC 的规则 MFC Dll](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL](extension-dlls-overview.md)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](dlls-in-visual-cpp.md)
