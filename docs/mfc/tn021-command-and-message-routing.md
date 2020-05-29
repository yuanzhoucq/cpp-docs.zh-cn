---
title: TN021：命令和消息传送
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: bdd405bda5c0af9e04a50eee4ef5738f3a53259e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370410"
---
# <a name="tn021-command-and-message-routing"></a>TN021：命令和消息传送

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明描述了命令路由和调度体系结构以及常规窗口消息路由中的高级主题。

有关此处描述的体系结构的一般详细信息，请参阅 Visual C++，特别是 Windows 消息、控件通知和命令之间的区别。 本说明假定您非常熟悉打印文档中描述的问题，并且仅涉及非常高级的主题。

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>命令路由和调度 MFC 1.0 功能演变为 MFC 2.0 体系结构

Windows 具有已重加载WM_COMMAND消息，以提供菜单命令、快捷键和对话框控制通知的通知。

MFC 1.0 通过允许`CWnd`派生类中的命令处理程序（例如"OnFileNew"）调用以响应特定WM_COMMAND，从而在此基础上构建了一点。 这与称为消息映射的数据结构粘合在一起，并产生了非常节省空间的命令机制。

MFC 1.0 还提供了用于将控制通知与命令消息分开的其他功能。 命令由 16 位 ID 表示，有时称为命令 ID。 命令通常从 （`CFrameWnd`即菜单选择或翻译的加速器） 开始，并路由到各种其他窗口。

MFC 1.0 在有限意义上使用命令路由，用于实现多文档接口 （MDI）。 （MDI 框架窗口将命令委托给其活动 MDI 子窗口。

此功能已在 MFC 2.0 中进行推广和扩展，以允许由更广泛的对象（而不仅仅是窗口对象）处理命令。 它为路由消息提供了更正式和可扩展的体系结构，并重用命令目标路由，不仅用于处理命令，还用于更新 UI 对象（如菜单项和工具栏按钮），以反映命令的当前可用性。

## <a name="command-ids"></a>命令 ID

有关命令路由和绑定过程的说明，请参阅可视化C++。 [技术说明 20](../mfc/tn020-id-naming-and-numbering-conventions.md)包含有关 ID 命名的信息。

我们使用通用前缀"ID_"用于命令 ID。 命令 ID >= 0x8000。 如果存在与命令 ID 具有相同 ID 的 STRINGTABLE 资源，则消息行或状态栏将显示命令描述字符串。

在应用程序的资源中，命令 ID 可以出现在多个位置：

- 在一个与消息行提示具有相同 ID 的 STRINGTABLE 资源中。

- 在可能附加到调用同一命令的菜单项的许多 MENU 资源中。

- （ADVANCED）在 GOSUB 命令的对话框按钮中。

在应用程序的源代码中，命令 ID 可以出现在多个位置：

- 在你的资源中。H（或其他主符号标头文件）用于定义特定于应用程序的命令指示。

- 用于创建工具栏的 ID 数组中。

- 在ON_COMMAND宏中。

- 在ON_UPDATE_COMMAND_UI宏中。

目前，MFC 中唯一需要命令 ID >= 0x8000 的实现是 GOSUB 对话框/命令的实现。

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>GOSUB 命令，在对话框中使用命令体系结构

路由和启用命令的命令体系结构非常适合框架窗口、菜单项、工具栏按钮、对话框栏按钮、其他控制栏和其他用户界面元素，这些元素旨在按需更新命令或控制指示到主命令目标（通常是主框架窗口）。 该主命令目标可以根据需要将命令或控制通知路由到其他命令目标对象。

如果将对话框控件的控制 ID 分配给相应的命令 ID，则对话框（模式或无模式）可以从命令体系结构的某些功能中受益。 对对话框的支持不是自动的，因此您可能需要编写一些附加代码。

请注意，要使所有这些功能正常工作，命令 ID 应>= 0x8000。 由于许多对话框可以路由到同一帧，因此共享命令应>= 0x8000，而特定对话框中的非共享 IDC 应<= 0x7FFF。

您可以将普通按钮放在正常模式对话框中，将按钮的 IDC 设置为相应的命令 ID。 当用户选择该按钮时，对话框的所有者（通常是主框架窗口）将像任何其他命令一样获取该命令。 这称为 GOSUB 命令，因为它通常用于启动另一个对话框（第一个对话框的 GOSUB）。

您还可以在对话框上调用该`CWnd::UpdateDialogControls`函数，并将其传递给主框架窗口的地址。 此函数将根据对话框控件在帧中是否具有命令处理程序启用或禁用它们。 对于应用程序空闲循环中的控制栏，将自动调用此功能，但您必须直接调用它，用于希望具有此功能的正常对话框。

