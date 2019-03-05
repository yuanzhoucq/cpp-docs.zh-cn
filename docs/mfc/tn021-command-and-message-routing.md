---
title: TN021:命令和消息路由
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: ce8aa2013c8f2f351ca1028f0d6103135ba5ecd8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294390"
---
# <a name="tn021-command-and-message-routing"></a>TN021:命令和消息路由

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此说明描述命令路由和调度体系结构以及常规窗口消息路由中的高级的主题。

请参阅 Visual c + + 作介绍，在体系结构上的常规详细信息尤其是 Windows 消息、 控件通知和命令之间的区别。 本说明假定您非常熟悉打印文档中所述的问题，以及仅处理非常高级的主题。

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>命令路由和调度 MFC 1.0 功能发展到 MFC 2.0 体系结构

Windows 具有重载以提供的菜单命令、 快捷键和对话框控件通知的通知的 WM_COMMAND 消息。

MFC 1.0 基于的有点命令处理程序 (例如，"OnFileNew")，从而`CWnd`派生类来获取调用以响应特定 WM_COMMAND。 这粘附调用消息映射中，数据结构的同时，并且会导致空间非常高效命令机制。

MFC 1.0 还提供了将从命令消息的控件通知的其他功能。 命令都是一个 16 位 ID，有时称为命令 id。 命令通常从启动`CFrameWnd`（即，菜单中选择或已翻译的加速器） 和其他窗口的各种路由。

MFC 1.0 使用的有限的意义上实现的多文档界面 (MDI) 中的命令路由。 （MDI 框架窗口委派到其活动的 MDI 子窗口的命令。）

此功能已通用化并扩展在 MFC 2.0 中以允许命令来处理更多的对象 （而不仅仅是窗口对象）。 它提供了多个正式和可扩展的体系结构用于路由消息，并重用命令目标路由，用于仅不处理的命令，而且还可以用于更新用户界面对象 （如菜单项和工具栏按钮） 以反映当前命令的可用性.

## <a name="command-ids"></a>命令 ID

命令路由和绑定过程的说明，请参阅 Visual c + +。 [技术说明 20](../mfc/tn020-id-naming-and-numbering-conventions.md)包含 ID 命名的信息。

我们使用的命令 Id 的通用前缀"ID_"。 命令 Id 是 > = 0x8000。 消息行或状态栏将显示命令说明字符串是否存在具有相同的命令 id。 Id 的 STRINGTABLE 资源

在应用程序的资源，的命令 ID 可以将出现在多个位置：

- 在一个 STRINGTABLE 资源具有相同的 ID 作为消息行提示符。

- 可能是许多菜单资源中附加到调用相同的命令的菜单项。

- 在对话框按钮 GOSUB 命令中 （高级）。

在你的应用程序的源代码，的命令 ID 可以出现在多个位置：

- 在资源中。H （或其他主符号头文件） 来定义特定于应用程序的命令 Id。

- 可能是在用于创建工具栏的 ID 数组。

- 中的 ON_COMMAND 宏。

- 可能是在 ON_UPDATE_COMMAND_UI 宏。

目前，唯一需要的命令 Id 的 MFC 中的实现是 > = 0x8000 是 GOSUB 对话框/命令的实现。

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>使用对话框中的命令体系结构的 GOSUB 命令

路由和启用命令的命令体系结构适用于框架窗口、 菜单项、 工具栏按钮、 对话栏按钮、 其他控件条和其他设计用于更新需求和路由命令或到 main 中控件 Id 的用户界面元素命令目标 （通常主框架窗口）。 该主命令目标可能会将命令或控件通知路由到根据其他命令目标对象。

对话框 （模式或无模式） 可以受益于某些命令体系结构的功能，如果将对话框控件的控件 ID 分配给相应的命令 id。 对话框的支持不是自动进行的因此可能需要编写一些附加代码。

请注意，所有这些功能才能正常工作，命令 Id 应 > = 0x8000。 由于许多对话框都可能路由到同一个框架，共享的命令应 > = 0x8000，而在对话框中，特定非共享的 Idc 应为 < = 0x7FFF。

可以将普通按钮放置在正常模式对话框中进行设置为相应的命令 id。 该按钮的 IDC 当用户选择按钮时，对话框 （通常主框架窗口） 的所有者获取就像任何其他命令的命令。 这被称为 GOSUB 命令，因为它通常用来打开另一个对话框 (第一个对话框 GOSUB)。

