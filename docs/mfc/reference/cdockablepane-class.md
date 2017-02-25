---
title: "CDockablePane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDockablePane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockablePane class"
ms.assetid: e2495f4c-765f-48f9-a2e2-e45e47608d91
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CDockablePane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现在一个选项卡式窗格可以在停靠站点停靠或包含的一个窗格。  
  
## 语法  
  
```  
class CDockablePane : public CPane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDockablePane::CDockablePane](../Topic/CDockablePane::CDockablePane.md)|构造和初始化 `CDockablePane` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md)|附加窗格到另一个窗格。  这将创建一个选项卡式窗格。|  
|[CDockablePane::CalcFixedLayout](../Topic/CDockablePane::CalcFixedLayout.md)|返回窗格矩形的大小。|  
|[CDockablePane::CanAcceptMiniFrame](../Topic/CDockablePane::CanAcceptMiniFrame.md)|确定指定的要帧是否可以停靠到窗格。|  
|[CDockablePane::CanAcceptPane](../Topic/CDockablePane::CanAcceptPane.md)|确定另一个窗格是否可以停靠到当前窗格。|  
|[CDockablePane::CanAutoHide](../Topic/CDockablePane::CanAutoHide.md)|确定窗格是否支持自动隐藏模式。  （重写 [CBasePane::CanAutoHide](../Topic/CBasePane::CanAutoHide.md)。）|  
|[CDockablePane::CanBeAttached](../Topic/CDockablePane::CanBeAttached.md)|确定当前窗格是否可以停靠到另一个窗格。|  
|[CDockablePane::ConvertToTabbedDocument](../Topic/CDockablePane::ConvertToTabbedDocument.md)|将一个或多个停靠窗格为选项卡式MDI文档。|  
|[CDockablePane::CopyState](../Topic/CDockablePane::CopyState.md)|将一个停靠窗格的状态。|  
|[CDockablePane::Create](../Topic/CDockablePane::Create.md)|创建Windows控件并将它附加到 `CDockablePane` 对象。|  
|[CDockablePane::CreateDefaultPaneDivider](../Topic/CDockablePane::CreateDefaultPaneDivider.md)|当停靠到框架窗口，创建窗格中使用默认分隔符。|  
|[CDockablePane::CreateEx](../Topic/CDockablePane::CreateEx.md)|创建Windows控件并将它附加到 `CDockablePane` 对象。|  
|[CDockablePane::CreateTabbedPane](../Topic/CDockablePane::CreateTabbedPane.md)|创建从当前窗格的一个选项卡式窗格。|  
|[CDockablePane::DockPaneContainer](../Topic/CDockablePane::DockPaneContainer.md)|停靠容器到窗格中。|  
|[CDockablePane::DockPaneStandard](../Topic/CDockablePane::DockPaneStandard.md)|使用大纲\(标准\)停靠，停靠一个窗格。|  
|`CDockablePane::DockToFrameWindow`|内部使用。  停靠窗格，请使用 [CPane::DockPane](../Topic/CPane::DockPane.md) 或 [CDockablePane::DockToWindow](../Topic/CDockablePane::DockToWindow.md)。|  
|[CDockablePane::DockToRecentPos](../Topic/CDockablePane::DockToRecentPos.md)|停靠一个窗格将其存储最近的停靠位置。|  
|[CDockablePane::DockToWindow](../Topic/CDockablePane::DockToWindow.md)|停靠到另一个停靠窗格的一个停靠窗格中。|  
|[CDockablePane::EnableAutohideAll](../Topic/CDockablePane::EnableAutohideAll.md)|与其他窗格一起启动或禁用此窗格的自动隐藏模式在容器。|  
|[CDockablePane::EnableGripper](../Topic/CDockablePane::EnableGripper.md)|显示或隐藏声明\(手柄）。|  
|[CDockablePane::GetAHRestoredRect](../Topic/CDockablePane::GetAHRestoredRect.md)|在自动隐藏模式指定窗格的位置，当可见。|  
|[CDockablePane::GetAHSlideMode](../Topic/CDockablePane::GetAHSlideMode.md)|检索窗格的自动隐藏幻灯片模式。|  
|`CDockablePane::GetAutoHideButton`|内部使用。|  
|`CDockablePane::GetAutoHideToolBar`|内部使用。|  
|[CDockablePane::GetCaptionHeight](../Topic/CDockablePane::GetCaptionHeight.md)|返回当前声明的高度。|  
|[CDockablePane::GetDefaultPaneDivider](../Topic/CDockablePane::GetDefaultPaneDivider.md)|返回窗格的容器的默认窗格分隔符。|  
|[CDockablePane::GetDockingStatus](../Topic/CDockablePane::GetDockingStatus.md)|确定窗格的能力停靠根据提供的指针位置。|  
|[CDockablePane::GetDragSensitivity](../Topic/CDockablePane::GetDragSensitivity.md)|返回停靠窗格的拖动区分。|  
|[CDockablePane::GetLastPercentInPaneContainer](../Topic/CDockablePane::GetLastPercentInPaneContainer.md)|检索窗格在其容器中占用空间的百分比。|  
|[CDockablePane::GetTabArea](../Topic/CDockablePane::GetTabArea.md)|检索窗格中的选项卡区域。|  
|[CDockablePane::GetTabbedPaneRTC](../Topic/CDockablePane::GetTabbedPaneRTC.md)|返回有关创建的一个选项卡式窗口的运行时选件类信息，而另一个窗格停靠到当前窗格。|  
|[CDockablePane::HasAutoHideMode](../Topic/CDockablePane::HasAutoHideMode.md)|指定停靠窗格是否可以切换到自动隐藏模式。|  
|[CDockablePane::HitTest](../Topic/CDockablePane::HitTest.md)|在用户单击鼠标的窗格指定特定位置。|  
|`CDockablePane::IsAccessibilityCompatible`|内部使用。|  
|[CDockablePane::IsAutohideAllEnabled](../Topic/CDockablePane::IsAutohideAllEnabled.md)|指示停靠窗格和其他窗格在容器是在自动隐藏模式可将。|  
|[CDockablePane::IsAutoHideMode](../Topic/CDockablePane::IsAutoHideMode.md)|确定窗格是否在自动隐藏模式。|  
|`CDockablePane::IsChangeState`|内部使用。|  
|[CDockablePane::IsDocked](../Topic/CDockablePane::IsDocked.md)|确定当前窗格是停靠。|  
|[CDockablePane::IsHideInAutoHideMode](../Topic/CDockablePane::IsHideInAutoHideMode.md)|确定是在自动隐藏模式下窗格的行为，则通过调用 `ShowPane`显示\(或隐藏）。|  
|[CDockablePane::IsInFloatingMultiPaneFrameWnd](../Topic/CDockablePane::IsInFloatingMultiPaneFrameWnd.md)|指定窗格是否在多窗格框架窗口。|  
|[CDockablePane::IsResizable](../Topic/CDockablePane::IsResizable.md)|指定窗格是否可调整大小的。|  
|[CDockablePane::IsTabLocationBottom](../Topic/CDockablePane::IsTabLocationBottom.md)|指定选项是否位于窗格的顶部或底部。|  
|[CDockablePane::IsTracked](../Topic/CDockablePane::IsTracked.md)|指定窗格是由用户拖动。|  
|[CDockablePane::IsVisible](../Topic/CDockablePane::IsVisible.md)|确定当前窗格是否可见。|  
|[CDockablePane::LoadState](http://msdn.microsoft.com/zh-cn/96110136-4f46-4764-8a76-3b4abaf77917)|内部使用。|  
|[CDockablePane::OnAfterChangeParent](../Topic/CDockablePane::OnAfterChangeParent.md)|调用由结构，在窗格的父级更改为。  （重写 [CPane::OnAfterChangeParent](../Topic/CPane::OnAfterChangeParent.md)。）|  
|[CDockablePane::OnAfterDockFromMiniFrame](../Topic/CDockablePane::OnAfterDockFromMiniFrame.md)|调用由结构，在一个浮船坞栏停靠在框架窗口。|  
|[CDockablePane::OnBeforeChangeParent](../Topic/CDockablePane::OnBeforeChangeParent.md)|调用由结构，在窗格的父会发生更改。  （重写 [CPane::OnBeforeChangeParent](../Topic/CPane::OnBeforeChangeParent.md)。）|  
|[CDockablePane::OnBeforeFloat](../Topic/CDockablePane::OnBeforeFloat.md)|调用由结构，当窗格将浮动。  （重写 [CPane::OnBeforeFloat](../Topic/CPane::OnBeforeFloat.md)。）|  
|[CDockablePane::RemoveFromDefaultPaneDividier](../Topic/CDockablePane::RemoveFromDefaultPaneDividier.md)|在窗格停靠时，框架调用此方法。|  
|[CDockablePane::ReplacePane](../Topic/CDockablePane::ReplacePane.md)|用指定的窗格替换窗格。|  
|[CDockablePane::RestoreDefaultPaneDivider](../Topic/CDockablePane::RestoreDefaultPaneDivider.md)|在窗格中，将还原默认窗格分隔符，框架调用此方法。|  
|`CDockablePane::SaveState`|内部使用。|  
|`CDockablePane::Serialize`|序列化窗格。  （重写 `CBasePane::Serialize`。）|  
|[CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md)|切换在可见和自动隐藏模式之间的停靠窗格。|  
|[CDockablePane::SetAutoHideParents](../Topic/CDockablePane::SetAutoHideParents.md)|设置自动隐藏按钮和自动隐藏"窗格中。|  
|`CDockablePane::SetDefaultPaneDivider`|内部使用。|  
|[CDockablePane::SetLastPercentInPaneContainer](../Topic/CDockablePane::SetLastPercentInPaneContainer.md)|设置窗格在其容器中占用空间的百分比。|  
|`CDockablePane::SetResizeMode`|内部使用。|  
|[CDockablePane::SetRestoredDefaultPaneDivider](../Topic/CDockablePane::SetRestoredDefaultPaneDivider.md)|设置还原的默认窗格分隔符。|  
|[CDockablePane::SetTabbedPaneRTC](../Topic/CDockablePane::SetTabbedPaneRTC.md)|设置创建的一个选项卡式窗口的运行时选件类信息，在两个窗格同时停靠。|  
|[CDockablePane::ShowPane](../Topic/CDockablePane::ShowPane.md)|显示或隐藏窗格。|  
|[CDockablePane::Slide](../Topic/CDockablePane::Slide.md)|显示或隐藏具有个动画的一个窗格哪些显示仅在窗格中自动隐藏模式时。|  
|[CDockablePane::ToggleAutoHide](../Topic/CDockablePane::ToggleAutoHide.md)|触发器自动隐藏模式。  （重写 [CPane::ToggleAutoHide](../Topic/CPane::ToggleAutoHide.md)。）|  
|[CDockablePane::UndockPane](../Topic/CDockablePane::UndockPane.md)|停靠到主框架窗口或袖珍框架窗口容器的一个窗格。|  
|`CDockablePane::UnSetAutoHideMode`|内部使用。  若要设置自动隐藏模式，请使用 [CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md)|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CDockablePane::CheckAutoHideCondition](../Topic/CDockablePane::CheckAutoHideCondition.md)|确定停靠窗格是否为隐藏的\(在自动隐藏模式）。|  
|[CDockablePane::CheckStopSlideCondition](../Topic/CDockablePane::CheckStopSlideCondition.md)|在自动隐藏停靠窗格应停止个，确定。|  
|[CDockablePane::DrawCaption](../Topic/CDockablePane::DrawCaption.md)|绘制停靠窗格声明\(手柄）。|  
|[CDockablePane::OnPressButtons](../Topic/CDockablePane::OnPressButtons.md)|调用除了 `AFX_HTCLOSE` 和 `AFX_HTMAXBUTTON` 按钮外，那么，当用户按一个声明按钮。|  
|[CDockablePane::OnSlide](../Topic/CDockablePane::OnSlide.md)|调用框架呈现自动隐藏幻灯片效果，在窗格显示或隐藏。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDockablePane::m\_bDisableAnimation](../Topic/CDockablePane::m_bDisableAnimation.md)|指定停靠窗格的自动隐藏动画是否禁用。|  
|[CDockablePane::m\_bHideInAutoHideMode](../Topic/CDockablePane::m_bHideInAutoHideMode.md)|在窗格中自动隐藏模式时，确定窗格的行为。|  
|[CDockablePane::m\_nSlideSteps](../Topic/CDockablePane::m_nSlideSteps.md)|在自动隐藏模式时，显示或隐藏，指定窗格的动画速度。|  
  
## 备注  
 `CDockablePane` 实现以下功能:  
  
-   停靠一个窗格。主框架窗口。  
  
-   切换窗格自动隐藏模式。  
  
-   附加一个窗格到一个选项卡式窗口。  
  
-   浮动在袖珍框架窗口的一个窗格。  
  
-   停靠窗格将在袖珍框架窗口浮动另一个窗格。  
  
-   调整窗格。  
  
-   停靠窗格的加载和保存状态。  
  
    > [!NOTE]
    >  状态信息保存到Windows注册表。  
  
-   创建有或没有声明的一个窗格。  该声明可以具有文本标签，并且可以用渐变颜色。  
  
-   拖动窗格，同时显示窗格的内容时  
  
-   拖动窗格，同时显示拖动矩形时。  
  
 若要使用停靠窗格在应用程序中，从 `CDockablePane` 选件类派生您的窗格选件类。  在窗体中嵌入派生的对象向主框架窗口对象或向windows对象的控制窗格实例。  然后，在处理在主框架窗口时，的 `WM_CREATE` 消息调用 [CDockablePane::Create](../Topic/CDockablePane::Create.md) 方法或 [CDockablePane::CreateEx](../Topic/CDockablePane::CreateEx.md) 方法。  最后，通过调用 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)、 [CBasePane::DockPane](../Topic/CBasePane::DockPane.md)或 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md)设置窗格对象。  
  
## 自定义提示  
 以下提示应用于 `CDockablePane` 对象:  
  
-   如果调用非选项卡式两个 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md)，可停靠窗格，指针到一个选项卡式窗口在 `ppTabbedControlBar` 参数将返回。  通过使用此参数，可以继续添加选项。选项卡式窗口。  
  
-   由 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md) 创建的此选项卡式窗格取决于 `pTabControlBarAttachTo` 参数的 `CDockablePane` 对象。  可以调用 [CDockablePane::SetTabbedPaneRTC](../Topic/CDockablePane::SetTabbedPaneRTC.md) 设置 `CDockablePane` 将创建一个选项卡式窗格。  首次创建 `CDockablePane`时，默认类型取决于 [CDockablePane::Create](../Topic/CDockablePane::Create.md)`dwTabbedStyle`。  如果 `dwTabbedStyle` 是AFX\_CBRS\_OUTLOOK\_TABS默认类型为 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md);如果 `dwTabbedStyle` 是AFX\_CBRS\_REGULAR\_TABS默认类型为 [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md)。  
  
-   如果要停靠一个停靠窗格到另一个，请调用 [CDockablePane::DockToWindow](../Topic/CDockablePane::DockToWindow.md) 方法。  在调用此方法之前，必须停靠窗格原始位置。  
  
-   成员变量的 [CDockablePane::m\_bHideInAutoHideMode](../Topic/CDockablePane::m_bHideInAutoHideMode.md) 控件停靠窗格如何在自动隐藏模式的行为，当您调用 [CDockablePane::ShowPane](../Topic/CDockablePane::ShowPane.md)。  如果该成员变量设置为 `TRUE`，可停靠窗格及其自动隐藏"按钮被隐藏。  否则，它们和缩小将滑。  
  
-   可以通过设置 [CDockablePane::m\_bDisableAnimation](../Topic/CDockablePane::m_bDisableAnimation.md) 成员变量禁用自动隐藏动画。`TRUE`。  
  
## 示例  
 通过在 `CDockablePane` 选件类，中的各种方法下面的示例演示如何配置 `CDockablePane` 对象。  示例演示如何启用"自动隐藏停靠窗格的所有功能，启用声明或手柄，启动自动隐藏模式，显示窗格和对自动隐藏模式下的窗格中进行动画处理。  此代码段是 [Visual Studio演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#27](../../mfc/codesnippet/CPP/cdockablepane-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#28](../../mfc/codesnippet/CPP/cdockablepane-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
## 要求  
 **标头:** afxDockablePane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)