## <a name="when-on_update_command_ui-is-called"></a>调用ON_UPDATE_COMMAND_UI时

始终保持程序菜单项的所有启用/检查状态可能是计算上成本高昂的问题。 一种常见技术是仅在用户选择 POPUP 时启用/检查菜单项。 mFC 2.0 的`CFrameWnd`实现处理WM_INITMENUPOPUP消息，并使用命令路由体系结构通过ON_UPDATE_COMMAND_UI处理程序确定菜单状态。

`CFrameWnd`还处理WM_ENTERIDLE消息来描述在状态栏（也称为消息行）上选择的当前菜单项。

由 Visual C++ 编辑的应用程序菜单结构用于表示WM_INITMENUPOPUP时可用的潜在命令。 ON_UPDATE_COMMAND_UI处理程序可以修改菜单的状态或文本，或用于高级用途（如文件 MRU 列表或 OLE Verbs 弹出式菜单），在绘制菜单之前实际修改菜单结构。

当应用程序进入空闲循环时，对工具栏（和其他控制栏）执行相同的ON_UPDATE_COMMAND_UI处理。 有关控制栏的详细信息，请参阅*类库参考*[和技术说明 31。](../mfc/tn031-control-bars.md)

## <a name="nested-pop-up-menus"></a>嵌套弹出式菜单

如果使用嵌套菜单结构，您会注意到在两个不同的情况下调用弹出菜单中第一个菜单项ON_UPDATE_COMMAND_UI处理程序。

首先，它调用弹出菜单本身。 这是必要的，因为弹出式菜单没有 ID，我们使用弹出式菜单的第一个菜单项的 ID 来引用整个弹出式菜单。 在这种情况下，`CCmdUI`对象的*m_pSubMenu*成员变量将为非 NULL，并将指向弹出菜单。

其次，在绘制弹出式菜单中的菜单项之前调用它。 在这种情况下，ID 仅引用第一个菜单项，`CCmdUI`对象*m_pSubMenu*成员变量将为 NULL。

这允许您启用不同于其菜单项的弹出式菜单，但需要编写一些菜单感知代码。 例如，在具有以下结构的嵌套菜单中：

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

可以独立启用或禁用ID_NEW_SHEET和ID_NEW_CHART命令。 如果启用了两个中的一个，则应启用 **"新建**"弹出式菜单。

ID_NEW_SHEET的命令处理程序（弹出窗口中的第一个命令）如下所示：

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

ID_NEW_CHART的命令处理程序将是一个正常的更新命令处理程序，如下所示：

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND和ON_BN_CLICKED

**ON_COMMAND**和**ON_BN_CLICKED**的消息映射宏相同。 MFC 命令和控制通知路由机制仅使用命令 ID 来决定路由到何处。 控件通知代码为零 （**BN_CLICKED**） 的控件通知被解释为命令。

> [!NOTE]
> 事实上，所有控件通知消息都通过命令处理程序链。 例如，从技术上讲，您可以在文档类中为**EN_CHANGE**编写控件通知处理程序。 这通常不可取，因为此功能的实际应用很少，ClassWizard 不支持该功能，并且使用该功能可能会导致代码脆弱。

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>禁用自动禁用按钮控件

如果在对话框栏或使用您自己调用**CWnd：：UpdateDialogControls**的对话框中放置按钮控件，您会注意到框架会自动为您禁用没有**ON_COMMAND**或**ON_UPDATE_COMMAND_UI**处理程序的按钮。 在某些情况下，您不需要有处理程序，但您希望该按钮保持启用状态。 实现此目的的最简单方法是添加虚拟命令处理程序（易于使用 ClassWizard），并且不执行任何操作。

## <a name="window-message-routing"></a>窗口消息路由

下面介绍了 MFC 类上的一些更高级的主题，以及 Windows 消息路由和其他主题如何影响它们。 此处的信息仅简要描述。 有关公共 API 的详细信息，请参阅*类库参考*。 有关实现详细信息的详细信息，请参阅 MFC 库源代码。

有关窗口清理的详细信息，请参阅[技术说明 17，](../mfc/tn017-destroying-window-objects.md)这是所有**CWnd**派生类的一个非常重要的主题。

## <a name="cwnd-issues"></a>问题

