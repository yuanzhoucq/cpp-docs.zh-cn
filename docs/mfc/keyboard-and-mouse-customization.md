---
title: 键盘和鼠标自定义
ms.date: 11/19/2018
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
ms.openlocfilehash: 262555b060f226a86438a2189eda44d83c55d5a2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621508"
---
# <a name="keyboard-and-mouse-customization"></a>键盘和鼠标自定义

MFC 允许应用程序用户自定义其处理键盘和鼠标输入的方式。 用户可通过为命令分配键盘快捷键来自定义键盘输入。 用户还可通过选择应在用户双击应用程序特定窗口内时执行的命令来自定义鼠标输入。 本主题介绍如何为您的应用程序自定义输入。

在 "**自定义**" 对话框中，用户可以更改鼠标和键盘的自定义控件。 若要显示此对话框，用户可在 "**视图**" 菜单上指向 "**自定义**"，然后单击 "**工具栏和停靠**"。 在对话框中，用户可以单击 "**键盘**" 选项卡或 "**鼠标**" 选项卡。

## <a name="keyboard-customization"></a>键盘自定义

下图显示了 "**自定义**" 对话框的 "**键盘**" 选项卡。

![“自定义”对话框中的“键盘”选项卡](../mfc/media/mfcnextkeyboardtab.png "“自定义”对话框中的“键盘”选项卡") <br/>
键盘自定义选项卡

用户将与键盘选项卡交互以为命令分配一个或多个键盘快捷键。 可用命令在选项卡的左侧列出。用户可以从菜单中选择任何可用命令。 仅菜单命令与键盘快捷键相关。 用户输入新的快捷方式后，"**分配**" 按钮将变为 "已启用"。 当用户单击此按钮时，应用程序会将选定命令与该快捷键关联。

右列的列表框中将列出当前分配的所有键盘快捷键。 用户还可选择单独的快捷键并删除它们，或为应用程序重置所有映射。

如果要在应用程序中支持此自定义，则必须创建一个[CKeyboardManager](reference/ckeyboardmanager-class.md)对象。 若要创建 `CKeyboardManager` 对象，请调用函数[CWinAppEx：： InitKeyboardManager](reference/cwinappex-class.md#initkeyboardmanager)。 此方法将创建并初始化一个键盘管理器。 如果手动创建键盘管理器，则仍必须调用 `CWinAppEx::InitKeyboardManager` 初始化键盘管理器。

如果使用向导创建应用程序，则向导将初始化键盘管理器。 在应用程序初始化键盘管理器后，框架会将 "**键盘**" 选项卡添加到 "**自定义**" 对话框。

## <a name="mouse-customization"></a>鼠标自定义

下图显示了 "**自定义**" 对话框的 "**鼠标**" 选项卡。

![“自定义”对话框中的“鼠标”选项卡](../mfc/media/mfcnextmousetab.png "“自定义”对话框中的“鼠标”选项卡") <br/>
鼠标自定义选项

用户将与此选项卡交互，以为鼠标双击操作分配菜单命令。 用户将从窗口左侧选择视图，然后使用右侧的控件将命令与双击操作关联。 用户单击 "**关闭**" 后，每当用户双击视图中的任意位置时，应用程序就会执行关联的命令。

默认情况下，当您使用向导创建应用程序时，不会启用鼠标自定义。

#### <a name="to-enable-mouse-customization"></a>启用鼠标自定义

1. 通过调用[CWinAppEx：： InitMouseManager](reference/cwinappex-class.md#initmousemanager)初始化[CMouseManager](reference/cmousemanager-class.md)对象。

1. 使用[CWinAppEx：： GetMouseManager](reference/cwinappex-class.md#getmousemanager)获取指向鼠标管理器的指针。

1. 使用[CMouseManager：： AddView](reference/cmousemanager-class.md#addview)方法将视图添加到鼠标管理器。 针对要添加到鼠标管理器的每个视图执行此操作。

在应用程序初始化鼠标管理器后，框架会将 "**鼠标**" 选项卡添加到 "**自定义**" 对话框。 如果未添加任何视图，则访问此选项将导致未经处理的异常。 创建视图列表后，用户可以使用 "**鼠标**" 选项卡。

当您将新视图添加到鼠标管理器后，您将为其提供一个唯一 ID。 如果要支持窗口的鼠标自定义，则必须处理 WM_LBUTTONDBLCLICK 消息并调用[CWinAppEx：： OnViewDoubleClick](reference/cwinappex-class.md#onviewdoubleclick)函数。 当您调用此函数时，其中一个参数就是该窗口的 ID。 程序员负责记录 ID 号以及与其关联的对象。

## <a name="security-concerns"></a>安全问题

如[用户定义的工具](user-defined-tools.md)中所述，用户可以将用户定义的工具 ID 与双击事件关联。 当用户双击视图时，应用程序将寻找与关联 ID 匹配的用户工具。 如果应用程序找到匹配的工具，则它将执行该工具。 如果应用程序无法找到匹配的工具，则它将向双击的视图发送带有 ID 的 WM_COMMAND 消息。

自定义的设置存储在注册表中。 通过编辑注册表，攻击者可将有效的用户工具 ID 替换为任意命令。 当用户双击视图时，视图将处理攻击者植入的命令。 这可能导致意外和潜在的危险行为。

此外，此类攻击可以绕开用户界面安全措施。 例如，假定应用程序已禁用打印。 也就是说，在其用户界面中，"**打印**" 菜单和按钮不可用。 通常这将防止应用程序打印。 但如果攻击者编辑注册表，则用户现在可通过双击视图、绕过不可用的用户界面元素直接发送打印命令。

若要防止此类攻击，请向应用程序命令处理程序添加代码，以在命令执行前验证命令是否有效。 请勿依赖用户界面来阻止命令发送到应用程序。

## <a name="see-also"></a>另请参阅

[MFC 自定义](customization-for-mfc.md)<br/>
[CKeyboardManager 类](reference/ckeyboardmanager-class.md)<br/>
[CMouseManager 类](reference/cmousemanager-class.md)<br/>
[自定义的安全隐患](security-implications-of-customization.md)
