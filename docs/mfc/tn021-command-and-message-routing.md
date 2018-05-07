---
title: TN021： 命令和消息传送 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.routing
dev_langs:
- C++
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a1061f4a7d4394cb84c26514795c406f78146df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tn021-command-and-message-routing"></a>TN021：命令和消息传送
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍命令路由和调度体系结构以及常规的窗口消息路由中的高级的主题。  
  
 请参阅 Visual c + + 有关此处所述的体系结构的常规详细信息尤其是 Windows 消息、 控件通知和命令之间的差异。 本说明假定你非常熟悉打印文档中所述的问题，并仅解决非常高级的主题。  
  
## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>命令传送和调度 MFC 1.0 功能发展到 MFC 2.0 体系结构  
 Windows 具有**WM_COMMAND**重载以提供的菜单命令、 快捷键和对话框控件通知的通知的消息。  
  
 MFC 1.0 内置上稍有允许命令处理程序 (例如，"OnFileNew")，从而**CWnd**派生类来获取调用以响应特定**WM_COMMAND**。 这与调用消息映射的数据结构一起粘附并导致空间非常高效命令机制中。  
  
 MFC 1.0 还提供其他功能来分隔从命令消息的控件通知。 命令表示的 16 位 ID，有时称为一个命令 id。 从正常启动命令**CFrameWnd** （即菜单中选择或已翻译的快捷键），并获取路由到各种其他窗口。  
  
 MFC 1.0 使用的有限的意义上实现多文档界面 (MDI) 中的命令路由。 （MDI 框架窗口的委托到其活动的 MDI 子窗口的命令）。  
  
 此功能已通用化和扩展在 MFC 2.0 中以允许由更多的对象 （而不仅仅是窗口对象） 处理的命令。 它提供了详细的正式和可扩展的体系结构，用于路由消息，并重新使用命令目标传送，不仅能处理的命令，但还用于更新 UI 对象 （如菜单项和工具栏按钮） 以反映命令的当前可用性.  
  
## <a name="command-ids"></a>命令 ID  
 命令路由和绑定过程的说明，请参阅 Visual c + +。 [技术说明 20](../mfc/tn020-id-naming-and-numbering-conventions.md)包含 ID 命名的信息。  
  
 我们使用泛型的前缀"ID_"命令 Id。 命令 Id 是 > = 0x8000。 消息行或状态栏将显示命令描述字符串是否具有同一 Id 作为命令 id。 的 STRINGTABLE 资源  
  
 在你的应用程序的资源，的命令 ID 可以将出现在多个位置：  
  
-   在一个 STRINGTABLE 资源具有相同 ID 作为消息行提示符。  
  
-   可能是多个菜单的资源中附加到调用相同的命令的菜单项。  
  
-   （高级） GOSUB 命令对话框按钮。  
  
 在你的应用程序的源代码，的命令 ID 可以显示在多个位置：  
  
-   在所需的资源。H （或其他主符号头文件） 来定义特定于应用程序的命令 Id。  
  
-   可能是在用于创建工具栏的 ID 数组。  
  
-   在**ON_COMMAND**宏。  
  
-   可能在**ON_UPDATE_COMMAND_UI**宏。  
  
 当前，需要命令 Id 的 MFC 中唯一的实现是 > = 0x8000 是 GOSUB 对话框/命令的实现。  
  
## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>GOSUB 命令，使用对话框中的命令体系结构  
 路由和启用命令的命令体系结构适用于框架窗口、 菜单项、 工具栏按钮、 对话栏按钮，其他控件栏和旨在更新上需和路由命令或控件 Id 到 main 其他用户界面元素命令目标 （通常主框架窗口）。 该主命令目标可能将命令或控件通知路由到根据其他命令目标对象。  
  
 对话框 （模式或无模式） 可以受益于的一些命令体系结构功能，如果将对话框控件的控件 ID 分配到相应的命令 id。 对话框支持不是自动进行的因此你可能需要编写一些附加代码。  
  
 请注意，所有这些功能正常工作，你的命令 Id 应 > = 0x8000。 由于许多对话框无法获取路由到同一帧，共享的命令应 > = 0x8000，而非共享的 Idc 中特定对话应为 < = 0x7FFF。  
  
 你可以将常规按钮放在与设置为相应的命令 id。 该按钮的 IDC 正常模式对话框 当用户选择按钮时，对话框 （通常主框架窗口） 的所有者将获取就像任何其他命令的命令。 这被称为 GOSUB 命令，因为它通常用于显示其他对话框 (第一个对话框 GOSUB)。  
  
 你还可以调用该函数**CWnd::UpdateDialogControls**上你的对话框并将其传递的主框架窗口的地址。 此函数将启用或禁用对话框控件基于是否帧中具有命令处理程序。 调用此函数可自动为你的应用程序的空闲循环中的控件条，但你必须调用它直接为你想让此功能的正常对话框。  
  