实现成员函数**CWnd：：OnChildNotify**为子窗口（也称为控件）提供了一个强大且可扩展的体系结构，用于钩住或以其他方式通知发送到其父级（或"所有者"）的消息、命令和控制通知。 如果子窗口（/控件）是**cWnd**对象本身C++，则首先使用原始消息（即**MSG**结构）中的参数调用虚拟函数**OnChildNotify。** 子窗口可以单独保留消息、食用邮件或修改父级的消息（罕见）。

默认**的 CWnd**实现处理以下消息，并使用**OnChildNotify**挂钩允许子窗口（控件）首先访问消息：

- **WM_MEASUREITEM**和**WM_DRAWITEM（** 用于自绘）

- **WM_COMPAREITEM**和**WM_DELETEITEM（** 用于自绘）

- **WM_HSCROLL**和**WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

您会注意到**OnChildNotify**挂钩用于将所有者绘制消息更改为自绘制消息。

除了**OnChildNotify**挂钩之外，滚动消息还有进一步的路由行为。 有关滚动条以及**WM_HSCROLL**和**WM_VSCROLL**消息源的更多详细信息，请参阅下文。

## <a name="cframewnd-issues"></a>CFramewnd 问题

**CFrameWnd**类提供大部分命令路由和用户界面更新实现。 这主要用于应用程序的主框架窗口 （**CWinApp：：m_pMainWnd**），但适用于所有框架窗口。

主框架窗口是带有菜单栏的窗口，是状态栏或消息行的父级。 请参阅上述有关命令路由和**WM_INITMENUPOPUP的讨论。**

**CFrameWnd**类提供活动视图的管理。 以下消息通过活动视图路由：

- 所有命令消息（活动视图将首先访问它们）。

- **来自**同级滚动条WM_HSCROLL和**WM_VSCROLL**消息（见下文）。

- **WM_ACTIVATE（** 和**MDI 的WM_MDIACTIVATE）** 被转换为对虚拟函数**CView 的调用：onActivateView**。

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFramewnd/CMDIChildwnd 问题

两个 MDI 帧窗口类都派生自**CFrameWnd，** 因此都启用了相同的命令路由和用户界面更新在**CFrameWnd**中提供。 在典型的 MDI 应用程序中，只有主框架窗口（即**CMDIFrameWnd**对象）保存菜单栏和状态栏，因此是命令路由实现的主要来源。

常规路由方案是活动 MDI 子窗口首先访问命令。 默认**PreTranslateMessage**函数可处理 MDI 子窗口（第一个）和 MDI 帧（第二个）以及通常由**TranslateMDISysAccel（** 最后）处理的标准 MDI 系统命令加速器的加速器表。

## <a name="scroll-bar-issues"></a>滚动条问题

处理滚动消息时 **（WM_HSCROLL**/**OnHScroll**和/或**WM_VSCROLL**/**OnVScroll），** 应尝试编写处理程序代码，以便它不依赖于滚动条消息的来龙去向。 这不仅是一般 Windows 问题，因为滚动消息可能来自真正的滚动条控件或/**WS_HSCROLLWS_VSCROLL**滚动条**WS_HSCROLL**（不是滚动条控件）。

MFC 扩展了该控件，以使滚动条控件可以是要滚动的窗口的子控件或同级控件（事实上，滚动条和要滚动的窗口之间的父/子关系可以是任何）。 对于具有拆分窗口的共享滚动条，这一点尤其重要。 有关**CSplitterWnd**实施的详细信息，请参阅[技术说明 29，](../mfc/tn029-splitter-windows.md)包括有关共享滚动条问题的详细信息。

在旁注中，有两个**CWnd**派生类，其中在创建时指定的滚动条样式被困，不会传递到 Windows。 当传递到创建例程时，可以独立设置**WS_HSCROLL**和**WS_VSCROLL，** 但在创建后无法更改。 当然，不应直接测试或设置它们创建的窗口的WS_SCROLL样式位。

对于**CMDIFrame，** 您传递给 **"创建**"或 **"加载帧"** 的滚动条样式用于创建 MDICLIENT。 如果您希望有一个可滚动的 MDICLIENT 区域（如 Windows 程序管理器），请确保为用于创建**CMDIFrameWnd**的样式设置滚动条样式 **（WS_HSCROLL&#124;WS_VSCROLL）。** **WS_VSCROLL**

对于**CSplitterWnd，** 滚动条样式适用于拆分器区域的特殊共享滚动条。 对于静态拆分窗口，通常不会设置任一滚动条样式。 对于动态拆分窗口，通常为要拆分的方向设置了滚动条样式，也就是说，如果可以拆分行 **，WS_HSCROLL，WS_VSCROLL****拆分**列。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
