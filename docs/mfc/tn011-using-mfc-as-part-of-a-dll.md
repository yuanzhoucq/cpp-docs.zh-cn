---
title: "TN011： 将 MFC 作为 DLL 的一部分使用 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.dll
dev_langs: C++
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d0ac05e314f3f8354ba289695afa672b1e28881
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011：将 MFC 作为 DLL 的一部分使用
本说明介绍正则 MFC Dll，它允许你使用 MFC 库作为 Windows 动态链接库 (DLL) 的一部分。 此说明假定您已熟悉 Windows DLL 及其生成方式。 有关 MFC 扩展 Dll，使用它可以创建扩展 MFC 库中，请参阅[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)。  
  
## <a name="dll-interfaces"></a>DLL 接口  
 MFC 的规则 Dll 假定应用程序和 DLL 之间的接口在类似 C 的函数或显式导出的类中指定。 MFC 类接口无法导出。  
  
 如果 DLL 和应用程序要使用 MFC，则请选择是使用共享版本的 MFC 库还是静态链接到这些库的副本。 应用程序和 DLL 可能都会使用 MFC 库的标准版本之一。  
  
 MFC 的规则 Dll 有若干优点：  
  
-   使用 DLL 的应用程序不必使用 MFC，并且不必是 Visual C++ 应用程序。  
  
-   静态链接到 MFC 的规则 MFC dll，DLL 的大小取决于仅使用和链接的 MFC 和 C 运行时例程。  
  
-   动态链接到 MFC 的规则 MFC dll，内存中开始使用共享的版本的 MFC 节省的空间可能很明显。 但是，你必须将分发共享的 Dll，Mfc*\<版本 >*.dll 和 Msvvcrt*\<版本 >*.dll，与您的 DLL。  
  
-   DLL 设计独立于类的实现方式之外。 您的 DLL 设计仅导出到需要的 API。 因此，如果实现发生更改，MFC 的规则 Dll 将仍然有效。  
  
-   使用 MFC 的规则 Dll，静态链接到 MFC，如果 DLL 和应用程序使用 MFC，有想 MFC DLL 或，反之亦然，这样的不同版本的应用程序无任何问题。 由于 MFC 库将静态链接到每个 DLL 或 EXE，因此您具有哪一版本没有任何问题。  
  
## <a name="api-limitations"></a>API 限制  
 一些 MFC 功能不适用于 DLL 版本，原因是技术方面的限制或者这些服务一般都是应用程序提供的。 利用当前版本的 MFC，唯一不适用的功能是 `CWinApp::SetDialogBkColor`。  
  
## <a name="building-your-dll"></a>生成您的 DLL  
 编译静态链接到 MFC，符号的正则 MFC Dll 时`_USRDLL`和`_WINDLL`必须定义。 你的 DLL 代码还必须使用下列编辑器开关进行编译：  
  
- **/ D_WINDLL**表示编译为 dll  
  
- **/ D_USRDLL**指定您将生成正则 MFC DLL  
  
 你还必须定义这些符号和编译动态链接到 MFC 的规则 MFC Dll 时使用这些编译器开关。 此外，必须定义 `_AFXDLL` 符号，并且必须使用以下内容编译 DLL 代码：  
  
- **/ D_AFXDLL**指定您将生成动态链接到 MFC 的正则 MFC DLL  
  
 必须显式导出应用程序和 DLL 之间的接口 (API)。 建议您将接口定义为低带宽，并且如果可以只使用 C 接口。 直接 C 接口更易于维护更复杂的 C++ 类。  
  
 将 API 放在 C 文件和 C++ 文件均可包含的单独标头中。 请参阅 MFC 高级概念示例中的 screencap.h [DLLScreenCap](../visual-cpp-samples.md)有关示例。 若要导出函数，请在模块定义文件 (.DEF) 的 `EXPORTS` 部分中输入它们，或将 `__declspec(dllexport)` 包含在您的函数定义中。 使用 `__declspec(dllimport)` 将这些函数导入客户端可执行文件中。  
  
 你必须添加`AFX_MANAGE_STATE`开头的动态链接到 MFC 的正则 MFC Dll 中的所有导出函数的宏。 此宏会将当前模块状态设置为 DLL 的模块状态。 若要使用该宏，请将以下代码行添加到从 DLL 导出的函数的开始处：  
  
 `AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`  
  
## <a name="winmain---dllmain"></a>WinMain -> DllMain  
 MFC 库定义的标准 Win32`DllMain`初始化的入口点你[CWinApp](../mfc/reference/cwinapp-class.md)派生如下所示典型的 MFC 应用程序的对象。 将中的所有 DLL 特定初始化都放[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)如下所示典型的 MFC 应用程序的方法。  
  
 请注意， [cwinapp:: Run](../mfc/reference/cwinapp-class.md#run)机制不适用于 DLL，由于应用程序拥有的主消息泵。 如果您的 DLL 显示无模式对话框，或有其自己的主框架窗口，应用程序的主消息泵必须调用 DLL 导出的调用的例程[CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage)。  
  
 有关此函数的使用，请参阅 DLLScreenCap 示例。  
  
 `DllMain` MFC 提供了将调用的函数[CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)方法的类派生自`CWinApp`将在卸载 DLL 之前。  
  
## <a name="linking-your-dll"></a>链接您的 DLL  
 静态链接到 MFC 的规则 MFC dll，你必须链接您的 DLL 与 Nafxcwd.lib 或 Nafxcw.lib 和名为 Libcmt.lib 的 C 运行时版本。 这些库之前是预先生成的，并且可能是通过在运行 Visual C++ 安装程序时指定它们安装的。  
  
## <a name="sample-code"></a>代码示例  
 有关完整示例，请参阅 MFC 高级概念示例程序 DLLScreenCap。 以下是此示例中要注意的一些有趣事项：  
  
-   DLL 的编译器标志与应用程序的不同。  
  
-   DLL 的链接线和 .DEF 文件与应用程序的不同。  
  
-   使用 DLL 的应用程序不必使用 C++。  
  
-   应用程序和 DLL 之间的接口是 C 或 C++ 可使用以及使用 DLLScreenCap.def 导出的 API。  
  
 下面的示例演示在正则表达式 MFC 静态链接到 MFC 的 DLL 中定义的 API。 在此示例中，声明将封闭在 C++ 用户的 `extern "C" { }` 块中。 这有许多好处。 首先，它使您的 DLL API 可由非 C++ 客户端应用程序使用。 其次，它减少了 DLL 开销，原因是 C++ 名称重整不会应用于导出的名称。 最后，它使显式添加到 .DEF 文件（以便按顺序导出）更方便，不必担心名称重整。  
  
```  
#ifdef __cplusplus  
extern "C" {  
#endif  /* __cplusplus */  
 
struct TracerData  
{  
    BOOL bEnabled;  
    UINT flags;  
};  
 
BOOL PromptTraceFlags(TracerData FAR* lpData);

 
#ifdef __cplusplus  
}  
#endif  
```  
  
 API 使用的结构不是从 MFC 类派生的，是在 API 标头中定义的。 这将降低 DLL 和应用程序之间接口的复杂性并使 DLL 可由 C 程序使用。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

