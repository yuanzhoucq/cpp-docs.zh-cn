---
title: "TN021：命令和消息传送 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.routing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令传送 [C++], 技术说明 TN021"
  - "TN021"
  - "Windows 消息 [C++], 路由"
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN021：命令和消息传送
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释在常规窗口信息描述路由命令传送和计划的体系结构和高级主题。  
  
 参考有关 Visual C\+\+ 在 \+ 这里，尤其是介绍的体系结构方法的泛详细信息窗口消息之间的变化，控件通知和命令。  此注释假定您非常熟悉。仅打印文档和地址非常高级主题描述的问题。  
  
## MFC 命令传送和计划 1.0 功能发展到 MFC 2.0 体系结构  
 窗口具有重载提供菜单命令、快捷键和对话框通知控件通知的 **WM\_COMMAND** 消息。  
  
 在这 1.0 生成 MFC 的一点。允许的命令处理程序 \(例如，“OnFileNew”\) **CWnd** 派生类中调用。响应特定的 **WM\_COMMAND**。  这与在中的空间利用率的命令机制的数据结构调用消息映射的结果。粘附和。  
  
 分隔的控件通知 MFC 1.0 还提供的其他功能。命令消息。  命令由 16 位表示 ID，有时称为命令 ID.  从命令 **CFrameWnd** \(即选择的菜单或转换的快捷键\) 开始通常并将其路由到各种其他窗口。  
  
 一种在受限有意义的 MFC 1.0 使用的命令传送多文档界面 \(MDI\) \(MDI\) 的实现。\(MDI 框架窗口委托命令到其活动 MDI 子窗口。\)  
  
 此功能在 MFC 2.0 对并扩展允许命令由各种各样的对象 \(而不仅仅窗口对象\) 处理。  为路由消息提供更为正式和更可扩展的体系结构并重用不仅处理的路由命令，命令目标，而且用于更新 UI 对象 \(如菜单项和工具栏按钮\) 以反映命令的当前状态。  
  
## 命令 ID  
 对于命令传送和绑定过程的说明参见 Visual C\+\+。  [技术说明 20](../mfc/tn020-id-naming-and-numbering-conventions.md) 包含有关 ID 命名的信息。  
  
 我们为命令 ID 使用常规前缀“ID\_”。  命令 ID 是 \>\= 0x8000。  如果具有 ID 的 STRINGTABLE 资源和 . 命令 ID 相同，或消息行状态栏将显示命令描述字符串  
  
 在应用程序的资源 ID，命令导航到的只在几个位置显示：  
  
-   在具有 ID 和提示消息行相同的 STRINGTABLE 资源。  
  
-   在可以附加与此菜单项调用相同的命令的许多菜单资源。  
  
-   \(高级\) 在命令按钮 GOSUB 的对话框。  
  
 在应用程序的源代码，该命令 ID 导航到的只在几个位置显示：  
  
