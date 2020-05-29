---
title: 动态链接到 MFC 的规则 MFC DLL
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 3bfed5f75dab4c501708950fdb99f53c40ec142c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314996"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>动态链接到 MFC 的规则 MFC DLL

动态链接到 MFC 的规则 MFC DLL 是在内部使用 MFC 的 DLL，而 DLL 中的导出函数可以由 MFC 或非 MFC 可执行文件调用。 顾名思义，这种 DLL 是使用 MFC 的动态链接库版本（也称为 MFC 的共享版本）生成的。 通常使用标准 C 接口从规则 MFC DLL 导出函数。

你必须在动态链接到 MFC 的规则 MFC DLL 中的所有导出函数的开头处添加 `AFX_MANAGE_STATE` 宏，以将当前模块状态设置为 DLL 的状态。 这通过将以下代码行添加到从 DLL 导出的函数的开头来实现：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

动态链接到 MFC 的规则 MFC DLL 具有以下功能：

- 这是 Visual C++ 4.0 引入的新型 DLL。

- 可以采用支持使用 DLL 的任何语言（C、C++、Pascal、Visual Basic 等）编写客户端可执行文件；它不必是 MFC 应用程序。

- 与静态链接的规则 MFC DLL 不同，这种 DLL 动态链接到 MFC DLL（也称为共享 MFC DLL）。

- 链接到这种 DLL 的 MFC 导入库与用于 MFC 扩展 DLL 或应用程序（使用 MFC DLL）的库相同：MFCxx(D).lib。

动态链接到 MFC 的规则 MFC DLL 具有以下要求：

- 编译这些 DLL 时需定义 _AFXDLL  ，就像动态链接到 MFC DLL 的可执行文件一样。 但同时还需定义 _USRDLL  ，就像静态链接到 MFC 的规则 MFC DLL 一样。

- 这种 DLL 必须实例化 `CWinApp` 派生类。

- 这种 DLL 使用 MFC 提供的 `DllMain`。 将所有特定于 DLL 的初始化代码都置于 `InitInstance` 成员函数中，而将终止代码置于 `ExitInstance` 中，就如同在普通 MFC 应用程序中一样。

由于这种 DLL 使用 MFC 的动态链接库版本，因此必须将当前模块状态显式设置为 DLL 的状态。 为此，请在从 DLL 导出的每个函数的开头使用 [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) 宏。

与 MFC 应用程序一样，规则 MFC DLL 必须具有 `CWinApp` 派生类和该应用程序类的单个对象。 但是，DLL 的 `CWinApp` 对象没有主消息泵，而应用程序的 `CWinApp` 对象也是如此。

请注意，`CWinApp::Run` 机制不适用于 DLL，因为应用程序拥有主消息泵。 如果 DLL 显示无模式对话框或有自己的主框架窗口，则应用程序的主消息泵必须调用从 DLL 导出的例程来调用 `CWinApp::PreTranslateMessage`。

将所有特定于 DLL 的初始化代码都置于 `CWinApp::InitInstance` 成员函数中，就如同在普通 MFC 应用程序中一样。 在卸载 DLL 之前，从 MFC 提供的 `DllMain` 函数调用 `CWinApp` 派生类的 `CWinApp::ExitInstance` 成员函数。

你必须随应用程序分发共享的 DLL MFCx0.dll 和 Msvcr*0.dll（或类似文件）。

动态链接到 MFC 的 DLL 不能同时又静态链接到 MFC。 应用程序链接到动态链接到 MFC 的规则 MFC DLL，就像链接到任何其他 DLL 一样。

通常使用标准 C 接口从规则 MFC DLL 导出符号。 从规则 MFC DLL 导出的函数的声明如下所示：

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

规则 MFC DLL 内的所有内存分配都应保留在 DLL 内；DLL 不应向调用可执行文件传递或从其接收以下任何内容：

- 指向 MFC 对象的指针

- 指向由 MFC 分配的内存的指针

如果需要执行上述任何操作，或者需要在调用可执行文件与 DLL 之间传递 MFC 派生对象，则必须生成 MFC 扩展 DLL。

仅当创建数据的副本时，才可安全地在应用程序和 DLL 之间传递指向由 C 运行时库分配的内存的指针。 不得删除这些指针或重设其大小，也不得在不创建内存副本的情况下使用它们。

在生成动态链接到 MFC 的规则 MFC DLL 时，需要使用宏 [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) 来正确切换 MFC 模块状态。 这通过将以下代码行添加到从 DLL 导出的函数的开头来实现：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

在静态链接到 MFC 的规则 MFC DLL 或 MFC 扩展 DLL 中，不应使用 AFX_MANAGE_STATE  宏。 有关详细信息，请参阅[管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)。

有关如何编写、生成和使用规则 MFC DLL 的示例，请参阅示例 [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。 有关动态链接到 MFC 的规则 MFC DLL 的详细信息，请参阅该示例的摘要中标题为“Converting DLLScreenCap to Dynamically Link with the MFC DLL”（转换 DLLScreenCap 以动态链接到 MFC DLL）的部分。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [初始化规则 MFC DLL](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [动态链接到 MFC 的规则 MFC DLL 的模块状态](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)

- [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [将 MFC 用作 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>请参阅

[DLL 的类型](kinds-of-dlls.md)
