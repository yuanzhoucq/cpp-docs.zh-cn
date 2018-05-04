---
title: 动态链接到 MFC 的正则 MFC Dll |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e20a3937786d65945256eeadcf0bf08b0314470
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>动态链接到 MFC 的正则 MFC Dll
MFC DLL 动态链接到 MFC 正则表达式是在内部，使用 MFC 的 DLL，可以由 MFC 或非 MFC 可执行文件调用 DLL 中导出的函数。 名称所述，使用动态链接库版本的 MFC （也称为 MFC 的共享版本） 进行构建这种类型的 DLL。 函数通常是从正则表达式使用标准的 C 界面的 MFC DLL 导出的。  
  
 你必须添加`AFX_MANAGE_STATE`宏的动态链接到 MFC 将当前模块状态设置为一个用于 DLL 规则 MFC Dll 中的所有导出函数的开头。 这可通过将以下代码行添加到从 DLL 导出的函数的开头：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 常规 MFC DLL 动态链接到 MFC 具有以下功能：  
  
-   这是一种新引入的 Visual c + + 4.0 的 DLL。  
  
-   可以以支持 Dll （C、 c + +、 Pascal、 Visual Basic 等）; 使用任何语言编写的客户端可执行文件它不必是 MFC 应用程序。  
  
-   与静态链接的常规 MFC DLL，这种类型的 DLL 动态链接到 MFC DLL (也称为共享 MFC DLL)。  
  
-   链接到此类型的 DLL 的 MFC 导入库为用于 MFC 扩展 Dll 或应用程序中使用 MFC DLL 的同一： MFCxx (D).lib。  
  
 常规 MFC DLL 动态链接到 MFC 具有以下要求：  
  
-   这些 Dll 在编译时带有 **_AFXDLL**定义，就像动态链接到 MFC DLL 的可执行文件。 但是 **_USRDLL**也被定义一样静态链接到 MFC 常规 MFC DLL。  
  
-   这种类型的 DLL 必须实例化`CWinApp`-派生类。  
  
-   这种类型的 DLL 将`DllMain`MFC 提供。 所有 DLL 特定初始化将代码都放置在`InitInstance`中的成员函数和终止代码`ExitInstance`如下所示普通的 MFC 应用程序。  
  
 由于这种类型的 DLL 使用 MFC 的动态链接库版本，你必须显式设置为一个用于 DLL 的当前模块状态。 若要执行此操作，使用[AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state)从 DLL 导出的每个函数开头的宏。  
  
 常规 MFC Dll 必须有`CWinApp`-派生的类以及该类应用程序的单个对象一样 MFC 应用程序。 但是，`CWinApp`的 DLL 的对象不具有主消息泵，一样`CWinApp`的应用程序的对象。  
  
 请注意，`CWinApp::Run`机制不适用于 DLL，由于应用程序拥有的主消息泵。 如果您的 DLL 生成无模式对话框，或有其自己的主框架窗口，应用程序的主消息泵必须调用 DLL 导出的调用的例程`CWinApp::PreTranslateMessage`。  
  
 将中的所有 DLL 特定初始化都放`CWinApp::InitInstance`如下所示普通的 MFC 应用程序的成员函数。 `CWinApp::ExitInstance`成员函数你`CWinApp`派生的类称为从 MFC 提供`DllMain`函数之前将在卸载 DLL 函数。  
  
 你必须与你的应用程序分发共享的 Dll MFCx0.dll 和 Msvcr*0.dll （或类似的文件）。  
  
 动态链接到 MFC 的 DLL 无法还静态链接到 MFC。 应用程序链接到 MFC 的规则 Dll 动态链接到 MFC 它就像任何其他 DLL。  
  
 符号通常是从正则表达式使用标准的 C 界面的 MFC DLL 导出的。 从常规 MFC DLL 导出函数的声明如下所示：  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 常规 MFC DLL 的所有内存分配应都保留在 DLL 中;DLL 不应将传递给或接收从调用的可执行文件的以下任何：  
  
-   指向 MFC 对象的指针  
  
-   对 mfc 分配的内存的指针  
  
 如果你需要执行与上述任一操作，或如果你需要调用的可执行文件和 DLL 之间传递 MFC 派生的对象，则必须生成 MFC 扩展 DLL。  
  
 则可以安全地将指针传递给已分配的内存由 C 运行时库应用程序和 DLL 之间仅当你创建的数据副本。 你必须删除或调整这些指针的大小或使用它们而无需制作内存的副本。  
  
 当生成正则 MFC DLL，该服务动态链接到 MFC 时，你需要使用宏[AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state)正确切换 MFC 模块状态。 这可通过将以下代码行添加到从 DLL 导出的函数的开头：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 **AFX_MANAGE_STATE**在静态链接到 MFC 的正则 MFC Dll 或 MFC 扩展 Dll 中，不应使用宏。 有关详细信息，请参阅[管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)。  
  
 有关如何编写、 生成和使用的规则的 MFC DLL 的示例，请参见示例[DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)。 有关动态链接到 MFC 的规则 MFC Dll 的详细信息，请参阅中的示例抽象标题为"转换 DLLScreenCap 到动态链接与 MFC DLL"部分。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
-   [初始化 MFC 的规则 Dll](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [动态链接到 MFC 的规则的 MFC DLL 的模块状态](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
  
-   [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [在规则 MFC DLL 中使用数据库、OLE 和套接字 MFC 扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
## <a name="see-also"></a>请参阅  
 [DLL 的类型](../build/kinds-of-dlls.md)