您还可以调用该函数`CWnd::UpdateDialogControls`上您的对话框，并将它传递的主框架窗口的地址。 此函数将启用或禁用对话框控件基于是否具有命令处理程序的框架中。 调用此函数会自动为你的应用程序的空闲循环中的控件条，但必须调用该直接为您希望具有此功能的正常对话框。

## <a name="when-onupdatecommandui-is-called"></a>当调用 ON_UPDATE_COMMAND_UI

维护程序的所有菜单项的启用检查状态的时间可能会占用大量计算资源的问题。 一种常用技术是以启用/检查菜单项仅当用户选择弹出窗口。 MFC 2.0 实现`CFrameWnd`处理 WM_INITMENUPOPUP 消息并使用命令路由体系结构来确定菜单通过 ON_UPDATE_COMMAND_UI 处理程序的状态。

`CFrameWnd` 此外可以处理 WM_ENTERIDLE 消息来描述当前所选菜单项 （也称为消息行） 的状态栏上。

应用程序的菜单结构，编辑由 Visual c + +，用于表示在 WM_INITMENUPOPUP 时可用的潜在命令。 ON_UPDATE_COMMAND_UI 处理程序可以修改的状态或文本的菜单中，或有关 （如文件 MRU 列表或 OLE 谓词弹出菜单） 的高级用法，实际修改菜单结构在绘制菜单之前。

工具栏 （以及其他控件栏） 进行 ON_UPDATE_COMMAND_UI 处理相同排序应用程序时进入其空闲循环。 请参阅*类库参考*并[技术说明 31](../mfc/tn031-control-bars.md)的控件条的详细信息。

## <a name="nested-pop-up-menus"></a>嵌套的弹出菜单

如果使用嵌套的菜单结构，您将注意到，在两个不同的情况下调用弹出菜单中的第一个菜单项的 ON_UPDATE_COMMAND_UI 处理程序。

首先，它被调用的自身的弹出菜单。 这是必需的因为弹出菜单不具有的 Id，并且我们使用的弹出菜单的第一个菜单项的 ID 来指代整个弹出菜单。 在这种情况下， *m_pSubMenu*成员变量`CCmdUI`对象将为非 NULL，也将指向弹出菜单。

其次，调用弹出菜单中的菜单项是要在绘制之前。 在这种情况下，ID 是指只是第一个菜单项并*m_pSubMenu*成员变量`CCmdUI`对象将为 NULL。

这允许你启用弹出菜单不同于其菜单项，但需要编写一些菜单识别代码。 例如，在具有以下结构的嵌套菜单：

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

可以单独启用或禁用的 ID_NEW_SHEET 和 ID_NEW_CHART 命令。 **新建**如果启用了其中一个两个，应启用弹出菜单。

ID_NEW_SHEET （在弹出窗口中的第一个命令） 的命令处理程序将如下所示：

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION |
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

ID_NEW_CHART 的命令处理程序将正常更新命令处理程序并查找类似于：

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND 和 ON_BN_CLICKED

有关消息映射宏**ON_COMMAND**并**ON_BN_CLICKED**相同。 MFC 命令和控制通知路由机制仅使用命令 ID 来确定要将路由到哪个位置。 控制通知与控件通知代码为零 (**BN_CLICKED**) 被解释为命令。

> [!NOTE]
> 事实上，所有控件通知消息都经过命令处理程序链。 例如，它是为您编写的控件通知处理程序从技术上讲可能**EN_CHANGE**文档类中。 此外，由于此功能的实际应用程序很少，ClassWizard，不支持该功能使用可能会导致脆弱的代码对这不是功能的通常建议。

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>禁用自动禁用的按钮控件

如果放置了一个按钮控件上对话栏，或在对话框中，使用 where 调用**CWnd::UpdateDialogControls**自己，你会注意到这些按钮不具有**ON_COMMAND**或**ON_UPDATE_COMMAND_UI**处理程序将自动禁用，由框架。 在某些情况下，不需要有一个处理程序，但你将想要保持启用状态的按钮。 若要实现此目的的最简单方法是添加虚拟命令处理程序 （变得简单类向导） 并不执行任何操作中它。

## <a name="window-message-routing"></a>窗口消息路由

下面的 MFC 类和 Windows 消息路由和其他主题的影响它们在介绍一些更高级的主题。 此处的信息仅简要介绍。 请参阅*类库参考*有关公共 Api 的详细信息。 请参阅 MFC 库源代码的实现细节的详细信息。

请参阅[技术注意 17](../mfc/tn017-destroying-window-objects.md)窗口中清除的详细信息、 所有非常重要的主题**CWnd**-派生的类。

## <a name="cwnd-issues"></a>CWnd 问题

