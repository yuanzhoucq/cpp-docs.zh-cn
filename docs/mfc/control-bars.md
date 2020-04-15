---
title: 控件条
ms.date: 11/04/2016
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
ms.openlocfilehash: ceae20c89d9a6d3f4393f838b3594938107785f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353573"
---
# <a name="control-bars"></a>控件条

“控件条”是工具栏、状态栏和对话栏的统称。 MFC`CToolBar`类`CStatusBar` `CDialogBar`、`COleResizeBar`和`CReBar`派生自[CControlBar](../mfc/reference/ccontrolbar-class.md)类，后者实现其公共功能。

控件条是显示多行控件的窗口，用户可以使用它来选择选项、执行命令或获取程序信息。 控件条的类型包括工具栏、对话栏和状态栏。

- 工具栏，在类[CToolBar 中](../mfc/reference/ctoolbar-class.md)

- 状态栏，在[CStatusBar](../mfc/reference/cstatusbar-class.md)类中

- 对话框栏，在类[CDialog 栏中](../mfc/reference/cdialogbar-class.md)

- 钢筋，在[CReBar](../mfc/reference/crebar-class.md)类中

> [!IMPORTANT]
> 自 MFC 版本 4.0 起，工具栏、状态栏和工具提示使用*在 comctl32.dll*中实现的系统功能而不是特定于 MFC 的前一个实现实现实现。 在 MFC 版本 6.0 中`CReBar`，还添加了 comctl32.dll 功能。

下面将简单介绍控件条类型。 有关详细信息，请参阅以下链接。

## <a name="control-bars"></a>控件条

控件条通过提供快速、一步式的命令操作，极大提升了程序的可用性。 `CControlBar` 类提供了所有工具栏、状态栏和对话栏的常见功能。 `CControlBar` 提供了用于在其父框架窗口中定位控件条的功能。 由于控件条通常是父框架窗口的子窗口，因此它是客户端视图或框架窗口的 MDI 客户端的“同级”。 控件条对象使用有关其父窗口的客户端矩形的信息来为自身定位。 然后它改变父级的其余客户端窗口矩形，以便客户端视图或 MDI 客户端窗口填充客户端窗口的其余部分。

> [!NOTE]
> 如果控制栏上的按钮没有**COMMAND**或**UPDATE_COMMAND_UI**处理程序，则框架将自动禁用该按钮。

## <a name="toolbars"></a>工具栏

工具栏是一个显示一行可执行命令的位图化按钮的控件条。 按一个工具栏按钮相当于选择一个菜单项；如果某个菜单项具有与所按的工具栏按钮相同的 ID，则会调用映射到该菜单项的同一处理程序。 可将工具栏按钮配置为使用与普通按钮、单选按钮或复选框相同的显示和操作方式。 工具栏通常与框架窗口的顶部对齐，但 MFC 工具栏可以“停靠”到其父窗口的任何一侧或在其微型框架窗口中浮动。 工具栏也可以“浮动”，您可以使用鼠标更改它的大小并进行拖动。 当用户将鼠标移到工具栏的按钮上方时，工具栏也可以显示工具提示。 工具提示是一个小型弹出窗口，用于简要介绍按钮的作用。

> [!NOTE]
> 从 MFC 版本 4.0 起[，CToolBar](../mfc/reference/ctoolbar-class.md)类使用 Windows 工具栏通用控件。 A`CToolBar`包含[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)。 但仍支持较早的工具栏。 请参阅文章[工具栏](../mfc/mfc-toolbar-implementation.md)。

## <a name="status-bars"></a>状态栏

状态栏是包含文本输出窗格或“指示器”的控件条。 输出窗格通常用作消息行和状态指示器。 消息行示例包括命令帮助消息行，这些消息行简短解释了由 MFC 应用程序向导创建的默认状态栏的最左侧窗格中所选的菜单或工具栏命令。 状态指示器示例包括 Scroll Lock、Num Lock 和其他键。 状态栏通常与框架窗口的底部对齐。 请参阅类[CStatusBar](../mfc/reference/cstatusbar-class.md)和类[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)。

## <a name="dialog-bars"></a>对话栏

对话栏是一个基于对话框模板资源的控件条，具有无模式对话框的功能。 对话栏可以包含 Windows 控件、自定义控件或 ActiveX 控件。 与在对话框中一样，用户可以使用 Tab 键在控件之间切换。 对话栏可以与框架窗口的顶部、底部、左侧或右侧对齐，也能在自己的框架窗口中浮动。 请参阅类[CDialogBar](../mfc/reference/cdialogbar-class.md)。

## <a name="rebars"></a>Rebar

[钢筋](../mfc/using-crebarctrl.md)是一种控件栏，它为钢筋控件提供停靠、布局、状态和持久性信息。 Rebar 对象可以包含各种子窗口，通常为其他控件，包括编辑框、工具栏和列表框。 Rebar 对象可以在指定位图上显示其子窗口。 它可以自动调整大小，也可以通过单击或拖动其手柄栏来手动调整其大小。 请参阅[CReBar](../mfc/reference/crebar-class.md)类。

## <a name="see-also"></a>另请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)
