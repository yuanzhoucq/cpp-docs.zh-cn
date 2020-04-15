---
title: TN028：区分上下文的帮助支持
ms.date: 11/04/2016
f1_keywords:
- vc.help
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
ms.openlocfilehash: 502edc837d7886dd60ab5107fb194c1490a76928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370333"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028：区分上下文的帮助支持

此注释描述在 MFC 中分配帮助上下文 ID 和其他帮助问题的规则。 上下文相关帮助支持需要 Visual C++ 中提供的帮助编译器。

> [!NOTE]
> 除实现使用 WinHelp 的上下文相关帮助之外，MFC 还支持使用 HTML 帮助。 有关此支持和 HTML 帮助编程的详细信息，请参阅[HTML 帮助：程序上下文敏感帮助](../mfc/html-help-context-sensitive-help-for-your-programs.md)。

## <a name="types-of-help-supported"></a>支持的帮助类型

在 Windows 应用程序中实现了两种上下文相关帮助。 第一种称为“F1 帮助”，包括基于当前活动的对象使用合适的上下文启动 WinHelp。 第二种是“Shift+ F1”模式。 在此模式下，鼠标光标将更改为帮助光标，而用户继续单击对象。 此时，WinHelp 将启动以为用户单击的对象提供帮助。

Microsoft 基础类实现这两种形式的帮助。 此外，框架支持两条简单的帮助命令、帮助索引和使用帮助。

## <a name="help-files"></a>帮助文件

Microsoft 基础类假定有一个“帮助”文件。 “帮助”文件的名称和路径必须与应用程序的相同。 例如，如果可执行文件为 C:\MyApplication\MyHelp.exe，则帮助文件必须为 C:\MyApplication\MyHelp.hlp。 通过[CWinApp 类](../mfc/reference/cwinapp-class.md)的*m_pszHelpFilePath*成员变量设置路径。

## <a name="help-context-ranges"></a>帮助上下文范围

MFC 的默认实现需要程序遵循有关帮助上下文 ID 分配的一些规则。 这些规则是分配给特定控件的 ID 范围。 您可通过为各种帮助相关成员函数提供不同的实现来重写这些规则。

```
0x00000000 - 0x0000FFFF : user defined
0x00010000 - 0x0001FFFF : commands (menus/command buttons)
0x00010000 + ID_
(note: 0x18000-> 0x1FFFF is the practical range since command IDs are>=0x8000)
0x00020000 - 0x0002FFFF : windows and dialogs
0x00020000 + IDR_
(note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)
0x00030000 - 0x0003FFFF : error messages (based on error string ID)
0x00030000 + IDP_
0x00040000 - 0x0004FFFF : special purpose (non-client areas)
0x00040000 + HitTest area
0x00050000 - 0x0005FFFF : controls (those that are not commands)
0x00040000 + IDW_
```

## <a name="simple-help-commands"></a>简单的“帮助”命令

Microsoft 基础类实现了两条简单的“帮助”命令：

