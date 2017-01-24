---
title: "动态链接到 MFC 的规则 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFX_MANAGE_STATE 宏"
  - "DLL [C++], 规则"
  - "动态链接的 DLL [C++]"
  - "规则 DLL [C++], 动态链接到 MFC"
  - "共享的 DLL 版本 [C++]"
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 动态链接到 MFC 的规则 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

动态链接到 MFC 的规则 DLL 是在内部使用 MFC 的 DLL，这类 DLL 中的导出函数可由 MFC 或非 MFC 可执行文件调用。  正如名称所体现的，这类 DLL 是使用 MFC 动态链接库版本（也称作 MFC 共享版本）生成的。  函数通常是通过标准 C 接口从规则 DLL 导出的。  
  
 在动态链接到 MFC 的规则 DLL 中，必须在所有导出函数的开始处添加 `AFX_MANAGE_STATE` 宏，以将当前模块的状态设置为 DLL 的状态。  为此，需将下列代码行添加到从 DLL 导出的函数的开始处：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 动态链接到 MFC 的规则 DLL 具有下列功能：  
  
-   它是由 Visual C\+\+ 4.0 引入的一种新的 DLL 类型。  
  
-   客户端可执行文件可以用任何支持使用 DLL 的语言（C、C\+\+、Pascal、Visual Basic 等）编写；它不必是 MFC 应用程序。  
  
-   与静态链接的规则 DLL 不同，这类 DLL 动态链接到 MFC DLL（也称作共享 MFC DLL）。  
  
-   链接到这类 DLL 的 MFC 导入库与用于使用 MFC DLL 的扩展 DLL 或应用程序的 MFC 导入库相同：都是 MFCxx\(D\).lib。  
  
 动态链接到 MFC 的规则 DLL 具有下列要求：  
  
-   与动态链接到 MFC DLL 的可执行文件相同，这些 DLL 也是通过定义的 **\_AFXDLL** 进行编译的。  但同时也像静态链接到 MFC 的规则 DLL 那样，定义了 **\_USRDLL**。  
  
-   这类 DLL 必须实例化 `CWinApp` 派生类。  
  
-   此类型的 DLL 使用 MFC 提供的 `DllMain`。  与在标准 MFC 应用程序中一样，将所有 DLL 特定的初始化代码放到 `InitInstance` 成员函数中，将终止代码放到 `ExitInstance` 中。  
  
 由于这类 DLL 使用 MFC 动态链接库版本，因此必须将当前模块的状态显式设置为 DLL 的状态。  为此，请在从 DLL 导出的每个函数的开始处使用 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 宏。  
  
 与 MFC 应用程序相同，规则 DLL 必须有一个 `CWinApp` 派生的类和此应用程序类的单个对象。  然而，与应用程序的 `CWinApp` 对象不同，DLL 的 `CWinApp` 对象没有主消息泵。  
  
 请注意，`CWinApp::Run` 机制不适用于 DLL，因为应用程序拥有主消息泵。  如果 DLL 生成无模式对话框或有自己的主框架窗口，则应用程序的主消息泵必须调用从 DLL 导出的例程来调用 `CWinApp::PreTranslateMessage`。  
  
 与在标准 MFC 应用程序中一样，将所有 DLL 特定的初始化放到 `CWinApp::InitInstance` 成员函数中。  卸载 DLL 之前，将从 MFC 提供的 `DllMain` 函数调用 `CWinApp` 派生类的 `CWinApp::ExitInstance` 成员函数。  
  
 必须随应用程序一起发布共享 DLL：MFCx0.dll 和 Msvcr\*0.dll（或类似的文件）。  
  
 动态链接到 MFC 的 DLL 无法同时静态链接到 MFC。  像任何其他 DLL 一样，应用程序链接到动态链接到 MFC 的规则 DLL。  
  
 符号通常是通过标准 C 接口从规则 DLL 导出的。  从规则 DLL 导出的函数的声明类似下面这样：  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 规则 DLL 内的所有内存分配都应在该 DLL 内进行；DLL 不应向调用可执行文件传递或从调用可执行文件接收下列任何指针：  
  
-   指向 MFC 对象的指针  
  
-   指向由 MFC 分配的内存的指针  
  
 如果需要执行上述任一操作，或者如果需要在调用可执行文件和 DLL 之间传递 MFC 派生的对象，则必须生成扩展 DLL。  
  
 仅当创建了数据副本后，在应用程序和 DLL 之间传递指向 C 运行库所分配的内存的指针才是安全的。  一定不要删除这些指针或调整它们的大小，也不要在没有创建内存副本的情况下使用这些指针。  
  
 生成动态链接到 MFC 的规则 DLL 时，需要使用 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 宏正确切换 MFC 模块状态。  为此，需将下列代码行添加到从 DLL 导出的函数的开始处：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 **AFX\_MANAGE\_STATE** 宏不应当用于静态链接到 MFC 的规则 DLL 中，也不应当用于扩展 DLL 中。  有关更多信息，请参见[管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)。  
  
 有关如何编写、生成和使用规则 DLL 的示例，请参见示例 [DLLScreenCap](http://msdn.microsoft.com/zh-cn/2171291d-3a50-403b-90a1-d93c2acb4f4a)。  有关动态链接到 MFC 的规则 DLL 的更多信息，请参见示例摘要中标题为“转换 DLLScreenCap 以与 MFC DLL 动态链接”的部分。  
  
## 你希望做什么？  
  
-   [初始化规则 DLL](../build/initializing-regular-dlls.md)  
  
## 您想进一步了解什么？  
  
-   [动态链接到 MFC 的规则 DLL 的模块状态](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
  
-   [管理 MFC 模块的状态数据](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [在规则 DLL 中使用数据库、OLE 和套接字扩展 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [将 MFC 作为 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
## 请参阅  
 [DLL 类型](../build/kinds-of-dlls.md)