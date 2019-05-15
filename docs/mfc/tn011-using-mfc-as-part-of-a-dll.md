---
title: TN011:将 MFC 作为 DLL 的一部分使用
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 753612fae101708dd4f8294db121980b62af30b3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65610943"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011:将 MFC 作为 DLL 的一部分使用

此说明描述规则 MFC Dll，这样即可使用 MFC 库作为 Windows 动态链接库 (DLL) 的一部分。 此说明假定您已熟悉 Windows DLL 及其生成方式。 有关 MFC 扩展 Dll，使用它创建扩展 MFC 库，请参阅[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)。

## <a name="dll-interfaces"></a>DLL 接口

MFC 的规则 Dll 假定应用程序和 DLL 之间的接口类似于 C 的函数或显式导出的类中指定。 MFC 类接口无法导出。

如果 DLL 和应用程序要使用 MFC，则请选择是使用共享版本的 MFC 库还是静态链接到这些库的副本。 应用程序和 DLL 可能都会使用 MFC 库的标准版本之一。

MFC 的规则 Dll 有若干优点：

- 使用 DLL 的应用程序不必使用 MFC，并且不必是 Visual C++ 应用程序。

- 静态链接到 MFC 的规则 MFC dll，DLL 的大小取决于仅 MFC 和 C 运行时例程的使用和链接。

- 动态链接到 MFC 的规则 MFC dll，节省的内存使用共享的 MFC 版本可能很大。 但是，必须将分发共享的 Dll、 Mfc\<*版本*>.dll 和 Msvvcrt\<*版本*>.dll 与您的 DLL。

- DLL 设计独立于类的实现方式之外。 您的 DLL 设计仅导出到需要的 API。 因此，如果实现发生更改，规则 MFC Dll 是仍有效。

- 静态链接到 MFC 的规则 MFC DLL 和应用程序使用 MFC，是否想 MFC 于 DLL 或进行相反的不同版本的应用程序没有问题。 由于 MFC 库将静态链接到每个 DLL 或 EXE，因此您具有哪一版本没有任何问题。

## <a name="api-limitations"></a>API 限制

一些 MFC 功能不适用于 DLL 版本，原因是技术方面的限制或者这些服务一般都是应用程序提供的。 利用当前版本的 MFC，唯一不适用的功能是 `CWinApp::SetDialogBkColor`。

## <a name="building-your-dll"></a>生成您的 DLL

编译静态链接到 MFC，符号的规则 MFC Dll 时`_USRDLL`和`_WINDLL`必须定义。 你的 DLL 代码还必须使用下列编辑器开关进行编译：

- **/ D_WINDLL**表示编译为 dll

- **/ D_USRDLL**指定您将生成规则 MFC DLL

此外必须定义这些符号并编译动态链接到 MFC 的规则 MFC Dll 时使用这些编译器开关。 此外，必须定义 `_AFXDLL` 符号，并且必须使用以下内容编译 DLL 代码：

- **/ D_AFXDLL**指定您将生成动态链接到 MFC 的规则 MFC DLL

必须显式导出应用程序和 DLL 之间的接口 (API)。 建议您将接口定义为低带宽，并且如果可以只使用 C 接口。 直接 C 接口更易于维护更复杂的 C++ 类。

将 API 放在 C 文件和 C++ 文件均可包含的单独标头中。 请参阅 MFC 高级概念示例中的 screencap.h [DLLScreenCap](../overview/visual-cpp-samples.md)有关的示例。 若要导出函数，请在模块定义文件 (.DEF) 的 `EXPORTS` 部分中输入它们，或将 `__declspec(dllexport)` 包含在您的函数定义中。 使用 `__declspec(dllimport)` 将这些函数导入客户端可执行文件中。

必须将 AFX_MANAGE_STATE 宏添加动态链接到 MFC 的规则 MFC Dll 中的所有导出函数的开头。 此宏会将当前模块状态设置为 DLL 的模块状态。 若要使用该宏，请将以下代码行添加到从 DLL 导出的函数的开始处：

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain -> DllMain

MFC 库定义的标准 Win32`DllMain`初始化的入口点你[CWinApp](../mfc/reference/cwinapp-class.md)派生的对象，如典型的 MFC 应用程序中所示。 将中的所有 DLL 特定初始化都放[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)如典型的 MFC 应用程序中所示的方法。

请注意， [cwinapp:: Run](../mfc/reference/cwinapp-class.md#run)机制不适用于 DLL，因为应用程序拥有主消息泵。 如果 DLL 显示无模式对话框或有其自己的主框架窗口，应用程序的主消息泵必须调用调用的 DLL 导出的例程[CWinApp::PreTranslateMessage](../mfc/reference/cwinapp-class.md#pretranslatemessage)。

有关此函数的使用，请参阅 DLLScreenCap 示例。

`DllMain` MFC 提供了将调用的函数[CWinApp::ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)类派生自方法`CWinApp`卸载 DLL 之前。

## <a name="linking-your-dll"></a>链接您的 DLL

静态链接到 MFC 的规则 MFC dll，必须链接您的 DLL 与 Nafxcwd.lib 或 Nafxcw.lib 以及与名为 Libcmt.lib 的 C 运行时版本。 这些库之前是预先生成的，并且可能是通过在运行 Visual C++ 安装程序时指定它们安装的。

## <a name="sample-code"></a>代码示例

有关完整示例，请参阅 MFC 高级概念示例程序 DLLScreenCap。 以下是此示例中要注意的一些有趣事项：

- DLL 的编译器标志与应用程序的不同。

- DLL 的链接线和 .DEF 文件与应用程序的不同。

- 使用 DLL 的应用程序不必使用 C++。

- 应用程序和 DLL 之间的接口是 C 或 C++ 可使用以及使用 DLLScreenCap.def 导出的 API。

下面的示例演示了正则表达式以静态方式链接到 MFC 的 MFC DLL 中定义的 API。 在此示例中，声明将封闭在 C++ 用户的 `extern "C" { }` 块中。 这有许多好处。 首先，它使您的 DLL API 可由非 C++ 客户端应用程序使用。 其次，它减少了 DLL 开销，原因是 C++ 名称重整不会应用于导出的名称。 最后，它使显式添加到 .DEF 文件（以便按顺序导出）更方便，不必担心名称重整。

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

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
