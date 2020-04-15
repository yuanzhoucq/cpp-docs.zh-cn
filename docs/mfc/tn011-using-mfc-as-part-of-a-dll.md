---
title: TN011：将 MFC 作为 DLL 的一部分使用
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 0f4d4e2ed76a0fa5f8f775345fc672a1df055a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370427"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011：将 MFC 作为 DLL 的一部分使用

本说明介绍常规 MFC DLL，它允许您将 MFC 库用作 Windows 动态链接库 （DLL） 的一部分。 此说明假定您已熟悉 Windows DLL 及其生成方式。 有关 MFC 扩展 DLL 的信息（您可以使用该扩展创建 MFC 库，请参阅[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)）。

## <a name="dll-interfaces"></a>DLL 接口

常规 MFC DLL 假定应用程序之间的接口，DLL 在 C 样的函数或显式导出的类中指定。 MFC 类接口无法导出。

如果 DLL 和应用程序要使用 MFC，则请选择是使用共享版本的 MFC 库还是静态链接到这些库的副本。 应用程序和 DLL 可能都会使用 MFC 库的标准版本之一。

常规 MFC DLL 有几个优点：

- 使用 DLL 的应用程序不必使用 MFC，并且不必是 Visual C++ 应用程序。

- 对于静态链接到 MFC 的常规 MFC DLL，DLL 的大小仅取决于使用和链接的 MFC 和 C 运行时例程。

- 使用动态链接到 MFC 的常规 MFC DLL，使用 MFC 的共享版本可以节省内存。 但是，您必须将共享的 DLL、mfc\<*版本*>.dll 和\<msvvcrt*版本*>.dll 分发，并与您的 DLL 一起分发。

- DLL 设计独立于类的实现方式之外。 您的 DLL 设计仅导出到需要的 API。 因此，如果实现发生更改，常规 MFC DLL 仍然有效。

- 对于静态链接到 MFC 的常规 MFC DLL，如果 DLL 和应用程序都使用 MFC，则应用程序不需要与 DLL 不同版本的 MFC 出现问题，反之亦然。 由于 MFC 库将静态链接到每个 DLL 或 EXE，因此您具有哪一版本没有任何问题。

## <a name="api-limitations"></a>API 限制

一些 MFC 功能不适用于 DLL 版本，原因是技术方面的限制或者这些服务一般都是应用程序提供的。 利用当前版本的 MFC，唯一不适用的功能是 `CWinApp::SetDialogBkColor`。

## <a name="building-your-dll"></a>生成您的 DLL

编译静态链接到 MFC 的常规 MFC DLL 时，必须定义`_USRDLL`符号`_WINDLL`和符号。 你的 DLL 代码还必须使用下列编辑器开关进行编译：

- **/D_WINDLL**表示编译用于 DLL

- **/D_USRDLL**指定您正在构建常规 MFC DLL

编译动态链接到 MFC 的常规 MFC DLL 时，还必须定义这些符号并使用这些编译器开关。 此外，必须定义 `_AFXDLL` 符号，并且必须使用以下内容编译 DLL 代码：

- **/D_AFXDLL**指定您正在构建一个定期 MFC DLL，该 DLL 动态链接到 MFC

必须显式导出应用程序和 DLL 之间的接口 (API)。 建议您将接口定义为低带宽，并且如果可以只使用 C 接口。 直接 C 接口更易于维护更复杂的 C++ 类。

将 API 放在 C 文件和 C++ 文件均可包含的单独标头中。 有关示例，请参阅 MFC 高级概念示例[DLLScreenCap](../overview/visual-cpp-samples.md)中的头 ScreenCap.h。 若要导出函数，请在模块定义文件 (.DEF) 的 `EXPORTS` 部分中输入它们，或将 `__declspec(dllexport)` 包含在您的函数定义中。 使用 `__declspec(dllimport)` 将这些函数导入客户端可执行文件中。

您必须在定期 MFC DLL 中动态链接到 MFC 的所有导出函数的开头添加AFX_MANAGE_STATE宏。 此宏会将当前模块状态设置为 DLL 的模块状态。 若要使用该宏，请将以下代码行添加到从 DLL 导出的函数的开始处：

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>温曼 -> 德曼

MFC 库定义标准 Win32`DllMain`入口点，该入口点将[CWinApp](../mfc/reference/cwinapp-class.md)派生对象初始化为典型 MFC 应用程序中。 将所有特定于 DLL 的初始化放在[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)方法中，如在典型的 MFC 应用程序中。

请注意[，CWinApp：：运行](../mfc/reference/cwinapp-class.md#run)机制不适用于 DLL，因为应用程序拥有主消息泵。 如果您的 DLL 显示无模式对话框或自己的主框架窗口，则应用程序的主消息泵必须调用 DLL 导出的例程，该例程称为[CWinApp：:P重新翻译消息](../mfc/reference/cwinapp-class.md#pretranslatemessage)。

有关此函数的使用，请参阅 DLLScreenCap 示例。

MFC 提供的`DllMain`函数将调用类的[CWinApp：：exitInstance](../mfc/reference/cwinapp-class.md#exitinstance)方法，该方法派生自`CWinApp`DLL 之前。

## <a name="linking-your-dll"></a>链接您的 DLL

使用静态链接到 MFC 的常规 MFC DLL，您必须将 DLL 与 Nafxcwd.lib 或 Nafxcw.lib 以及名为 Libcmt.lib 的 C 运行时版本链接。 这些库之前是预先生成的，并且可能是通过在运行 Visual C++ 安装程序时指定它们安装的。

## <a name="sample-code"></a>代码示例

有关完整示例，请参阅 MFC 高级概念示例程序 DLLScreenCap。 以下是此示例中要注意的一些有趣事项：

- DLL 的编译器标志与应用程序的不同。

- DLL 的链接线和 .DEF 文件与应用程序的不同。

- 使用 DLL 的应用程序不必使用 C++。

- 应用程序和 DLL 之间的接口是 C 或 C++ 可使用以及使用 DLLScreenCap.def 导出的 API。

下面的示例演示了在常规 MFC DLL 中定义的 API，该 API 以静态方式链接到 MFC。 在此示例中，声明将封闭在 C++ 用户的 `extern "C" { }` 块中。 这有许多好处。 首先，它使您的 DLL API 可由非 C++ 客户端应用程序使用。 其次，它减少了 DLL 开销，原因是 C++ 名称重整不会应用于导出的名称。 最后，它使显式添加到 .DEF 文件（以便按顺序导出）更方便，不必担心名称重整。

```cpp
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

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