## <a name="when-onupdatecommandui-is-called"></a>当调用 ON_UPDATE_COMMAND_UI  
 维护程序的所有菜单项的启用检查状态的时间可能是计算开销很大的问题。 一种常用技术是启用/检查菜单项仅当用户选择弹出窗口时。 MFC 2.0 实现**CFrameWnd**句柄**WM_INITMENUPOPUP**消息并使用命令路由体系结构来确定通过菜单的状态**ON_UPDATE_COMMAND_UI**处理程序。  
  
 **CFrameWnd**还可以处理**WM_ENTERIDLE**要说明当前选择 （也称为消息行） 的状态栏上的项的菜单的消息。  
  
 应用程序的菜单结构，由 Visual c + + 中，编辑用于表示可用的潜在命令**WM_INITMENUPOPUP**时间。 **ON_UPDATE_COMMAND_UI**处理程序可以修改的状态或文本的菜单上，或者为高级 （如文件 MRU 列表或 OLE 谓词弹出菜单），使用实际修改之前的菜单结构绘制菜单。  
  
 某种程度上相同**ON_UPDATE_COMMAND_UI**对工具栏 （和其他控件栏） 执行处理应用程序在进入其空闲循环。 请参阅*类库参考*和[技术说明 31](../mfc/tn031-control-bars.md)的控件条的详细信息。  
  
## <a name="nested-pop-up-menus"></a>嵌套的弹出菜单  
 如果使用嵌套的菜单结构，您将注意到， **ON_UPDATE_COMMAND_UI**在两个不同的情况下调用第一个弹出菜单中的菜单项的处理程序。  
  
 首先，为调用弹出菜单。 这是必需的因为弹出菜单没有 Id，我们使用弹出菜单的第一菜单项的 ID 来引用整个弹出菜单。 在这种情况下， **m_pSubMenu**成员变量**CCmdUI**对象将为非 NULL，并且将指向弹出菜单。  
  
 其次，它之前调用的弹出菜单中的菜单项是要绘制。 在这种情况下，ID 是指只是第一个菜单项和**m_pSubMenu**成员变量**CCmdUI**对象将为 NULL。  
  
 这允许你启用弹出菜单不同于其菜单项，但需要你编写一些菜单注意代码。 例如，在具有以下结构的嵌套菜单：  
  
```  
File>  
    New> 
    Sheet (ID_NEW_SHEET)  
    Chart (ID_NEW_CHART)  
```  
  
 ID_NEW_SHEET 和 ID_NEW_CHART 命令可以单独启用或禁用。 **新建**如果启用了两个的其中一个，则应启用弹出菜单。  
  
 ID_NEW_SHEET （弹出窗口中的第一个命令） 的命令处理程序将如下所示：  
  
```  
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)  
{  
    if (pCmdUI->m_pSubMenu != NULL)  
 { *// enable entire pop-up for "New" sheet and chart  
    BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;  
 *// CCmdUI::Enable is a no-op for this case,
    so we *//   must do what it would have done.  
    pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex, 
    MF_BYPOSITION |   
 (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

    return; 
 } *// otherwise just the New Sheet command  
    pCmdUI->Enable(m_bCanCreateSheet);

} 
```  
  
 ID_NEW_CHART 的命令处理程序将正常更新命令处理程序和外观类似于：  
  
```  
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)  
{  
    pCmdUI->Enable(m_bCanCreateChart);

} 
```  
  
## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND 和 ON_BN_CLICKED  
 有关消息映射宏**ON_COMMAND**和**ON_BN_CLICKED**相同。 MFC 命令和控件通知路由机制仅使用命令 ID 来决定将路由到的位置。 控制通知控件通知代码为零 (**BN_CLICKED**) 都会被解释为命令。  
  
> [!NOTE]
>  事实上，所有控件通知消息的都经历命令处理程序链。 例如，它是为你要写入的控件通知处理程序从技术上讲可能**EN_CHANGE**中您的文档类。 这是功能的不通常，建议您，因为此功能的实际应用几个，ClassWizard，不支持该功能并且使用可能导致脆弱的代码。  
  
## <a name="disabling-the-automatic-disabling-of-button-controls"></a>禁用自动禁用的按钮控件  
 如果你在上一个对话栏，按钮控件置于或在对话框中使用的位置调用**CWnd::UpdateDialogControls**自己，你将注意到没有该按钮**ON_COMMAND**或**ON_UPDATE_COMMAND_UI**处理程序将自动禁用为你的框架。 在某些情况下，你将不需要的处理程序，但你将想要保持启用状态的按钮。 实现此目的的最简单方法是添加 dummy 命令处理程序 （轻松地完成与 ClassWizard） 和不在其中执行任何操作。  
  
## <a name="window-message-routing"></a>窗口消息路由  
 下面的 MFC 类和如何邮件路由，Windows 及其他主题影响它们描述一些更高级的主题。 此处的信息只简要介绍。 请参阅*类库参考*有关公共 Api 的详细信息。 请参阅实现详细信息的详细信息的 MFC 库源代码。  
  
 请参阅[技术注意 17](../mfc/tn017-destroying-window-objects.md)窗口清理的详细信息、 所有非常重要主题**CWnd**-派生类。  
  
