---
title: "CFrameWndEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFrameWndEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFrameWndEx class"
ms.assetid: 5830aca8-4a21-4f31-91f1-dd5477ffcc8d
caps.latest.revision: 39
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFrameWndEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现的Windows函数单文档界面\(SDI\)利用率、线程或弹出框架窗口，并为管理窗口提供成员。  它扩展 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 选件类。  
  
## 语法  
  
```  
class CFrameWndEx : public CFrameWnd  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFrameWndEx::ActiveItemRecalcLayout](../Topic/CFrameWndEx::ActiveItemRecalcLayout.md)|调整OLE客户端项目和框架的工作区的格式。|  
|`CFrameWndEx::AddDockSite`|未使用此方法。|  
|[CFrameWndEx::AddPane](../Topic/CFrameWndEx::AddPane.md)|注册停靠管理器的控件条。|  
|[CFrameWndEx::AdjustDockingLayout](../Topic/CFrameWndEx::AdjustDockingLayout.md)|重新停靠到框架窗口所有窗格的格式。|  
|[CFrameWndEx::DelayUpdateFrameMenu](../Topic/CFrameWndEx::DelayUpdateFrameMenu.md)|在命令处理空闲时，将框架菜单上的并进行更新。|  
|[CFrameWndEx::DockPane](../Topic/CFrameWndEx::DockPane.md)|停靠指定的窗格到框架窗口。|  
|[CFrameWndEx::DockPaneLeftOf](../Topic/CFrameWndEx::DockPaneLeftOf.md)|停靠在另一个窗格左侧的一个窗格。|  
|[CFrameWndEx::EnableAutoHidePanes](../Topic/CFrameWndEx::EnableAutoHidePanes.md)|当它们停靠在主框架窗口时，的指定端启动窗格"自动隐藏"模式。|  
|[CFrameWndEx::EnableDocking](../Topic/CFrameWndEx::EnableDocking.md)|启用属于框架窗口窗格的停靠。|  
|[CFrameWndEx::EnableFullScreenMainMenu](../Topic/CFrameWndEx::EnableFullScreenMainMenu.md)|显示或隐藏主菜单在一个全屏模式。|  
|[CFrameWndEx::EnableFullScreenMode](../Topic/CFrameWndEx::EnableFullScreenMode.md)|启动框架窗口的"全屏"模式。|  
|[CFrameWndEx::EnableLoadDockState](../Topic/CFrameWndEx::EnableLoadDockState.md)|启用或禁用停靠状态的加载。|  
|[CFrameWndEx::EnablePaneMenu](../Topic/CFrameWndEx::EnablePaneMenu.md)|启用或禁用自动处理窗格菜单。|  
|[CFrameWndEx::GetActivePopup](../Topic/CFrameWndEx::GetActivePopup.md)|返回指向当前显示的弹出菜单。|  
|[CFrameWndEx::GetDefaultResId](../Topic/CFrameWndEx::GetDefaultResId.md)|返回您指定的资源ID框架时加载了框架窗口。|  
|[CFrameWndEx::GetDockingManager](../Topic/CFrameWndEx::GetDockingManager.md)|检索框架窗口的 [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) 对象。|  
|[CFrameWndEx::GetMenuBar](../Topic/CFrameWndEx::GetMenuBar.md)|返回指向附加的菜单栏对象到框架窗口。|  
|[CFrameWndEx::GetPane](../Topic/CFrameWndEx::GetPane.md)|返回指向具有指定的ID.的窗格|  
|[CFrameWndEx::GetRibbonBar](../Topic/CFrameWndEx::GetRibbonBar.md)|检索框架的功能区栏控件。|  
|[CFrameWndEx::GetTearOffBars](../Topic/CFrameWndEx::GetTearOffBars.md)|返回的窗格对象列表。拖曳状态。|  
|[CFrameWndEx::GetToolbarButtonToolTipText](../Topic/CFrameWndEx::GetToolbarButtonToolTipText.md)|调用由结构，当应用程序显示工具栏按钮的工具提示。|  
|[CFrameWndEx::InsertPane](../Topic/CFrameWndEx::InsertPane.md)|注册了停靠管理器的一个窗格。|  
|[CFrameWndEx::IsFullScreen](../Topic/CFrameWndEx::IsFullScreen.md)|确定框架窗口是否在"全屏"模式。|  
|[CFrameWndEx::IsMenuBarAvailable](../Topic/CFrameWndEx::IsMenuBarAvailable.md)|确定与菜单栏对象的指针是否有效。|  
|[CFrameWndEx::IsPointNearDockSite](../Topic/CFrameWndEx::IsPointNearDockSite.md)|指示点是否位于对齐区域。|  
|[CFrameWndEx::IsPrintPreview](../Topic/CFrameWndEx::IsPrintPreview.md)|指示框架窗口是否在打印预览模式。|  
|[CFrameWndEx::LoadFrame](../Topic/CFrameWndEx::LoadFrame.md)|此方法在构造后调用创建框架窗口和填充其资源。|  
|[CFrameWndEx::NegotiateBorderSpace](../Topic/CFrameWndEx::NegotiateBorderSpace.md)|实现OLE客户端协商边框。|  
|[CFrameWndEx::OnActivate](../Topic/CFrameWndEx::OnActivate.md)|当用户输入被切换到或其他帧时，框架调用此方法。|  
|[CFrameWndEx::OnActivateApp](../Topic/CFrameWndEx::OnActivateApp.md)|调用由结构，当应用程序选择或取消选择。|  
|[CFrameWndEx::OnChangeVisualManager](../Topic/CFrameWndEx::OnChangeVisualManager.md)|调用由结构，当对框架的更改要求对视觉管理器的更改。|  
|[CFrameWndEx::OnClose](../Topic/CFrameWndEx::OnClose.md)|框架调用此方法关闭帧。|  
|[CFrameWndEx::OnCloseDockingPane](../Topic/CFrameWndEx::OnCloseDockingPane.md)|调用由结构，当用户在停靠窗格 **关闭** 单击按钮。|  
|[CFrameWndEx::OnCloseMiniFrame](../Topic/CFrameWndEx::OnCloseMiniFrame.md)|调用由结构，当用户在浮动mini框架窗口 **关闭** 单击按钮。|  
|[CFrameWndEx::OnClosePopupMenu](../Topic/CFrameWndEx::OnClosePopupMenu.md)|调用由结构，当一个有效的弹出菜单操作WM\_DESTROY消息。|  
|[CFrameWndEx::OnCmdMsg](../Topic/CFrameWndEx::OnCmdMsg.md)|计划命令消息。|  
|[CFrameWndEx::OnContextHelp](../Topic/CFrameWndEx::OnContextHelp.md)|调用由框架显示上下文相关帮助。|  
|[CFrameWndEx::OnCreate](../Topic/CFrameWndEx::OnCreate.md)|调用由框架在框架的后面创建。|  
|[CFrameWndEx::OnDestroy](../Topic/CFrameWndEx::OnDestroy.md)|调用由结构，当销毁框架。|  
|[CFrameWndEx::OnDrawMenuImage](../Topic/CFrameWndEx::OnDrawMenuImage.md)|调用由结构，当应用程序绘制图像与菜单项。|  
|[CFrameWndEx::OnDrawMenuLogo](../Topic/CFrameWndEx::OnDrawMenuLogo.md)|调用由结构，当 `CMFCPopupMenu` 对象处理 [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) 消息。|  
|[CFrameWndEx::OnDWMCompositionChanged](../Topic/CFrameWndEx::OnDWMCompositionChanged.md)|调用由结构，在桌面窗口管理器\(DWM\)配置已启用或禁用了。|  
|[CFrameWndEx::OnExitSizeMove](../Topic/CFrameWndEx::OnExitSizeMove.md)|调用由框架，这些帧停止移动或调整。|  
|[CFrameWndEx::OnGetMinMaxInfo](../Topic/CFrameWndEx::OnGetMinMaxInfo.md)|调用由框架，这些帧调整大小设置窗口的尺寸限制。|  
|[CFrameWndEx::OnIdleUpdateCmdUI](../Topic/CFrameWndEx::OnIdleUpdateCmdUI.md)|调用由框架更新帧示，当命令处理idle。|  
|[CFrameWndEx::OnLButtonDown](../Topic/CFrameWndEx::OnLButtonDown.md)|当用户按下鼠标左键时，框架调用此方法。|  
|[CFrameWndEx::OnLButtonUp](../Topic/CFrameWndEx::OnLButtonUp.md)|当用户松开鼠标左键时，框架调用此方法。|  
|[CFrameWndEx::OnMenuButtonToolHitTest](../Topic/CFrameWndEx::OnMenuButtonToolHitTest.md)|调用由结构，当 `CMFCToolBarButton` 对象处理 `WM_NCHITTEST` 消息。|  
|[CFrameWndEx::OnMenuChar](../Topic/CFrameWndEx::OnMenuChar.md)|调用由框架，在菜单上显示时和用户按下不对应命令的一个键。|  
|[CFrameWndEx::OnMouseMove](../Topic/CFrameWndEx::OnMouseMove.md)|当指针移动时，框架调用此方法。|  
|[CFrameWndEx::OnMoveMiniFrame](../Topic/CFrameWndEx::OnMoveMiniFrame.md)|调用由结构，当窗口窗格移动。|  
|[CFrameWndEx::OnNcActivate](../Topic/CFrameWndEx::OnNcActivate.md)|调用由框架，则必须重绘帧的非工作区指示在活动状态的更改。|  
|[CFrameWndEx::OnNcCalcSize](../Topic/CFrameWndEx::OnNcCalcSize.md)|调用由框架，则必须计算工作区的大小和位置。|  
|[CFrameWndEx::OnNcHitTest](../Topic/CFrameWndEx::OnNcHitTest.md)|调用由结构，当指针移动或，按下鼠标按钮或释放。|  
|[CFrameWndEx::OnNcMouseMove](../Topic/CFrameWndEx::OnNcMouseMove.md)|调用由结构，当指针在非工作区移动。|  
|[CFrameWndEx::OnNcPaint](../Topic/CFrameWndEx::OnNcPaint.md)|调用由框架，则必须绘制非工作区。|  
|[CFrameWndEx::OnPaneCheck](../Topic/CFrameWndEx::OnPaneCheck.md)|调用由结构窗格控件的可见性。|  
|[CFrameWndEx::OnPostPreviewFrame](../Topic/CFrameWndEx::OnPostPreviewFrame.md)|调用由结构，当用户更改了打印预览模式。|  
|[CFrameWndEx::OnPowerBroadcast](../Topic/CFrameWndEx::OnPowerBroadcast.md)|调用由结构，当电源管理事件发生。|  
|[CFrameWndEx::OnSetMenu](../Topic/CFrameWndEx::OnSetMenu.md)|调用由框架替换框架窗口菜单。|  
|[CFrameWndEx::OnSetPreviewMode](../Topic/CFrameWndEx::OnSetPreviewMode.md)|调用由框架将框架的打印预览模式。|  
|[CFrameWndEx::OnSetText](../Topic/CFrameWndEx::OnSetText.md)|调用由框架设置窗口的文本。|  
|[CFrameWndEx::OnShowCustomizePane](../Topic/CFrameWndEx::OnShowCustomizePane.md)|调用由框架，快速自定义时窗格启用。|  
|[CFrameWndEx::OnShowPanes](../Topic/CFrameWndEx::OnShowPanes.md)|调用由结构显示或隐藏窗格。|  
|[CFrameWndEx::OnShowPopupMenu](../Topic/CFrameWndEx::OnShowPopupMenu.md)|调用由结构，当弹出菜单启用。|  
|[CFrameWndEx::OnSize](../Topic/CFrameWndEx::OnSize.md)|在帧大小更改后，框架调用此方法。|  
|[CFrameWndEx::OnSizing](../Topic/CFrameWndEx::OnSizing.md)|当用户调整帧时，框架调用此方法。|  
|[CFrameWndEx::OnSysColorChange](../Topic/CFrameWndEx::OnSysColorChange.md)|调用由结构，当系统颜色更改。|  
|[CFrameWndEx::OnTearOffMenu](../Topic/CFrameWndEx::OnTearOffMenu.md)|调用由结构，当有一个拖曳栏的菜单上启用。|  
|[CFrameWndEx::OnToolbarContextMenu](../Topic/CFrameWndEx::OnToolbarContextMenu.md)|调用由框架生成工具栏上下文菜单。|  
|[CFrameWndEx::OnToolbarCreateNew](../Topic/CFrameWndEx::OnToolbarCreateNew.md)|框架调用此方法来创建新工具栏。|  
|[CFrameWndEx::OnToolbarDelete](../Topic/CFrameWndEx::OnToolbarDelete.md)|调用由结构，在工具栏中删除。|  
|[CFrameWndEx::OnUpdateFrameMenu](../Topic/CFrameWndEx::OnUpdateFrameMenu.md)|调用由框架设置框架菜单。|  
|[CFrameWndEx::OnUpdateFrameTitle](../Topic/CFrameWndEx::OnUpdateFrameTitle.md)|框架调用此方法将更新框架窗口的标题栏。|  
|[CFrameWndEx::OnUpdatePaneMenu](../Topic/CFrameWndEx::OnUpdatePaneMenu.md)|调用由框架更新窗格菜单。|  
|[CFrameWndEx::OnWindowPosChanged](../Topic/CFrameWndEx::OnWindowPosChanged.md)|调用由结构，当帧大小、位置或z顺序更改为由于调用windows管理方法。|  
|[CFrameWndEx::PaneFromPoint](../Topic/CFrameWndEx::PaneFromPoint.md)|返回包含指定的点停靠窗格。|  
|[CFrameWndEx::PreTranslateMessage](../Topic/CFrameWndEx::PreTranslateMessage.md)|处理特定窗口消息，在计划之前它们。|  
|[CFrameWndEx::RecalcLayout](../Topic/CFrameWndEx::RecalcLayout.md)|调整帧及其子窗口的格式。|  
|[CFrameWndEx::RemovePaneFromDockManager](../Topic/CFrameWndEx::RemovePaneFromDockManager.md)|注销窗格和从内部在停靠管理器移除该列表。|  
|[CFrameWndEx::SetDockState](../Topic/CFrameWndEx::SetDockState.md)|还原停靠布局将存储在注册表中的停靠状态。|  
|[CFrameWndEx::SetPrintPreviewFrame](../Topic/CFrameWndEx::SetPrintPreviewFrame.md)|设置打印预览框架窗口。|  
|[CFrameWndEx::SetupToolbarMenu](../Topic/CFrameWndEx::SetupToolbarMenu.md)|插入用户定义的命令到工具栏菜单中。|  
|[CFrameWndEx::ShowFullScreen](../Topic/CFrameWndEx::ShowFullScreen.md)|切换到全屏和普通模式之间的主框架。|  
|[CFrameWndEx::ShowPane](../Topic/CFrameWndEx::ShowPane.md)|显示或隐藏指定的窗格。|  
|[CFrameWndEx::UpdateCaption](../Topic/CFrameWndEx::UpdateCaption.md)|调用由框架更新窗架说明。|  
|[CFrameWndEx::WinHelp](../Topic/CFrameWndEx::WinHelp.md)|调用 `WinHelp` 应用程序或上下文相关的帮助。|  
  
## 示例  
 下面的示例演示如何继承 `CFrameWndEx` 选件类的选件类。  示例阐释了子类的方法签名，以及如何重写 `OnShowPopupMenu` 方法。  此代码段是 [Word填充示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#3](../../mfc/reference/codesnippet/CPP/cframewndex-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#4](../../mfc/reference/codesnippet/CPP/cframewndex-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CFrameWndEx](../../mfc/reference/cframewndex-class.md)  
  
## 要求  
 **标头:** afxframewndex.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)