实现成员函数**CWnd::OnChildNotify**提供子窗口 （也称为控件），以挂钩或否则通知消息、 命令和控件的一个功能强大且可扩展的体系结构请转到其父 （或"所有者"） 的通知。 如果子窗口 （/ 控件） 是 c + + **CWnd**对象本身，虚函数**OnChildNotify**首次使用的参数调用原始消息中 (即， **MSG**结构)。 子窗口可以保留不动，消息、 吃掉它，或父级 （极少见的） 修改消息。

默认值**CWnd**实现处理以下消息，并使用**OnChildNotify**挂钩允许子窗口 （控件） 到第一次访问的消息：

- **WM_MEASUREITEM**并**WM_DRAWITEM** （对于自我描述）

- **WM_COMPAREITEM**并**WM_DELETEITEM** （对于自我描述）

- **WM_HSCROLL**和**WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

你会注意到**OnChildNotify**挂钩用于更改成自我描述消息的所有者描述消息。

除了**OnChildNotify**挂钩，滚动消息具有执行进一步的路由行为。 有关滚动条和源的详细信息，请参阅下面**WM_HSCROLL**并**WM_VSCROLL**消息。

## <a name="cframewnd-issues"></a>CFrameWnd 问题

**CFrameWnd**类提供的大多数命令路由和用户界面更新实现。 这主要用于应用程序的主框架窗口 (**M_pmainwnd**)，但适用于所有框架窗口。

主框架窗口是带有菜单栏的窗口和状态栏的父级或消息行。 命令传送上述讨论，请参阅和**WM_INITMENUPOPUP。**

**CFrameWnd**类提供了管理活动视图。 通过活动视图路由的以下消息：

- 所有命令消息 （活动视图获取第一次访问到它们）。

- **WM_HSCROLL**并**WM_VSCROLL**消息从同级滚动条 （见下文）。

- **WM_ACTIVATE** (和**WM_MDIACTIVATE** mdi) 获取转变为对虚拟函数的调用**CView::OnActivateView**。

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd 问题

这两个 MDI 框架窗口类派生自**CFrameWnd**因此同时启用了同样的命令路由和用户界面更新中提供**CFrameWnd**。 在典型 MDI 应用程序中，仅主框架窗口 (即**CMDIFrameWnd**对象) 包含菜单栏和状态栏，因此命令路由实现的主要来源。

常规路由方案为活动的 MDI 子窗口获取命令的第一次访问。 默认值**PreTranslateMessage**函数处理这两个 MDI 子窗口的快捷键对应表 （第一次） 和 MDI 框架 （第二个） 以及标准 MDI 系统命令快捷键一般将由**TranslateMDISysAccel** （最后一个）。

## <a name="scroll-bar-issues"></a>滚动条的问题

处理滚动消息时 (**WM_HSCROLL**/**OnHScroll**和/或**WM_VSCROLL**/**OnVScroll**)，应尝试编写处理程序代码，因此它不依赖于滚动栏消息来自何处。 这不只是常规的 Windows 问题，因为滚动消息可来自于 true 滚动条控件或从**WS_HSCROLL**/**WS_VSCROLL**滚动条不是滚动条控件。

MFC 扩展，以允许为子级或同级滚动窗口的滚动条控件 （事实上，滚动条和滚动的窗口之间的父/子关系可以是任何内容）。 这一点尤其重要的拆分窗口具有共享的滚动条。 请参阅[技术注意 29](../mfc/tn029-splitter-windows.md)有关的实现的详细信息**CSplitterWnd**上包括的详细信息共享滚动栏问题。

在边注中，有两个**CWnd**派生的类指定在滚动条样式在其中创建时间是捕获并不会传递给 Windows。 当传递给创建例程**WS_HSCROLL**和**WS_VSCROLL**可以独立设置，但不能更改创建后。 当然，应该不是直接测试，或将它们创建的窗口的 WS_SCROLL 样式位设置。

有关**CMDIFrameWnd**滚动条样式中传递到**创建**或**LoadFrame**用于创建 MDICLIENT。 如果您希望确保设置的可滚动 MDICLIENT 区域 （如 Windows 项目经理） 同时滚动条样式 (**WS_HSCROLL** &#124; **WS_VSCROLL**) 用于创建样式**CMDIFrameWnd**。

有关**CSplitterWnd**滚动条样式应用于拆分器区域的特殊共享的滚动条。 对于静态拆分窗口，通常不会设置这两种滚动条样式。 对于动态拆分窗口，则通常必须滚动条将拆分，也就是说，方向的样式集**WS_HSCROLL**如果你可以将行拆分**WS_VSCROLL**如果可以拆分列。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