## <a name="cwnd-issues"></a>CWnd 问题  
 实现成员函数**CWnd::OnChildNotify**提供的子窗口 （也称为控件） 挂钩或否则通知的消息、 命令和控件的功能强大且可扩展体系结构转到其父 （或"所有者"） 的通知。 如果子窗口 （/ 控制） 是 c + + **CWnd**对象本身，虚函数**OnChildNotify**都会首先调用具有参数从原始消息 (即，**消息**结构)。 子窗口可以让消息保持不变，从中，或父级 （罕见） 修改消息。  
  
 默认值**CWnd**实现处理以下消息，并使用**OnChildNotify**挂钩以便子窗口 （控件） 的消息的第一个访问：  
  
- **WM_MEASUREITEM**和**WM_DRAWITEM** （对于自我描述）  
  
- **WM_COMPAREITEM**和**WM_DELETEITEM** （对于自我描述）  
  
- **WM_HSCROLL**和**WM_VSCROLL**  
  
- **WM_CTLCOLOR**  
  
- **WM_PARENTNOTIFY**  
  
 你将注意到**OnChildNotify**挂钩用于自我描述的消息更改所有者描述消息。  
  
 除了**OnChildNotify**挂钩，滚动消息具有进一步的路由行为。 有关在滚动条和资源的更多详细信息，请参阅下面**WM_HSCROLL**和**WM_VSCROLL**消息。  
  
## <a name="cframewnd-issues"></a>CFrameWnd 问题  
 **CFrameWnd**类提供的大多数命令路由和用户界面更新实现。 这主要用于应用程序的主框架窗口 (**M_pmainwnd**)，但适用于所有框架窗口。  
  
 主框架窗口是与菜单栏窗口，并且是状态栏的父级或消息行。 命令传送上面讨论，请参阅和**WM_INITMENUPOPUP。**  
  
 **CFrameWnd**类提供的活动视图的管理。 通过活动视图，以下的消息进行路由：  
  
-   （活动视图获取第一个访问它们） 的所有命令消息。  
  
- **WM_HSCROLL**和**WM_VSCROLL**消息从同级滚动条 （见下文）。  
  
- **WM_ACTIVATE** (和**WM_MDIACTIVATE** mdi) 获取转变为对虚函数的调用**CView::OnActivateView**。  
  
## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd 问题  
 这两个 MDI 框架窗口类派生自**CFrameWnd**因此同时启用同一个排序的命令路由和用户界面更新中提供**CFrameWnd**。 在典型 MDI 应用程序中，仅主框架窗口 (即， **CMDIFrameWnd**对象) 包含在菜单栏和状态栏，因此是命令路由实现的主要来源。  
  
 常规的路由方案为活动的 MDI 子窗口获取命令的第一次访问。 默认值**PreTranslateMessage**函数处理这两个 MDI 子窗口的快捷键对应表 （第一次） 和 MDI 框架 （第二个） 以及一般将由标准 MDI 系统命令加速器**TranslateMDISysAccel** （最后一个）。  
  
## <a name="scroll-bar-issues"></a>滚动条问题  
 当处理滚动消息 (**WM_HSCROLL**/**OnHScroll**和/或**WM_VSCROLL**/**OnVScroll**)，你应尝试编写处理程序代码，因此它不依赖于滚动栏消息来自何处。 这不是因为滚动消息可以来自 true 滚动条控件或从仅一个常规的 Windows 问题， **WS_HSCROLL**/**WS_VSCROLL**滚动条不是滚动条控件。  
  
 MFC 扩展，若要允许滚动条控件是子或在滚动窗口的同级 （事实上，之间的滚动条和在滚动的窗口的父/子关系可以是任何内容）。 这一点尤其重要的拆分窗口具有共享的滚动条。 请参阅[技术注意 29](../mfc/tn029-splitter-windows.md)有关的实现的详细信息**CSplitterWnd**上包括的详细信息共享滚动栏问题。  
  
 在端说明中，有两个**CWnd**派生的类指定在滚动条样式在其中创建时间是捕获并不会传递给 Windows。 当传递到创建例程， **WS_HSCROLL**和**WS_VSCROLL**可以独立设置，但不能更改创建后。 当然，应该不是直接测试，或将它们创建的窗口 WS_SCROLL 样式位设置。  
  
 有关**CMDIFrameWnd**滚动条样式在传入到**创建**或**LoadFrame**用于创建 MDICLIENT。 如果你想要具有一定要设置的可滚动 MDICLIENT 区域 （如 Windows 程序管理器） 同时滚动条样式 (**WS_HSCROLL** &#124; **WS_VSCROLL**) 用于创建样式**CMDIFrameWnd**。  
  
 有关**CSplitterWnd**滚动条样式应用于拆分器区域的特殊共享的滚动条。 对于静态拆分窗口，通常不会设置这两种滚动栏样式。 对于动态拆分窗口，你将通常具有滚动条样式设置为您将拆分，即方向**WS_HSCROLL**可以拆分行，如果**WS_VSCROLL**如果可以拆分列。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

