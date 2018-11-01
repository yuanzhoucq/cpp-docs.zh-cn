---
title: 动态链接到 MFC 的规则 MFC Dll
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 550391d51560ff0beca8252ffb6193dd1e4d89b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632383"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>动态链接到 MFC 的规则 MFC Dll

MFC DLL 动态链接到 MFC 正则表达式是在内部，使用 MFC 的 DLL 和可由 MFC 或非 MFC 可执行文件调用 DLL 中导出的函数。 如名称所述，使用动态链接库版本的 MFC （也称为共享的 MFC 版本） 生成此类型的 DLL。 通常是从正则表达式使用标准的 C 接口的 MFC DLL 导出函数。

必须添加`AFX_MANAGE_STATE`动态链接到 MFC，以便将当前模块状态设置为 dll 的规则 MFC Dll 中的所有导出函数的开始处的宏。 这是通过将以下代码行添加到从 DLL 导出的函数的开头：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

常规 MFC DLL 动态链接到 MFC 具有以下功能：

- 这是一种新引入的 Visual c + + 4.0 的 DLL。

- 可以采用支持的 Dll （C、 c + +、 Pascal、 Visual Basic 等）; 使用任何语言编写客户端可执行文件它不必是 MFC 应用程序。

- 与静态链接的规则 MFC DLL，这种类型的 DLL 动态链接到 MFC DLL (也称为共享 MFC DLL)。

- MFC 导入库链接到此类型的 DLL 是同一个用于 MFC 扩展 Dll 或使用 MFC DLL 的应用程序：.lib MFCxx (D)。

常规 MFC DLL 动态链接到 MFC 具有以下要求：

- 与编译这些 Dll **_AFXDLL**定义，就像动态链接到 MFC DLL 的可执行文件。 但是 **_USRDLL**也定义，就像静态链接到 MFC 的规则 MFC DLL。

- 这种类型的 DLL 必须实例化`CWinApp`-派生的类。

- 这种类型的 DLL 将`DllMain`MFC 提供。 将中的所有 DLL 特定初始化代码都放`InitInstance`中的成员函数和终止代码`ExitInstance`如普通的 MFC 应用程序中所示。

由于这种 DLL 使用 MFC 的动态链接库版本，您必须显式设置为 DLL 的一个的当前模块状态。 若要执行此操作，请使用[AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state)从 DLL 导出的每个函数开头的宏。

规则 MFC Dll 必须具有`CWinApp`-派生的类以及该类应用程序的单个对象的 MFC 应用程序一样。 但是， `CWinApp` DLL 的对象不具有主消息泵，如同`CWinApp`应用程序的对象。

请注意，`CWinApp::Run`机制不适用于 DLL，因为应用程序拥有主消息泵。 如果您的 DLL 将显示无模式对话框或有其自己的主框架窗口，应用程序的主消息泵必须调用 DLL 导出的例程来调用`CWinApp::PreTranslateMessage`。

将中的所有 DLL 特定初始化都放`CWinApp::InitInstance`如普通的 MFC 应用程序中所示的成员函数。 `CWinApp::ExitInstance`成员函数在`CWinApp`派生的类称为从 MFC 提供`DllMain`函数卸载 DLL 之前。

使用你的应用程序，必须将分发共享的 Dll MFCx0.dll 和 Msvcr*0.dll （或类似文件）。

动态链接到 MFC 的 DLL 无法还以静态方式链接到 MFC。 应用程序链接到 MFC 的规则 Dll 动态链接到 MFC 它就像任何其他 DLL。

通常是从正则表达式使用标准的 C 接口的 MFC DLL 导出的符号。 从规则 MFC DLL 导出函数的声明如下所示：

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

规则 MFC DLL 的所有内存分配应都遵守 DLL;DLL 不应传递给或接收从调用的可执行文件的以下任何：

- MFC 对象的指针

- 指向由 MFC 分配的内存的指针

如果你需要执行上述任一或者如果你需要调用的可执行文件和 DLL 之间传递 MFC 派生的对象，则必须生成 MFC 扩展 DLL。

它可以安全地将指针传递给已分配的内存的 C 运行时库应用程序和 DLL 之间仅当您制作数据的副本。 您必须删除或调整这些指针的大小或使用它们而无需进行的内存的副本。

当生成规则 MFC DLL 的动态链接到 MFC 时，需要使用该宏[AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state)正确切换 MFC 模块状态。 这是通过将以下代码行添加到从 DLL 导出的函数的开头：

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

**AFX_MANAGE_STATE**在静态链接到 MFC 的规则 MFC Dll 或 MFC 扩展 Dll 中，不应使用宏。 有关详细信息，请参阅[管理 MFC 模块状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)。

有关如何编写、 构建和使用的规则 MFC DLL 的示例，请参阅示例[DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。 有关动态链接到 MFC 的规则 MFC Dll 的详细信息，请参阅示例的抽象中标题为"转换 DLLScreenCap 到动态链接与 MFC DLL"部分。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [初始化规则 MFC Dll](../build/run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [动态链接到 MFC 的规则 MFC DLL 的模块状态](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [管理 MFC 模块状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)

- [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>请参阅

[DLL 的类型](../build/kinds-of-dlls.md)