-   在\) 定义特定的命令 ID 的 RESOURCE.H \(或其他主符号头文件。  
  
-   可能在使用的 ID 数组创建工具栏。  
  
-   在 **ON\_COMMAND** 宏。  
  
-   无法在 **ON\_UPDATE\_COMMAND\_UI** 宏。  
  
 目前，需要命令 ID。MFC 的实现是 \>\= 0x8000 是 GOSUB 对话框\/命令的实现。  
  
## GOSUB 命令，将在对话框的命令体系结构  
 路由和启用命令、命令结构适用于框架窗口，菜单项，工具栏按钮，对话栏使用按钮，设计的其他控件条和其他用户界面元素更新按需和路由命令或控件 ID。主命令目标 \(通常主框架窗口。\)  主的命令目标上发送命令或控件通知。其他命令中为适当目标对象。  
  
 对话框 \(模式或无模式\) 得益于某些命令的体系结构功能，则分配对话框的控件 ID 的适当 . 命令 ID  对话框的支持并不是自动进行的，因此，您可能需要编写一些个附加代码。  
  
 监视对所有这些功能正常工作，命令 ID 应是 \>\= 0x8000。  因为许多对话框会路由到相同的帧，共享的命令应是 \>\=，0x8000，而按特定的对话框应共享 IDCs 是 \<\= 0x7FFF。  
  
 在带有按钮集的 IDC 的普通模式对话框可以将普通按钮为适当的命令 ID.  当用户选择该按钮时，对话框 \(通常主框架窗口的所有者\) 获取命令与任何其他命令。  这称为 GOSUB 命令，因为它通常用于引发其他对话框 \(第一个对话框的 GOSUB\)。  
  
 也可以调用在对话框的函数 **CWnd::UpdateDialogControls** 和传递给主框架窗口的地址。  此函数将禁用或启用基于的对话框控件无论包含命令处理程序。帧。  此函数为您自动调用在应用程序的、的控件条，但是，您必须调用它直接规则对话框中您希望具有此功能。  
  
## 当 ON\_UPDATE\_COMMAND\_UI 调用  
 维护的启用\/选中状态所有程序的菜单项。始终是计算开销大的问题。  只有当用户选择弹出时，常见方法是启用\/检查菜单项。  **CFrameWnd** 的 **WM\_INITMENUPOPUP** 实现 MFC 2.0 处理消息并使用命令传送结构通过 **ON\_UPDATE\_COMMAND\_UI** 处理程序确定菜单的状态。  
  
 **CFrameWnd** 还处理 **WM\_ENTERIDLE** 消息介绍状态栏上选择的当前菜单项 \(aka 消息行\)。  
  
 应用程序菜单结构，由 Visual C\+\+ 编辑，用于表示可能的命令 **WM\_INITMENUPOPUP** 在可用时间。  **ON\_UPDATE\_COMMAND\_UI** 处理程序来修改菜单的状态或文本，或者对高级用途使用 \(如文件 MRU 列表或 OLE 谓词弹出菜单\)，实际修改菜单结构，在菜单之前绘制。  
  
 同一类 **ON\_UPDATE\_COMMAND\_UI** 处理为工具栏 \(和其他控件条\) 完成，同时应用程序输入其、时。  参见 *类库参考* 和 [技术说明 31](../mfc/tn031-control-bars.md) 有关控件条的更多信息。  
  
## 嵌套的弹出菜单  
 如果您使用嵌套的菜单结构，则请注意第一个菜单项的处理 **ON\_UPDATE\_COMMAND\_UI** 程序在弹出菜单在两种不同情况调用。  
  
 首先，它为弹出菜单调用。  这是必需的，因为当弹出菜单没有 ID，我们使用弹出菜单的第一个菜单项的 ID 引用整个弹出菜单。  在此例中，**CCmdUI** 对象的 **m\_pSubMenu** 成员变量不为 null，并指向弹出菜单。  
  
 接下来，在这种情况下，在弹出菜单的菜单项将绘制前，它调用。  在这种情况下，ID 引用第一个菜单项，然后 **CCmdUI** 对象的 **m\_pSubMenu** 成员变量为 NULL。  
  
 这允许您支持菜单弹出不同于其菜单项，但是，要求您编写某菜单识别代码。  例如，在具有以下结构中嵌套的菜单：  
  
```  
File>  
    New>  
        Sheet (ID_NEW_SHEET)  
        Chart (ID_NEW_CHART)  
```  
  
 ID\_NEW\_SHEET 和 ID\_NEW\_CHART 命令可以单独启用或禁用。  **新建** 一个弹出菜单，如果中两个启用，应当启用。  
  
 ID\_NEW\_SHEET \(在弹出的第一个命令的命令处理程序\) 将类似于：  
  
```  
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)  
{  
    if (pCmdUI->m_pSubMenu != NULL)  
    {  
        // enable entire pop-up for "New" sheet and chart  
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;  
  
        // CCmdUI::Enable is a no-op for this case, so we  
        //   must do what it would have done.  
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,  
            MF_BYPOSITION |   
                (bEnable ? MF_ENABLED : (MF_DISABLED | MF_GRAYED)));  
        return;  
    }  
    // otherwise just the New Sheet command  
    pCmdUI->Enable(m_bCanCreateSheet);  
}  
```  
  
 ID\_NEW\_CHART 的命令处理程序会处理常规更新命令程序和类似于：  
  
```  
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)  
{  
    pCmdUI->Enable(m_bCanCreateChart);  
}  
```  
  
## ON\_COMMAND 和 ON\_BN\_CLICKED  
 **ON\_COMMAND** 和 **ON\_BN\_CLICKED** 的消息映射宏相同。  MFC 命令和控件通知路由机制在何处使用命令 ID 只确定路由。  与控件通知代码的控件通知被解释为零 \(**BN\_CLICKED**\) 命令。  
  
> [!NOTE]
>  事实上，任何控件通知消息查看命令处理程序的字符串。  例如，编写 **EN\_CHANGE** 的控件通知处理程序在类文档您可能的。  这通常不可取，因为此功能的实际应用的是，功能不受 ClassWizard 支持，因此，使用功能的使用可能生成脆弱的代码。  
  
## 禁用自动禁用的按钮控件  
 如果您将一个按钮控件在对话栏，或者在您调用的自己的 **CWnd::UpdateDialogControls** 对话框使用，您将注意没有 **ON\_COMMAND** 或 **ON\_UPDATE\_COMMAND\_UI** 处理程序的按钮。将自动禁用由框架。  有时，不需要具有处理程序，不过，您将希望该按钮将启用。  简单的实现此方法要么不会添加一个虚拟的命令处理程序 \(\) 和该执行。ClassWizard 轻松执行。  
  
## 窗口消息路由  
 下面描述了对 MFC 类的一些高级主题，并且窗口消息路由及其他主题如何影响这些值。  此处的信息只简单介绍。  有关公共 API 的详细信息，请参见 *类库参考*。   请参见 MFC 库源代码有关执行详细信息的更多信息。  
  
 参考 [技术说明 17](../mfc/tn017-destroying-window-objects.md) 有关窗口清理的详细信息，将任何 **CWnd**的一个非常基本主题派生类。  
  
## CWnd 问题  
 实现成员 **CWnd::OnChildNotify** 函数为子窗口 \(也称为\) 控件提供了强大且可扩展的体系结构以挂钩或都收到消息、命令并转到其父的控件通知 \(或“所有者”\)。  如果子窗口 \(\/control\) 是 C.C\+\+ **CWnd** 对象，虚函数首先调用 **OnChildNotify** 与原始消息 \(即 **MSG** 结构\) 的参数。  子窗口不能理会消息，吃它或修改父 \(常见的消息\)。  
  
 默认 **CWnd** 实现处理以下信息并使用 **OnChildNotify** 挂钩允许子窗口 \(控件\)。第一次访问包装在消息：  
  
-   **WM\_MEASUREITEM** 和 **WM\_DRAWITEM** \(对于自描述的\)  
  
-   **WM\_COMPAREITEM** 和 **WM\_DELETEITEM** \(对于自描述的\)  
  
-   **WM\_HSCROLL**、**WM\_VSCROLL**  
  
-   **WM\_CTLCOLOR**  
  
-   **WM\_PARENTNOTIFY**  
  
 可以注意 **OnChildNotify** 不提供更改所有者描述信息使用到自绘制消息。  
  
 除了 **OnChildNotify**，挂钩以外滚动消息有进一步的路由行为。   有关的更详细信息。下面参见位于 **WM\_HSCROLL** 和 **WM\_VSCROLL** 消息滚动条和源。  
  
## CFrameWnd 问题  
 提供大多数命令传送和用户界面更新实现的 **CFrameWnd** 类。  这适用于某些应用程序主要使用 \(**CWinApp::m\_pMainWnd**\) 的主框架窗口，但适用于所有框架窗口。  
  
 主框架窗口是窗口的菜单栏。和是状态栏或消息行的父。   请参见有关命令传送和 **WM\_INITMENUPOPUP.**的上面讨论  
  
 **CFrameWnd** 类提供活动视图的管理。  以下信息通过活动视图发送：  
  
-   所有命令消息 \(活动视图获得对其第一访问权限\)。  
  
-   **WM\_HSCROLL** 和 **WM\_VSCROLL** 消息来自同级滚动条 \(如下所示\)。  
  
-   MDI \(的**WM\_ACTIVATE** 和 **WM\_MDIACTIVATE** \) 获得转换为对中的虚函数 **CView::OnActivateView**。  
  
## CMDIFrameWnd\/CMDIChildWnd 问题  
 两个 MDI 框架窗口类从 **CFrameWnd** 派生并为同一类。**CFrameWnd**和用户界面更新启用提供的路由命令。  在典型的 MDI 应用程序，仅主框架窗口 \(即 **CMDIFrameWnd** 对象\) 存放菜单栏和状态栏也是路由命令实现的主要源。  
  
 泛路由方案处于活动 MDI 子窗口获取对命令之一访问。  默认 **PreTranslateMessage** 函数处理 MDI 子窗口中的快捷键对应表 \(\) 先和 MDI 框架 \(二个值\) 和 **TranslateMDISysAccel** 通常处理标准 \(FIPS\) MDI 系统命令快捷 \(前\)。  
  
## 条滚动问题  
 处理当滚动消息 \(**WM\_HSCROLL**\/**OnHScroll** 和 **WM\_VSCROLL**\/**OnVScroll**\) 时，应尝试编写处理程序代码，因此不取决于滚动条消息来自何处。  这是一般性问题，不仅窗口，因为滚动消息可以来自 true 滚动条控件或 **WS\_HSCROLL**\/不是滚动条控件的**WS\_VSCROLL** 滚动条。  
  
 MFC 扩展这允许滚动条控件是滚动窗口的子级或同级 \(实际上，滚动条之间的父\/子关系并滚动的窗口可以是任意值。\)  这对于使用拆分窗口的共享滚动条是尤为重要。   参考 [技术说明 29](../mfc/tn029-splitter-windows.md) 有关 **CSplitterWnd** 的实现的详细信息 \(包括有关共享条滚动问题的更多信息。  
  
 在旁注，具有滚动条来指定在创建时间捕获和未通过向窗口的两类 **CWnd** 派生。  当正传递到创建例程，**WS\_HSCROLL** 和 **WS\_VSCROLL**。独立设置，但，在创建无法更改后。  当然，您不应直接或测试设置 WS\_? 滚动它们创建的窗口样式位。  
  
 对于 **CMDIFrameWnd** 传递给 **创建** 的滚动条或样式 **LoadFrame** 用于创建 MDICLIENT。  如果希望在 MDICLIENT 可滚动区域 \(如窗口管理器\) 请务必设置两个滚动条。样式 \(**WS\_HSCROLL** &#124; **WS\_VSCROLL**\) 对的样式创建一个 **CMDIFrameWnd**。  
  
 对于 **CSplitterWnd** 滚动条样式适用于特定共享的滚动条。拆分区域。  对于静态拆分窗口，您通常不会设置任何滚动条。样式  对于动态拆分窗口，通常将样式滚动条设置。将拆分器的方向，也就是说，**WS\_HSCROLL**，则可以拆分行，如果 **WS\_VSCROLL**，可以拆分列。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)