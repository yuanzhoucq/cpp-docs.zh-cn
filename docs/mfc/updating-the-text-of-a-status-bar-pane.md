---
title: 更新状态栏窗格的文本
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
ms.openlocfilehash: 723046fc1721cc46608e00f19a4431ef081be13d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366691"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>更新状态栏窗格的文本

本文说明如何更改显示在 MFC 状态栏窗格中的文本。 状态栏（[类 CStatusBar](../mfc/reference/cstatusbar-class.md)的窗口对象）包含多个"窗格"。 每个窗格都是状态栏中可用于显示信息的矩形区域。 例如，很多应用程序在最右侧的窗格中显示了 CAPS LOCK、NUM LOCK 和其他键的状态。 应用程序通常还在最左侧的窗格（窗格 0）中显示信息性文本，该窗格有时称为“消息窗格”。 例如，默认 MFC 状态栏使用消息窗格来显示用来说明当前选择的菜单项或工具栏按钮的字符串。 [状态栏](../mfc/status-bar-implementation-in-mfc.md)中的图显示应用程序向导创建的 MFC 应用程序的状态栏。

默认情况下，在创建窗格时，MFC 不启用 `CStatusBar` 窗格。 要激活窗格，必须对状态栏中的每个窗格使用ON_UPDATE_COMMAND_UI宏并更新窗格。 由于窗格不会发送 WM_COMMAND 信息（它们与工具栏按钮不同），必须手动键入代码。

例如，假设某个窗格将 `ID_INDICATOR_PAGE` 设为其命令标识符，并且在文档中包含当前页码。 以下过程说明如何在状态栏中创建新窗格。

### <a name="to-make-a-new-pane"></a>制作新窗格

1. 定义窗格的命令 ID。

   在 **"视图"** 菜单上，单击"**资源视图**"。 右键单击项目资源，然后单击 **"资源符号**"。 在“资源符号”对话框中，单击 `New`。 键入命令 ID 名称：例如，`ID_INDICATOR_PAGE`。 为 ID 指定值或接受“资源符号”对话框建议的值。 例如，对于 `ID_INDICATOR_PAGE`，请接受默认值。 关闭“资源符号”对话框。

1. 定义要显示在窗格中的默认字符串。

   打开资源视图后，在列出应用程序资源类型的窗口中双击**字符串表**。 打开 **"字符串表"** 编辑器后，从 **"插入**"菜单中选择 **"新建字符串**"。 选择窗格的命令 ID（例如`ID_INDICATOR_PAGE`），然后键入默认字符串值，如"页"。 关闭字符串编辑器。 （您需要默认字符串来避免编译器错误。）

1. 将窗格添加到*指示器*数组。

   在文件中 MAINFRM 中。CPP，找到*指标*数组。 此数组以从左到右的顺序列出了所有状态栏的指示符的命令 ID。 在数组中的合适的点上，输入窗格的命令 ID，如此处为 `ID_INDICATOR_PAGE` 所示的：

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

建议在窗格中显示文本的方法是在窗格的更新处理程序函数中`SetText`调用类`CCmdUI`的成员函数。 例如，您可能希望设置包含当前页码的整数变量*m_nPage，* 并用于`SetText`将窗格的文本设置为该数字的字符串版本。

> [!NOTE]
> 建议`SetText`使用此方法。 可以通过调用 `CStatusBar` 成员函数 `SetPaneText` 在稍微低一点的级别中执行此任务。 尽管如此，您仍需一个更新处理程序。 如果窗格没有此类处理程序，MFC 将自动禁用窗格，并清除其内容。

以下过程显示如何使用更新处理程序函数在窗格中显示文本。

#### <a name="to-make-a-pane-display-text"></a>制作窗格显示文本

1. 为命令添加命令更新处理程序。

   为处理程序手动添加原型，如此处为 `ID_INDICATOR_PAGE`（在 MAINFRM.H 中）所示的：

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. 在合适的 .CPP 文件中，添加处理程序的定义，如此处为 `ID_INDICATOR_PAGE`（在 MAINFRM.CPP 中）所示的：

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   此处理程序的最后三行是显示文本的代码。

1. 在相应的消息映射中，添加ON_UPDATE_COMMAND_UI宏，如下所示`ID_INDICATOR_PAGE`（在 MAINFRM 中）。CPP）：

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

定义*m_nPage*成员变量（类`CMainFrame`）的值后，此技术会导致在空闲处理期间页码以与应用程序更新其他指标相同的方式显示在窗格中。 如果*m_nPage*更改，则显示在下一个空闲循环期间更改。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [更新用户界面对象（如何在程序条件更改时更新工具栏按钮和菜单项）](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>另请参阅

[MFC 中的状态栏实现](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar 类](../mfc/reference/cstatusbar-class.md)
