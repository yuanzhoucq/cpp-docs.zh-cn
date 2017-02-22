---
title: "COleIPFrameWndEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleIPFrameWndEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleIPFrameWndEx class"
ms.assetid: ebff1560-a1eb-4854-af00-95d4a192bd55
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 36
---
# COleIPFrameWndEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`COleIPFrameWndEx` 类实现支持 MFC 的 OLE 容器。 必须从 `COleIPFrameWndEx` 类派生应用程序的就地框架窗口类，而不是从 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) 类派生。  
  
## 语法  
  
```  
class COleIPFrameWndEx : public COleIPFrameWnd  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleIPFrameWndEx::AddDockSite](../Topic/COleIPFrameWndEx::AddDockSite.md)||  
|[COleIPFrameWndEx::AddPane](../Topic/COleIPFrameWndEx::AddPane.md)||  
|[COleIPFrameWndEx::AdjustDockingLayout](../Topic/COleIPFrameWndEx::AdjustDockingLayout.md)||  
|[COleIPFrameWndEx::DockPane](../Topic/COleIPFrameWndEx::DockPane.md)||  
|[COleIPFrameWndEx::DockPaneLeftOf](../Topic/COleIPFrameWndEx::DockPaneLeftOf.md)|将一个窗格停靠到另一个窗格的左侧。|  
|[COleIPFrameWndEx::EnableAutoHidePanes](../Topic/COleIPFrameWndEx::EnableAutoHidePanes.md)||  
|[COleIPFrameWndEx::EnableDocking](../Topic/COleIPFrameWndEx::EnableDocking.md)||  
|[COleIPFrameWndEx::EnablePaneMenu](../Topic/COleIPFrameWndEx::EnablePaneMenu.md)||  
|[COleIPFrameWndEx::GetActivePopup](../Topic/COleIPFrameWndEx::GetActivePopup.md)|返回一个指向当前显示的弹出菜单的指针。|  
|[COleIPFrameWndEx::GetContainerFrameWindow](../Topic/COleIPFrameWndEx::GetContainerFrameWindow.md)||  
|[COleIPFrameWndEx::GetDefaultResId](../Topic/COleIPFrameWndEx::GetDefaultResId.md)|返回加载窗口时你指定的框架窗口的资源 ID。|  
|[COleIPFrameWndEx::GetDockFrame](../Topic/COleIPFrameWndEx::GetDockFrame.md)||  
|[COleIPFrameWndEx::GetDockingManager](../Topic/COleIPFrameWndEx::GetDockingManager.md)||  
|[COleIPFrameWndEx::GetMainFrame](../Topic/COleIPFrameWndEx::GetMainFrame.md)||  
|[COleIPFrameWndEx::GetMenuBar](../Topic/COleIPFrameWndEx::GetMenuBar.md)|返回一个指向附加到框架窗口的菜单栏对象的指针。|  
|[COleIPFrameWndEx::GetPane](../Topic/COleIPFrameWndEx::GetPane.md)||  
|[COleIPFrameWndEx::GetTearOffBars](../Topic/COleIPFrameWndEx::GetTearOffBars.md)|返回处于拖曳状态的窗格对象的列表。|  
|[COleIPFrameWndEx::GetToolbarButtonToolTipText](../Topic/COleIPFrameWndEx::GetToolbarButtonToolTipText.md)|在显示按钮的工具提示之前由框架调用。|  
|[COleIPFrameWndEx::InsertPane](../Topic/COleIPFrameWndEx::InsertPane.md)||  
|[COleIPFrameWndEx::IsMenuBarAvailable](../Topic/COleIPFrameWndEx::IsMenuBarAvailable.md)|确定指向菜单栏对象的指针是否不是 `NULL`。|  
|[COleIPFrameWndEx::IsPointNearDockSite](../Topic/COleIPFrameWndEx::IsPointNearDockSite.md)||  
|[COleIPFrameWndEx::LoadFrame](../Topic/COleIPFrameWndEx::LoadFrame.md)|（重写 `COleIPFrameWnd::LoadFrame`。）|  
|[COleIPFrameWndEx::OnCloseDockingPane](../Topic/COleIPFrameWndEx::OnCloseDockingPane.md)||  
|[COleIPFrameWndEx::OnCloseMiniFrame](../Topic/COleIPFrameWndEx::OnCloseMiniFrame.md)||  
|[COleIPFrameWndEx::OnClosePopupMenu](../Topic/COleIPFrameWndEx::OnClosePopupMenu.md)|当活动的弹出菜单处理 WM\_DESTROY 消息时由框架调用。|  
|[COleIPFrameWndEx::OnCmdMsg](../Topic/COleIPFrameWndEx::OnCmdMsg.md)|（重写 `CFrameWnd::OnCmdMsg`。）|  
|[COleIPFrameWndEx::OnDrawMenuImage](../Topic/COleIPFrameWndEx::OnDrawMenuImage.md)|当绘制与菜单项关联的图像时由框架调用。|  
|[COleIPFrameWndEx::OnDrawMenuLogo](../Topic/COleIPFrameWndEx::OnDrawMenuLogo.md)|当 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) 对象处理 WM\_PAINT 消息时由框架调用。|  
|[COleIPFrameWndEx::OnMenuButtonToolHitTest](../Topic/COleIPFrameWndEx::OnMenuButtonToolHitTest.md)|当 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) 对象处理 WM\_NCHITTEST 消息时由框架调用。|  
|[COleIPFrameWndEx::OnMoveMiniFrame](../Topic/COleIPFrameWndEx::OnMoveMiniFrame.md)||  
|[COleIPFrameWndEx::OnSetPreviewMode](../Topic/COleIPFrameWndEx::OnSetPreviewMode.md)|调用该成员函数以设置应用程序主框架窗口打印预览模式的流入和流出。 （重写 [CFrameWnd::OnSetPreviewMode](../Topic/CFrameWnd::OnSetPreviewMode.md)。）|  
|[COleIPFrameWndEx::OnShowCustomizePane](../Topic/COleIPFrameWndEx::OnShowCustomizePane.md)||  
|[COleIPFrameWndEx::OnShowPanes](../Topic/COleIPFrameWndEx::OnShowPanes.md)||  
|[COleIPFrameWndEx::OnShowPopupMenu](../Topic/COleIPFrameWndEx::OnShowPopupMenu.md)|当激活弹出菜单时由框架调用。|  
|[COleIPFrameWndEx::OnTearOffMenu](../Topic/COleIPFrameWndEx::OnTearOffMenu.md)|当激活带有拖曳栏的菜单时由框架调用。|  
|[COleIPFrameWndEx::PaneFromPoint](../Topic/COleIPFrameWndEx::PaneFromPoint.md)||  
|[COleIPFrameWndEx::PreTranslateMessage](../Topic/COleIPFrameWndEx::PreTranslateMessage.md)|（重写 `COleIPFrameWnd::PreTranslateMessage`。）|  
|[COleIPFrameWndEx::RecalcLayout](../Topic/COleIPFrameWndEx::RecalcLayout.md)|（重写 `COleIPFrameWnd::RecalcLayout`。）|  
|[COleIPFrameWndEx::RemovePaneFromDockManager](../Topic/COleIPFrameWndEx::RemovePaneFromDockManager.md)||  
|[COleIPFrameWndEx::SetDockState](../Topic/COleIPFrameWndEx::SetDockState.md)|将指定的停靠状态应用于属于框架窗口的窗格。|  
|[COleIPFrameWndEx::SetupToolbarMenu](../Topic/COleIPFrameWndEx::SetupToolbarMenu.md)|通过搜索虚拟项并将其替换为指定的用户定义项修改工具栏对象。|  
|[COleIPFrameWndEx::ShowPane](../Topic/COleIPFrameWndEx::ShowPane.md)||  
|[COleIPFrameWndEx::WinHelp](../Topic/COleIPFrameWndEx::WinHelp.md)|由框架调用以启动 WinHelp 应用程序或上下文帮助。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[COleIPFrameWndEx::InitUserToobars](../Topic/COleIPFrameWndEx::InitUserToobars.md)|告知框架初始化一系列分配给用户定义的工具栏的控件 ID。|  
  
## 示例  
 下面的示例演示如何将 `COleIPFrameWndEx` 类的实例作为子类并重写其方法。 该示例演示如何重写 `OnDestory` 方法、`RepositionFrame` 方法、`RecalcLayout` 方法和 `CalcWindowRect` 方法。 此代码片段属于 [Word Pad 示例](../../top/visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad#1](../../mfc/reference/codesnippet/CPP/coleipframewndex-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)  
  
 [COleIPFrameWndEx](../../mfc/reference/coleipframewndex-class.md)  
  
## 要求  
 **标头：**afxoleipframewndex.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)   
 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)