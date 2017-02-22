---
title: "TN011：将 MFC 作为 DLL 的一部分使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_USRDLL 符号"
  - "DLL [C++], 链接"
  - "MFC DLL [C++], 将常规 DLL 链接到 MFC"
  - "TN011"
  - "USRDLL, 编译器开关"
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# TN011：将 MFC 作为 DLL 的一部分使用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该消息描述规则 DLL，它使您可以将 MFC 库作为 Windows 动态链接库的一部分来使用。  假定您熟悉 Windows DLL，以及如何生成它们。  有关 MFC 扩展 DLL 的信息，则您可以创建扩展到 MFC 库，请参见 [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)。  
  
## DLL 接口  
 常规 DLL 假定应用程序和 DLL 之间的接口与 C\# 的函数或者显式导出的类中指定。  MFC 类接口无法导出。  
  
 如果 DLL 和应用程序要使用 MFC，请安排一选择要使用 MFC 库的共享版本或静态链接到库的副本。  应用程序和 DLL 两种使用 MFC 库之一的标准版本。  
  
 规则 DLL 有若干优点：  
  
-   使用 DLL 的应用程序不必使用 MFC，并且不必是 Visual C\+\+ 应用程序。  
  
-   静态链接到 MFC 的规则 DLL，DLL 的大小只依赖于并使用链接的 MFC 和 C 运行期程序。  
  
-   动态链接到 MFC 的规则 DLL，在内存使用共享 MFC 版本会节省大量的版本非常显著。  但是，必须将共享的 DLL，MFC*\<version\>*.dll 和 Msvvcrt 与 DLL 的*\<version\>*.dll。  
  
-   DLL 设计是独立类的实现方式。  DLL 仅导出到要设计的 API。  因此，如果，实现更改，规则 DLL 是有效的。  
  
-   规则 DLL，DLL，则和应用程序所使用静态链接到 MFC 的 DLL 要比不使用 MFC，反之亦然 MFC 版本不同或应用程序中的问题。  由于静态 MFC 库链接到每个 DLL 或 EXE，不存在有关版本的有问题。  
  
## API限制  
 一些 MFC 功能不适用于 DLL 版本，或者由于技术方面的限制或者，因为应用程序一般提供这些服务。  MFC 当前版本，对象的唯一函数为 `CWinApp::SetDialogBkColor`。  
  
## 生成 DLL  
 当必须编译定义规则 DLL 静态链接到的 MFC、符号 `_USRDLL` 和 `_WINDLL`。  还必须编译 DLL 代码与以下编译器开关：  
  
-   **\/D\_WINDLL** 表示已编译为 DLL  
  
-   **\/D\_USRDLL** 指定所生成规则 DLL  
  
 您还必须定义这些符号和使用动态链接到 MFC 的这些编译器开关，并且编译规则 DLL 时。  此外，必须定义 `_AFXDLL` 符号，必须编译 DLL 代码为：  
  
-   **\/D\_AFXDLL** 指定要生成动态链接到 MFC 的规则 DLL  
  
 必须显式导出接口 \(API\) 应用程序和 DLL 之间。  建议您定义接口是低带宽，并且只使用 C 接口，则可以。  直接与 C 接口更复杂的 C\+\+ 类、易于维护。  
  
 API 将在可由 C 和 C\+\+ 文件包含的单独标题。  用于示例参见 MFC 在高级概念示例 [DLLScreenCap](../top/visual-cpp-samples.md) 的标题 ScreenCap.h。  若要导出函数，请输入其在模块上定义的函数定义文件 \(.DEF\) 或包含 `__declspec(dllexport)` 的 `EXPORTS` 节。  使用 `__declspec(dllimport)` 导入这些函数。客户可执行文件。  
  
 必须在动态链接到 MFC 的规则 DLL 的任何导出函数的开始处添加 `AFX_MANAGE_STATE` 宏。  此宏将当前模块状态到一个 DLL。  要使用该宏，需将下列代码行添加到从 DLL 导出的函数的开始处：  
  
 `AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`  
  
## DllMain WinMain \-\>  
 MFC 库定义初始化 [CWinApp](../mfc/reference/cwinapp-class.md) 派生对象在典型的 MFC 应用程序的标准 Win32 `DllMain` 入口点。  与在典型 MFC 应用程序中一样，将所有 DLL 特定的初始化放到 [InitInstance](../Topic/CWinApp::InitInstance.md) 成员函数中。  
  
 请注意，[CWinApp::Run](../Topic/CWinApp::Run.md) 机制不适用于 DLL，因为应用程序拥有主消息泵。  如果 DLL 显示无模式对话框或有自己的主框架窗口，则应用程序的主消息泵必须调用从 DLL 导出的例程来调用 [CWinApp::PreTranslateMessage](../Topic/CWinApp::PreTranslateMessage.md)。  
  
 有关此函数的示例，请参见 DLLScreenCap 示例。  
  
 MFC 提供 `DllMain` 函数将从 `CWinApp` 派生的类的方法 [CWinApp::ExitInstance](../Topic/CWinApp::ExitInstance.md)，卸载 DLL 之前。  
  
## 链接 DLL  
 静态链接到 MFC 的规则 DLL 中，必须链接 DLL 与 Nafxcwd.lib 或 Nafxcw.lib 与名为 Libcmt.lib 的 C 运行时的版本。  这些库之前生成并可能通过指定它们安装，在您安装时运行的 Visual C\+\+。  
  
## 代码示例  
 为完整示例参见 MFC 高级概念 DLLScreenCap 示例程序。  请注意的几个因素有趣本示例如下：  
  
-   DLL 的编译器标志和那些应用程序不同。  
  
-   链接线和 .DEF 文件和 DLL 的那些应用程序的不同。  
  
-   使用 DLL 的应用程序不必使用 C\+\+。  
  
-   由 C 或 C\+\+。活动和导出的 DLLScreenCap.def 的应用程序和 DLL 之间的接口是 API。  
  
 在常规 DLL 定义静态链接到 MFC 的示例说明的 API。  在此示例中，声明在 C\+\+ 用户的 `extern "C" { }` 块中。  这有多个好处。  首先，它使 DLL API可由非 C\+\+ 客户端应用程序使用。  其次，它减少了 DLL 系统开销，原因是 C\+\+ 名称修饰不会应用于导出的名称。  最后，它还使显式添加到 .DEF 文件（以便按顺序导出）更方便，无需再考虑 C\+\+ 名称修饰。  
  
```  
#ifdef __cplusplus  
extern "C" {  
#endif  /* __cplusplus */  
  
struct TracerData  
{  
    BOOL    bEnabled;  
    UINT    flags;  
};  
  
BOOL PromptTraceFlags(TracerData FAR* lpData);  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
 API 使用的结构从 MFC 类。API 标头没有派生和定义。  这减少接口 DLL 和应用程序之间的复杂性并使 DLL 可由 C 程序。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)