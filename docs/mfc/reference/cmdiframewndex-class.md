---
title: "CMDIFrameWndEx 类 | Microsoft Docs"
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
  - "CMDIFrameWndEx.AddDockSite"
  - "CMDIFrameWndEx"
  - "CMDIFrameWndEx::AddDockSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDIFrameWndEx 类"
ms.assetid: dbcafcb3-9a7a-4f11-9dfe-ba57565c81d0
caps.latest.revision: 42
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMDIFrameWndEx 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

扩展 [CMDIFrameWnd](../../mfc/reference/cframewnd-class.md)的功能，多文档界面 \(MDI\) 框架窗口的窗口。  
  
## 语法  
  
```  
class CMDIFrameWndEx : public CMDIFrameWnd  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMDIFrameWndEx::ActiveItemRecalcLayout](../Topic/CMDIFrameWndEx::ActiveItemRecalcLayout.md)|计算活动项的布局。|  
|`CMDIFrameWndEx::AddDockSite`|未使用此方法。|  
|[CMDIFrameWndEx::AddPane](../Topic/CMDIFrameWndEx::AddPane.md)|注册了停靠管理器的一个窗格。|  
|[CMDIFrameWndEx::AdjustClientArea](../Topic/CMDIFrameWndEx::AdjustClientArea.md)|减少客户端区域允许边框。|  
|[CMDIFrameWndEx::AdjustDockingLayout](../Topic/CMDIFrameWndEx::AdjustDockingLayout.md)|重新停靠的窗格布局。|  
|[CMDIFrameWndEx::AreMDITabs](../Topic/CMDIFrameWndEx::AreMDITabs.md)|确定 MDI 选项是否功能或 MDI 选项卡式组功能是否已启用。|  
|[CMDIFrameWndEx::CanCovertControlBarToMDIChild](../Topic/CMDIFrameWndEx::CanCovertControlBarToMDIChild.md)|调用由框架确定框架窗口是否可以转换停靠窗格为选项卡式文档。|  
|[CMDIFrameWndEx::ControlBarToTabbedDocument](../Topic/CMDIFrameWndEx::ControlBarToTabbedDocument.md)|将指定的停靠的窗格为选项卡式文档。|  
|[CMDIFrameWndEx::CreateDocumentWindow](../Topic/CMDIFrameWndEx::CreateDocumentWindow.md)|创建子文档窗口。|  
|[CMDIFrameWndEx::CreateNewWindow](../Topic/CMDIFrameWndEx::CreateNewWindow.md)|调用由框架创建一个新窗口。|  
|`CMDIFrameWndEx::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMDIFrameWndEx::DockPane](../Topic/CMDIFrameWndEx::DockPane.md)|停靠指定的窗格到框架窗口。|  
|[CMDIFrameWndEx::DockPaneLeftOf](../Topic/CMDIFrameWndEx::DockPaneLeftOf.md)|停靠在另一个窗格左侧的一个窗格。|  
|[CMDIFrameWndEx::EnableAutoHidePanes](../Topic/CMDIFrameWndEx::EnableAutoHidePanes.md)|当它们停靠在主框架窗口时，的指定端启动窗格"自动隐藏"模式。|  
|[CMDIFrameWndEx::EnableDocking](../Topic/CMDIFrameWndEx::EnableDocking.md)|启用属于 MDI 框架窗口窗格的停靠。|  
|[CMDIFrameWndEx::EnableFullScreenMainMenu](../Topic/CMDIFrameWndEx::EnableFullScreenMainMenu.md)|显示或隐藏主菜单在"全屏"模式。|  
|[CMDIFrameWndEx::EnableFullScreenMode](../Topic/CMDIFrameWndEx::EnableFullScreenMode.md)|启动框架窗口的"全屏"模式。|  
|[CMDIFrameWndEx::EnableLoadDockState](../Topic/CMDIFrameWndEx::EnableLoadDockState.md)|启用或禁用停靠状态的加载。|  
|[CMDIFrameWndEx::EnableMDITabbedGroups](../Topic/CMDIFrameWndEx::EnableMDITabbedGroups.md)|启用或禁用 MDI 选项卡式组功能。|  
|[CMDIFrameWndEx::EnableMDITabs](../Topic/CMDIFrameWndEx::EnableMDITabs.md)|启用或禁用 MDI 可选功能。  当启用，框架窗口显示每个 MDI 子窗口的选项。|  
|[CMDIFrameWndEx::EnableMDITabsLastActiveActivation](../Topic/CMDIFrameWndEx::EnableMDITabsLastActiveActivation.md)|指定是否应激活最后一个有效的选项，当用户关闭当前选项卡。|  
|[CMDIFrameWndEx::EnablePaneMenu](../Topic/CMDIFrameWndEx::EnablePaneMenu.md)|启用或禁用弹出菜单窗格的自动创建和管理，显示应用程序"窗格中。  .|  
|[CMDIFrameWndEx::EnableWindowsDialog](../Topic/CMDIFrameWndEx::EnableWindowsDialog.md)|将命令 ID 调用 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) 对话框的菜单项。|  
|[CMDIFrameWndEx::GetActivePopup](../Topic/CMDIFrameWndEx::GetActivePopup.md)|返回指向当前显示的弹出菜单。|  
|[CMDIFrameWndEx::GetPane](../Topic/CMDIFrameWndEx::GetPane.md)|返回指向具有指定的控件 ID. 的窗格|  
|[CMDIFrameWndEx::GetDefaultResId](../Topic/CMDIFrameWndEx::GetDefaultResId.md)|返回 MDI 框架窗口的共享资源 ID。|  
|[CMDIFrameWndEx::GetMDITabGroups](../Topic/CMDIFrameWndEx::GetMDITabGroups.md)|返回 MDI 选项卡式窗口列表。|  
|[CMDIFrameWndEx::GetMDITabs](../Topic/CMDIFrameWndEx::GetMDITabs.md)|返回对带下划线的选项卡式窗口。|  
|[CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems](../Topic/CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems.md)|返回确定标志的组合什么上下文菜单项是有效的，当 MDI 选项卡式组功能处于启用状态。|  
|[CMDIFrameWndEx::GetMenuBar](../Topic/CMDIFrameWndEx::GetMenuBar.md)|返回指向附加个菜单栏对象到框架窗口。|  
|[CMDIFrameWndEx::GetRibbonBar](../Topic/CMDIFrameWndEx::GetRibbonBar.md)|检索框架的功能区栏控件。|  
|[CMDIFrameWndEx::GetTearOffBars](../Topic/CMDIFrameWndEx::GetTearOffBars.md)|返回 [CPane](../../mfc/reference/cpane-class.md)列表\-在撕掉状态的派生对象。|  
|`CMDIFrameWndEx::GetThisClass`|调用由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMDIFrameWndEx::GetToolbarButtonToolTipText](../Topic/CMDIFrameWndEx::GetToolbarButtonToolTipText.md)|调用由结构，当应用程序显示工具栏按钮的工具提示。|  
|[CMDIFrameWndEx::InsertPane](../Topic/CMDIFrameWndEx::InsertPane.md)|注册了停靠管理器中指定的窗格。|  
|[CMDIFrameWndEx::IsFullScreen](../Topic/CMDIFrameWndEx::IsFullScreen.md)|确定框架窗口是否在"全屏"模式。|  
|[CMDIFrameWndEx::IsMDITabbedGroup](../Topic/CMDIFrameWndEx::IsMDITabbedGroup.md)|确定 MDI 选项卡式组功能是否已启用。|  
|[CMDIFrameWndEx::IsMemberOfMDITabGroup](../Topic/CMDIFrameWndEx::IsMemberOfMDITabGroup.md)|确定指定的选项卡式窗口是否在 MDI 选项卡式组中的窗口的列表。|  
|[CMDIFrameWndEx::IsMenuBarAvailable](../Topic/CMDIFrameWndEx::IsMenuBarAvailable.md)|确定框架窗口是否具有菜单栏。|  
|[CMDIFrameWndEx::IsPointNearDockSite](../Topic/CMDIFrameWndEx::IsPointNearDockSite.md)|确定指定的点是否在停靠站点附近。|  
|[CMDIFrameWndEx::IsPrintPreview](../Topic/CMDIFrameWndEx::IsPrintPreview.md)|确定框架窗口是否在打印预览模式。|  
|[CMDIFrameWndEx::LoadFrame](../Topic/CMDIFrameWndEx::LoadFrame.md)|创建从资源信息的框架窗口。  \(重写 `CMDIFrameWnd::LoadFrame`。\)|  
|[CMDIFrameWndEx::LoadMDIState](../Topic/CMDIFrameWndEx::LoadMDIState.md)|加载 MDI 选项卡式组指定的格式，并列出以前打开文档。|  
|[CMDIFrameWndEx::MDITabMoveToNextGroup](../Topic/CMDIFrameWndEx::MDITabMoveToNextGroup.md)|从当前活动的选项卡式窗口之间有效选项移到下一个或上一选项卡式组。|  
|[CMDIFrameWndEx::MDITabNewGroup](../Topic/CMDIFrameWndEx::MDITabNewGroup.md)|创建一个窗口的新选项卡式组。|  
|[CMDIFrameWndEx::NegotiateBorderSpace](../Topic/CMDIFrameWndEx::NegotiateBorderSpace.md)|在 OLE 就地激活时协调在框架窗口的边框空间。|  
|[CMDIFrameWndEx::OnCloseDockingPane](../Topic/CMDIFrameWndEx::OnCloseDockingPane.md)|调用由结构，当用户在一个停靠窗格中单击 **关闭** 按钮。|  
|[CMDIFrameWndEx::OnCloseMiniFrame](../Topic/CMDIFrameWndEx::OnCloseMiniFrame.md)|调用由结构，当用户在浮动 mini 框架窗口 **关闭** 单击按钮。|  
|[CMDIFrameWndEx::OnClosePopupMenu](../Topic/CMDIFrameWndEx::OnClosePopupMenu.md)|调用由结构，当一个有效的弹出菜单操作 `WM_DESTROY` 消息。|  
|[CMDIFrameWndEx::OnCmdMsg](../Topic/CMDIFrameWndEx::OnCmdMsg.md)|调用由框架路由和计划命令消息和更新命令用户界面对象。|  
|[CMDIFrameWndEx::OnDrawMenuImage](../Topic/CMDIFrameWndEx::OnDrawMenuImage.md)|调用由结构，在与菜单项绘制图像。|  
|[CMDIFrameWndEx::OnDrawMenuLogo](../Topic/CMDIFrameWndEx::OnDrawMenuLogo.md)|调用由结构，当 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)处理 `WM_PAINT` 消息。|  
|[CMDIFrameWndEx::OnEraseMDIClientBackground](../Topic/CMDIFrameWndEx::OnEraseMDIClientBackground.md)|调用由结构，当 MDI 框架窗口处理 `WM_ERASEBKGND` 消息。|  
|[CMDIFrameWndEx::OnMenuButtonToolHitTest](../Topic/CMDIFrameWndEx::OnMenuButtonToolHitTest.md)|调用由结构，当 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)对象处理 `WM_NCHITTEST` 消息。|  
|[CMDIFrameWndEx::OnMoveMiniFrame](../Topic/CMDIFrameWndEx::OnMoveMiniFrame.md)|调用由框架移动和框架窗口。|  
|[CMDIFrameWndEx::OnSetPreviewMode](../Topic/CMDIFrameWndEx::OnSetPreviewMode.md)|设置应用程序的主框架窗口打印预览模式。  \(重写 [CFrameWnd::OnSetPreviewMode](../Topic/CFrameWnd::OnSetPreviewMode.md)。\)|  
|[CMDIFrameWndEx::OnShowCustomizePane](../Topic/CMDIFrameWndEx::OnShowCustomizePane.md)|调用由框架，快速自定义时激活窗格。|  
|[CMDIFrameWndEx::OnShowMDITabContextMenu](../Topic/CMDIFrameWndEx::OnShowMDITabContextMenu.md)|调用由结构，在某个选项应显示上下文菜单。  \(活动的 MDI 仅选项卡式组。\)|  
|[CMDIFrameWndEx::OnShowPanes](../Topic/CMDIFrameWndEx::OnShowPanes.md)|调用由结构显示或隐藏窗格。|  
|[CMDIFrameWndEx::OnShowPopupMenu](../Topic/CMDIFrameWndEx::OnShowPopupMenu.md)|调用由结构，当激活弹出菜单。|  
|[CMDIFrameWndEx::OnSizeMDIClient](../Topic/CMDIFrameWndEx::OnSizeMDIClient.md)|调用由结构，当客户端 MDI 窗口的大小更改。|  
|[CMDIFrameWndEx::OnTearOffMenu](../Topic/CMDIFrameWndEx::OnTearOffMenu.md)|调用由结构，当有一个撕掉条活动的菜单。|  
|[CMDIFrameWndEx::OnUpdateFrameMenu](../Topic/CMDIFrameWndEx::OnUpdateFrameMenu.md)|调用由框架更新框架菜单。  \(重写 `CMDIFrameWnd::OnUpdateFrameMenu`。\)|  
|[CMDIFrameWndEx::PaneFromPoint](../Topic/CMDIFrameWndEx::PaneFromPoint.md)|返回包含指定的点停靠窗格。|  
|`CMDIFrameWndEx::PreTranslateMessage`|用于使选件类 [CWinApp](../../mfc/reference/cwinapp-class.md) 转换窗口消息，并在调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) windows 函数之前。  \(重写 `CMDIFrameWnd::PreTranslateMessage`。\)|  
|[CMDIFrameWndEx::RecalcLayout](../Topic/CMDIFrameWndEx::RecalcLayout.md)|调用由框架重新计算框架窗口的格式。  \(重写 [CFrameWnd::RecalcLayout](../Topic/CFrameWnd::RecalcLayout.md)。\)|  
|[CMDIFrameWndEx::RemovePaneFromDockManager](../Topic/CMDIFrameWndEx::RemovePaneFromDockManager.md)|注销窗格和距停靠管理器中移除。|  
|[CMDIFrameWndEx::SaveMDIState](../Topic/CMDIFrameWndEx::SaveMDIState.md)|保存 MDI 选项卡式组当前格式，并列出以前打开文档。|  
|[CMDIFrameWndEx::SetPrintPreviewFrame](../Topic/CMDIFrameWndEx::SetPrintPreviewFrame.md)|设置打印预览框架窗口。|  
|[CMDIFrameWndEx::SetupToolbarMenu](../Topic/CMDIFrameWndEx::SetupToolbarMenu.md)|通过搜索虚假的项目和替换这些修改工具栏对象使用指定的用户定义的项。|  
|[CMDIFrameWndEx::ShowFullScreen](../Topic/CMDIFrameWndEx::ShowFullScreen.md)|开关与常规模式的主框架到"全屏"模式。|  
|[CMDIFrameWndEx::ShowPane](../Topic/CMDIFrameWndEx::ShowPane.md)|显示或隐藏指定的窗格。|  
|[CMDIFrameWndEx::ShowWindowsDialog](../Topic/CMDIFrameWndEx::ShowWindowsDialog.md)|创建一个 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) 框中将其打开。|  
|[CMDIFrameWndEx::TabbedDocumentToControlBar](../Topic/CMDIFrameWndEx::TabbedDocumentToControlBar.md)|将指定的选项卡式文档到停靠窗格中。|  
|[CMDIFrameWndEx::UpdateCaption](../Topic/CMDIFrameWndEx::UpdateCaption.md)|调用由框架更新窗架说明。|  
|[CMDIFrameWndEx::UpdateMDITabbedBarsIcons](../Topic/CMDIFrameWndEx::UpdateMDITabbedBarsIcons.md)|将每个 MDI 选项卡式窗格的图标。|  
|[CMDIFrameWndEx::WinHelp](../Topic/CMDIFrameWndEx::WinHelp.md)|调用由框架启动 WinHelp 应用程序或上下文帮助。  \(重写 [CWnd::WinHelp](../Topic/CWnd::WinHelp.md)。\)|  
  