- [由 CWinApp 实现的ID_HELP_INDEX：：在帮助索引上](../mfc/reference/cwinapp-class.md#onhelpindex)

- [由 CWinApp 实现的ID_HELP_USING：在帮助使用](../mfc/reference/cwinapp-class.md#onhelpusing)

第一条命令显示应用程序的帮助索引。 第二条命令显示有关使用 WinHelp 程序的用户帮助。

## <a name="context-sensitive-help-f1-help"></a>上下文相关帮助（F1 帮助）

F1 键通常通过放置在主窗口的加速器表中的加速器转换为 ID 为 ID_HELP的命令。 ID_HELP命令也可以由主窗口或对话框上 ID 为 ID_HELP的按钮生成。

无论ID_HELP命令的生成方式如何，它都会作为常规命令进行路由，直到到达命令处理程序。 有关 MFC 命令路由体系结构的详细信息，请参阅[技术说明 21](../mfc/tn021-command-and-message-routing.md)。 如果应用程序启用了帮助，[则 cWinApp：：onHelp](../mfc/reference/cwinapp-class.md#onhelp)将处理ID_HELP命令。 应用程序对象将收到帮助消息，然后正确路由命令。 由于默认命令路由不适合确定最特定的上下文，因此这是必需的。

`CWinApp::OnHelp` 将尝试按以下顺序启动 WinHelp：

1. 使用帮助 ID 检查有效的 `AfxMessageBox` 调用。 如果消息框当前处于活动状态，则将使用适合消息框的上下文启动 WinHelp。

1. 向活动窗口发送一条 WM_COMMANDHELP 消息。 如果该窗口未通过启动 WinHelp 来响应，则之后将向该窗口的上级发送相同的消息，直到处理该消息或当前窗口为顶级窗口。

1. 向主窗口发送一条 ID_DEFAULT_HELP 命令。 这将调用默认帮助。 此命令一般将映射到 `CWinApp::OnHelpIndex`。

要全局覆盖默认 ID 基本值（例如命令的 0x10000 和对于对话框等资源 0x20000），应用程序应覆盖[CWinApp：：WinHelp](../mfc/reference/cwinapp-class.md#winhelp)。

若要重写此功能和确定帮助上下文的方式，您应处理 WM_COMMANDHELP 消息。 您可能希望相比框架提供更多特定帮助路由，因为框架深入程度仅与当前 MDI 子窗口一样。 您还可能想要为特定窗口或对话提供更具体的帮助，可能基于对话中对象或活动控件的当前内部状态。

## <a name="wm_commandhelp"></a>WM_COMMANDHELP

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)
```

WM_COMMANDHELP 是活动窗口在请求“帮助”时收到的私有 Windows MFC 消息。 当窗口收到此消息后，它可能使用与窗口的内部状态匹配的上下文调用 `CWinApp::WinHelp`。

*lParam*<br/>
包含当前可用的帮助上下文。 如果未确定帮助上下文，*则 lParam*为零。 的`OnCommandHelp`实现可以使用*lParam*中的上下文 ID 来确定不同的上下文，也可以将其传递给`CWinApp::WinHelp`。

*wParam*<br/>
未使用，将为零。

如果`OnCommandHelp`函数调用`CWinApp::WinHelp`，则应返回**TRUE**。 返回**TRUE**将停止此命令路由到其他类和其他窗口。

## <a name="help-mode-shiftf1-help"></a>帮助模式（Shift+F1 帮助）

这是上下文相关帮助的第二种形式。 通常，将通过按 Shift+F1 或通过菜单/工具栏进入此模式。 它将作为命令 (ID_CONTEXT_HELP) 实现。 当模式对话框或菜单处于活动状态时，消息筛选器挂钩不会用于转换此命令，因此此命令仅当应用程序执行主消息泵 (`CWinApp::Run`) 时才可供用户使用。

在进入此模式后，“帮助”鼠标光标将显示在应用程序所有区域上，即使应用程序在区域（如窗口周围的调整大小边框）内正常显示其自己的光标也是如此。 用户可以使用鼠标或键盘选择命令。 将显示与命令有关的“帮助”，而不是执行命令。 此外，用户可以单击屏幕上的可见对象（如工具栏上的按钮），该对象的“帮助”将显示。 此模式的“帮助”由 `CWinApp::OnContextHelp` 提供。

在此循环执行的过程中，所有键盘输入将不活动，访问菜单的键除外。 此外，仍将通过 `PreTranslateMessage` 执行命令转换，以允许用户按快捷键并接收有关命令的帮助。

如果`PreTranslateMessage`函数中发生的特定转换或操作不应在 SHIFT_F1 帮助模式期间发生，则应在执行这些操作之前检查 m_bHelpMode`CWinApp`*成员。* 例如，在调用 `CDialog` 之前，`PreTranslateMessage` 的 `IsDialogMessage` 实现将检查此成员。 这将在 Shift+F1 模式下禁用无模式对话框上的“对话框导航”键。 此外，仍将在此循环期间调用 `CWinApp::OnIdle`。

如果用户从菜单中选择命令，则会将其处理为有关该命令的帮助（通过 WM_COMMANDHELP，请参见下文）。 如果用户单击应用程序窗口的可见区域，则将确定单击是非工作区单击还是工作区单击。 `OnContextHelp` 会自动处理非工作区单击到工作区单击的映射。 如果它是工作区单击，则它之后将向单击的窗口发送 WM_HELPHITTEST。 如果该窗口返回一个非零值，则该值将用作帮助上下文。 如果返回零，则 `OnContextHelp` 将尝试父窗口（如果失败，则将尝试该窗口的父级，以此类推）。 如果无法确定帮助上下文，则默认是向主窗口发送ID_DEFAULT_HELP命令，主窗口（通常）映射到`CWinApp::OnHelpIndex`。

## <a name="wm_helphittest"></a>WM_HELPHITTEST

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

WM_HELPHITTEST 是单击的活动窗口在 Shift+F1 帮助模式期间收到的 MFC 私有 Windows 消息。 当窗口收到此消息时，它将返回一个**DWORD**帮助 ID 供 WinHelp 使用。

LOWORD（lParam） 包含 X 轴设备坐标，其中鼠标相对于窗口的工作区单击。

HIWORD（lParam）包含 Y 轴坐标。

*wParam*<br/>
未使用，将为零。 如果返回值不为零，则将使用相应上下文调用 WinHelp。 如果返回值为零，则将在父窗口中查询帮助。

在许多情况下，您可以利用您可能已具有的命中测试代码。 有关处理WM_HELPHITTEST消息`CToolBar::OnHelpHitTest`的示例，请参阅 的实现（代码利用了 在 中的`CControlBar`按钮和工具提示中使用的命中测试代码）。

## <a name="mfc-application-wizard-support-and-makehm"></a>MFC 应用程序向导支持和 MAKEHM

MFC 应用程序向导将创建生成帮助文件所需的文件（.cnt 文件和 .hpj 文件）。 它还包括 Microsoft 帮助编译器接受的一些预先生成 .rtf 文件。 许多主题已完成，但一些主题可能需要为特定应用程序进行修改。

名为 MAKEHM 的实用工具将支持“帮助映射”文件的自动创建。 MAKEHM 实用工具可以将应用程序的 RESOURCE.H 文件转换为帮助映射文件。 例如：

```
#define IDD_MY_DIALOG   2000
#define ID_MY_COMMAND   150
```

将转换为：

```
HIDD_MY_DIALOG    0x207d0
HID_MY_COMMAND    0x10096
```

此格式与帮助编译器的工具兼容，该设备使用主题名称（左侧的符号）映射上下文 ID（右侧的数字）。

MAKEHM 的源代码在 MFC 编程实用程序示例[MAKEHM](../overview/visual-cpp-samples.md)中可用。

## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>在运行 MFC 应用程序向导后添加帮助支持

将帮助添加到应用程序的最佳方式是，在创建应用程序之前，检查 MFC 应用程序向导的“高级功能”页上的“上下文相关帮助”选项。 这样一来，MFC 应用程序向导将自动将必需的消息映射条目添加到 `CWinApp` 派生类以支持帮助。

## <a name="help-on-message-boxes"></a>消息框上的“帮助”

通过 `AfxMessageBox` 函数（`MessageBox` Windows API 的包装器）支持消息框上的“帮助”（有时称为“警报”）。

`AfxMessageBox` 有两种形式，一种与字符串 ID 一起使用，另一种与指向字符串 (`LPCSTR`) 的指针一起使用：

```
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```

这两种情况下，均具有可选帮助 ID。

第一种情况下，nIDHelp 的默认值为 0，这指示此消息框无“帮助”。 如果用户在消息框处于活动状态时按 F1，则用户将收不到“帮助”（即使应用程序支持“帮助”也是如此）。 如果这不是需要的，则应为 nIDHelp 提供帮助 ID。

在第二种情况下，nIDHelp 的默认值为 -1，这指示帮助 ID 与 nIDPrompt 相同。 当然，“帮助”仅当应用程序启用“帮助”时起作用）。 如果您希望消息框没有任何“帮助”支持，则应为 nIDHelp 提供 0。 如果您希望消息启用“帮助”，但需要不同于 nIDPrompt 的帮助 ID，则只需为 nIDHelp 提供一个与 nIDPrompt 的帮助 ID 不同的正值。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
