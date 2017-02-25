---
title: "CMDIChildWndEx 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMDIChildWndEx"
  - "GetThisClass"
  - "CMDIChildWndEx::PreTranslateMessage"
  - "CMDIChildWndEx::ActivateFrame"
  - "CMDIChildWndEx.GetThisClass"
  - "CMDIChildWndEx::AddDockSite"
  - "CMDIChildWndEx.CreateObject"
  - "CMDIChildWndEx::CreateObject"
  - "CMDIChildWndEx.ActivateFrame"
  - "CMDIChildWndEx::GetThisClass"
  - "CMDIChildWndEx.PreTranslateMessage"
  - "PreTranslateMessage"
  - "ActivateFrame"
  - "CreateObject"
  - "CMDIChildWndEx.AddDockSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDIChildWndEx 类"
  - "ActivateFrame 方法"
  - "PreTranslateMessage 方法"
  - "GetThisClass 方法"
  - "CreateObject 方法"
ms.assetid: d39fec06-0bd6-4271-917d-35aae3b24d8e
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMDIChildWndEx 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMDIChildWndEx` 选件类提供功能多文档界面 \(MDI\) 子窗口的窗口。  它扩展 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)的功能。  当 MDI 应用程序使用一些 MFC 选件类时，框架需要此选件类。  
  
## 语法  
  
```  
class CMDIChildWndEx : public CMDIChildWnd  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMDIChildWndEx::ActivateTopLevelFrame](../Topic/CMDIChildWndEx::ActivateTopLevelFrame.md)|在内部调用由框架激活顶级帧，则应从任务栏选项激活应用程序。|  
|`CMDIChildWndEx::AddDockSite`|不使用此方法也不执行任何操作。|  
|[CMDIChildWndEx::AddPane](../Topic/CMDIChildWndEx::AddPane.md)|添加一个窗格。|  
|[CMDIChildWndEx::AddTabbedPane](../Topic/CMDIChildWndEx::AddTabbedPane.md)|添加一个选项卡式窗格。|  
|[CMDIChildWndEx::AdjustDockingLayout](../Topic/CMDIChildWndEx::AdjustDockingLayout.md)|调整停靠格式。|  
|[CMDIChildWndEx::CanShowOnMDITabs](../Topic/CMDIChildWndEx::CanShowOnMDITabs.md)||  
|[CMDIChildWndEx::CanShowOnTaskBarTabs](../Topic/CMDIChildWndEx::CanShowOnTaskBarTabs.md)|调用框架此 MDI 子窗体是否在窗口中显示 7 个任务栏选项。|  
|[CMDIChildWndEx::CanShowOnWindowsList](../Topic/CMDIChildWndEx::CanShowOnWindowsList.md)|如果 MDI 子窗口名称。[CMFCWindowsManagerDialog Class](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) 对话框，可以显示返回 `TRUE`。  否则，返回 `FALSE`。|  
|`CMDIChildWndEx::CreateObject`|调用由框架创建此选件类类型动态实例。|  
|[CMDIChildWndEx::DockPane](../Topic/CMDIChildWndEx::DockPane.md)|停靠一个窗格。|  
|[CMDIChildWndEx::DockPaneLeftOf](../Topic/CMDIChildWndEx::DockPaneLeftOf.md)|停靠在另一个窗格左侧的一个窗格。|  
|[CMDIChildWndEx::EnableAutoHidePanes](../Topic/CMDIChildWndEx::EnableAutoHidePanes.md)|当停靠窗口中，的指定端启动窗格"自动隐藏"模式。|  
|[CMDIChildWndEx::EnableDocking](../Topic/CMDIChildWndEx::EnableDocking.md)|启用子窗口的停靠到主框架。|  
|[CMDIChildWndEx::EnableTaskbarThumbnailClipRect](../Topic/CMDIChildWndEx::EnableTaskbarThumbnailClipRect.md)|启用或禁用窗口的客户端区域的一部分的自动选择的形式显示在任务栏的该窗口的缩略图。|  
|[CMDIChildWndEx::GetDockingManager](../Topic/CMDIChildWndEx::GetDockingManager.md)||  
|[CMDIChildWndEx::GetDocumentName](../Topic/CMDIChildWndEx::GetDocumentName.md)|返回在 MDI 子窗口中显示文档的名称。|  
|[CMDIChildWndEx::GetFrameIcon](../Topic/CMDIChildWndEx::GetFrameIcon.md)|调用由框架检索 MDI 子窗口图标。|  
|[CMDIChildWndEx::GetFrameText](../Topic/CMDIChildWndEx::GetFrameText.md)|调用由框架检索 MDI 子窗口的文本。|  
|[CMDIChildWndEx::GetPane](../Topic/CMDIChildWndEx::GetPane.md)|按指定的控件 ID. 查找一个窗格|  
|[CMDIChildWndEx::GetRelatedTabGroup](../Topic/CMDIChildWndEx::GetRelatedTabGroup.md)||  
|[CMDIChildWndEx::GetTabbedPane](../Topic/CMDIChildWndEx::GetTabbedPane.md)|返回指向转换为选项卡式文档的嵌入式停靠窗格中。|  
|[CMDIChildWndEx::GetTabProxyWnd](../Topic/CMDIChildWndEx::GetTabProxyWnd.md)|返回选项代理窗口实际上在 windows 中注册 7 个任务栏选项。|  
|[CMDIChildWndEx::GetTaskbarPreviewWnd](../Topic/CMDIChildWndEx::GetTaskbarPreviewWnd.md)|调用由框架，则需要获取对 windows 7 任务栏缩略图选项 \(通常视图或拆分窗口\) 上显示的子窗口。|  
|[CMDIChildWndEx::GetTaskbarThumbnailClipRect](../Topic/CMDIChildWndEx::GetTaskbarThumbnailClipRect.md)|调用由框架，则需要选择窗口的客户端区域的一部分的形式显示在任务栏的该窗口的缩略图。|  
|`CMDIChildWndEx::GetThisClass`|调用由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMDIChildWndEx::GetToolbarButtonToolTipText](../Topic/CMDIChildWndEx::GetToolbarButtonToolTipText.md)|调用由框架检索工具栏按钮的工具提示。|  
|[CMDIChildWndEx::InsertPane](../Topic/CMDIChildWndEx::InsertPane.md)|注册了停靠管理器中指定的窗格。|  
|[CMDIChildWndEx::InvalidateIconicBitmaps](../Topic/CMDIChildWndEx::InvalidateIconicBitmaps.md)|无效的 MDI 子级的图标样式的位图表示。|  
|[CMDIChildWndEx::IsPointNearDockSite](../Topic/CMDIChildWndEx::IsPointNearDockSite.md)|确定指定的点是否在停靠站点附近。|  
|[CMDIChildWndEx::IsReadOnly](../Topic/CMDIChildWndEx::IsReadOnly.md)|返回 `TRUE`，如果在子窗口中显示的文档是只读的。  否则，返回 `FALSE`。|  
|[CMDIChildWndEx::IsRegisteredWithTaskbarTabs](../Topic/CMDIChildWndEx::IsRegisteredWithTaskbarTabs.md)|MDI 子窗体，如果成功移动到窗口注册 7 个任务栏选项，则返回 TRUE。|  
|[CMDIChildWndEx::IsTabbedPane](../Topic/CMDIChildWndEx::IsTabbedPane.md)|如果 MDI 子窗口包含停靠窗格，返回 `TRUE`。  否则，返回 `FALSE`。|  
|[CMDIChildWndEx::IsTaskbarTabsSupportEnabled](../Topic/CMDIChildWndEx::IsTaskbarTabsSupportEnabled.md)|指示 MDI 子窗体是否可以显示在 windows 7 个任务栏选项。|  
|[CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled](../Topic/CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled.md)|告知窗口中将显示客户端区域的一部分的自动选择作为在任务栏的该窗口的缩略图是否启用或禁用。|  
|[CMDIChildWndEx::m\_dwDefaultTaskbarTabPropertyFlags](../Topic/CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags.md)|标志的组合，通过该机制。SetTaskbarTabProperties 方法，即，当选项 \(MDI 子窗口\) 在 windows 中注册 7 个任务栏选项。  默认值组合所 STPF\_USEAPPTHUMBNAILWHENACTIVE&#124;STPF\_USEAPPPEEKWHENACTIVE.|  
|[CMDIChildWndEx::OnGetIconicLivePreviewBitmap](../Topic/CMDIChildWndEx::OnGetIconicLivePreviewBitmap.md)|调用由框架，则需要获取 MDI 子窗体实时预览的位图。|  
|[CMDIChildWndEx::OnGetIconicThumbnail](../Topic/CMDIChildWndEx::OnGetIconicThumbnail.md)|调用由框架，则需要获取 MDI 子窗体图标样式的缩略图的位图。|  
|[CMDIChildWndEx::OnMoveMiniFrame](../Topic/CMDIChildWndEx::OnMoveMiniFrame.md)|调用由框架移动和框架窗口。|  
|[CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton](../Topic/CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton.md)|调用由结构，当用户在某个任务栏缩略图选项的"关闭"按钮。|  
|[CMDIChildWndEx::OnSetPreviewMode](../Topic/CMDIChildWndEx::OnSetPreviewMode.md)|调用由框架进入或退出打印预览模式。|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailActivate](../Topic/CMDIChildWndEx::OnTaskbarTabThumbnailActivate.md)|调用由结构，当任务栏缩略图选项应处理 WM\_ACTIVATE 消息。|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate](../Topic/CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate.md)|调用由结构，当任务栏缩略图选项应处理 WM\_MOUSEACTIVATE 消息。|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailStretch](../Topic/CMDIChildWndEx::OnTaskbarTabThumbnailStretch.md)|调用由框架，则需要拉伸 windows 7 任务栏选项 MDI 子窗体缩略图预览的位图。|  
|[CMDIChildWndEx::OnUpdateFrameTitle](../Topic/CMDIChildWndEx::OnUpdateFrameTitle.md)|调用由框架更新框架标题。  \(重写 `CMDIChildWnd::OnUpdateFrameTitle`。\)|  
|[CMDIChildWndEx::PaneFromPoint](../Topic/CMDIChildWndEx::PaneFromPoint.md)|返回包含给定的点窗格。|  
|`CMDIChildWndEx::PreTranslateMessage`|用于使选件类 [CWinApp](../../mfc/reference/cwinapp-class.md) 转换窗口消息，并在调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) windows 函数之前。  \(重写 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。\)|  
|[CMDIChildWndEx::RecalcLayout](../Topic/CMDIChildWndEx::RecalcLayout.md)|计算 windows 窗体中。|  
|[CMDIChildWndEx::RegisterTaskbarTab](../Topic/CMDIChildWndEx::RegisterTaskbarTab.md)|注册了窗口的 MDI 子窗体 7 个任务栏选项。|  
|[CMDIChildWndEx::RemovePaneFromDockManager](../Topic/CMDIChildWndEx::RemovePaneFromDockManager.md)|从停靠管理器移除窗格。|  
|[CMDIChildWndEx::SetRelatedTabGroup](../Topic/CMDIChildWndEx::SetRelatedTabGroup.md)||  
|[CMDIChildWndEx::SetTaskbarTabActive](../Topic/CMDIChildWndEx::SetTaskbarTabActive.md)|activates 对应的 windows 7 任务栏选项。|  
|[CMDIChildWndEx::SetTaskbarTabOrder](../Topic/CMDIChildWndEx::SetTaskbarTabOrder.md)|插入指定的窗口之前的 MDI 子窗体在 windows 7 个任务栏选项。|  
|[CMDIChildWndEx::SetTaskbarTabProperties](../Topic/CMDIChildWndEx::SetTaskbarTabProperties.md)|设置 windows 7 任务栏选项的属性。|  
|[CMDIChildWndEx::SetTaskbarThumbnailClipRect](../Topic/CMDIChildWndEx::SetTaskbarThumbnailClipRect.md)|在内部调用由框架设置剪辑矩形选择窗口的客户端区域的一部分的形式显示在任务栏的该窗口的缩略图。|  
|[CMDIChildWndEx::ShowPane](../Topic/CMDIChildWndEx::ShowPane.md)||  
|[CMDIChildWndEx::UnregisterTaskbarTab](../Topic/CMDIChildWndEx::UnregisterTaskbarTab.md)|从窗口中移除 MDI 子窗体 7 个任务栏选项。|  
|[CMDIChildWndEx::UpdateTaskbarTabIcon](../Topic/CMDIChildWndEx::UpdateTaskbarTabIcon.md)|更新 windows 7 任务栏选项"图标。|  
  
## 备注  
 要在 MDI 应用程序的扩展的停靠功能，从 `CMDIChildWndEx` 派生您的应用程序 MDI 子窗口选件类而不是 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)。  
  
## 示例  
 下面的示例从 `CMDIChildWndEx`派生选件类。  此代码段来自 [VisualStudioDemo 示例：MFC Visual Studio 应用程序](../../top/visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#3](../../mfc/codesnippet/CPP/cmdichildwndex-class_1.h)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)  
  
 [CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)  
  
## 要求  
 **标头：** afxMDIChildWndEx.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)   
 [CMFCWindowsManagerDialog Class](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)   
 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)