### 数据成员  
  
|名称|描述|  
|--------|--------|  
|[CMDIFrameWndEx::m\_bCanCovertControlBarToMDIChild](../Topic/CMDIFrameWndEx::m_bCanCovertControlBarToMDIChild.md)|确定停靠窗格是否可以转换到 MDI 子窗口。|  
|[CMDIFrameWndEx::m\_bDisableSetRedraw](../Topic/CMDIFrameWndEx::m_bDisableSetRedraw.md)|启用或禁用重绘 MDI 子窗口的优化。|  
  
## 备注  
 若要利用在 MDI 应用程序的扩展的自定义功能，从 `CMDIFrameWndEx` 派生应用程序的 MDI 框架窗口选件类而不是 `CMDIFrameWnd`。  
  
## 示例  
 下面的示例从 `CMDIFrameWndEx`派生选件类。  此代码段来自 [DrawClient 示例：基于 MFC 功能区的 OLE 对象绘图应用程序](../../top/visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient#1](../../mfc/reference/codesnippet/CPP/cmdiframewndex-class_1.h)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)  
  
 [CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)  
  
## 要求  
 **标头：** afxMDIFrameWndEx.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWnd](../../mfc/reference/cframewnd-class.md)   
 [CMDIChildWndEx 类](../../mfc/reference/cmdichildwndex-class.md)