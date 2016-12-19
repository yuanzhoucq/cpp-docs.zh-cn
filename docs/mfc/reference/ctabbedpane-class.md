---
title: "CTabbedPane Class | Microsoft Docs"
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
  - "CTabbedPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabbedPane class"
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTabbedPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

利用可拆分的选项卡实现窗格的功能。  
  
## 语法  
  
```  
class CTabbedPane : public CBaseTabbedPane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|`CTabbedPane::CTabbedPane`|默认构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTabbedPane::DetachPane](../Topic/CTabbedPane::DetachPane.md)|（重写 [CBaseTabbedPane::DetachPane](../Topic/CBaseTabbedPane::DetachPane.md)。）|  
|[CTabbedPane::EnableTabAutoColor](../Topic/CTabbedPane::EnableTabAutoColor.md)|启用或禁用自动选项卡着色。|  
|[CTabbedPane::FloatTab](../Topic/CTabbedPane::FloatTab.md)|仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。  （重写 [CBaseTabbedPane::FloatTab](../Topic/CBaseTabbedPane::FloatTab.md)。）|  
|[CTabbedPane::GetTabArea](../Topic/CTabbedPane::GetTabArea.md)|返回选项卡区域在选项卡式窗口中的大小和位置。|  
|[CTabbedPane::GetTabWnd](../Topic/CTabbedPane::GetTabWnd.md)||  
|[CTabbedPane::HasAutoHideMode](../Topic/CTabbedPane::HasAutoHideMode.md)|确定选项卡式窗格是否可以切换为自动隐藏模式。  （重写 [CBaseTabbedPane::HasAutoHideMode](../Topic/CBaseTabbedPane::HasAutoHideMode.md)。）|  
|[CTabbedPane::IsTabLocationBottom](../Topic/CTabbedPane::IsTabLocationBottom.md)|确定选项卡是否位于窗口的底部。|  
|[CTabbedPane::ResetTabs](../Topic/CTabbedPane::ResetTabs.md)|将所有选项卡式窗格重置为默认状态。|  
|[CTabbedPane::SetTabAutoColors](../Topic/CTabbedPane::SetTabAutoColors.md)|设置可以在自动颜色功能启用时可用的自定义颜色列表。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CTabbedPane::m\_bTabsAlwaysTop](../Topic/CTabbedPane::m_bTabsAlwaysTop.md)|选项卡在应用程序中的的默认位置。|  
|[CTabbedPane::m\_pTabWndRTC](../Topic/CTabbedPane::m_pTabWndRTC.md)|自定义 `CMFCTabCtrl`\-派生对象的运行时类信息。|  
  
## 备注  
 当用户通过将一个窗格指向第二个窗格的标题的方式来附加到另一个窗格，框架自动创建此类的实例。  由框架创建的所有选项卡式窗格都具有值为 \-1 的 ID。  
  
 若要指定常规选项卡而不是 Outlook 样式的选项卡，请将 `AFX_CBRS_REGULAR_TABS` 样式传递到 [CDockablePane::CreateEx](../Topic/CDockablePane::CreateEx.md) 方法。  
  
 如果你使用可拆离的选项卡创建一个选项卡式窗格，该窗格可能会被框架自动销毁，因此，你不应该存储该指针。  若要获取对选项卡式窗格的指针，请调用 `CBasePane::GetParentTabbedPane` 方法。  
  
## 示例  
 我们在此示例中创建了一个 `CTabbedPane` 对象。  接着，我们使用 [CBaseTabbedPane::AddTab](../Topic/CBaseTabbedPane::AddTab.md) 来附加其他选项卡。  
  
```  
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);  
if (!pTabbededBar->Create (_T(""), this, CRect (0, 0, 200, 200),  
                           TRUE,   
                           (UINT) -1,  
                           WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |  
                           WS_CLIPCHILDREN | CBRS_LEFT |    
                           CBRS_FLOAT_MULTI))  
{  
    TRACE0("Failed to create Solution Explorer bar\n");  
    return FALSE;      // fail to create  
}  
  
pTabbededBar->AddTab (&m_wndClassView);  
pTabbededBar->AddTab (&m_wndResourceView);  
pTabbededBar->AddTab (&m_wndFileView);  
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);  
DockPane(pTabbededBar);  
```  
  
## 示例  
 另一种创建选项卡式控制条对象的方法是使用 [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md)。  `AttachToTabWnd` 方法使用由 [CDockablePane::SetTabbedPaneRTC](../Topic/CDockablePane::SetTabbedPaneRTC.md) 设置的运行时类信息动态创建一个选项卡式窗格对象。  
  
 在此示例中，我们动态地创建了一个选项卡式窗格，附加这两个选项卡，并使第二个选项不可拆离。  
  
```  
DockPane(&m_wndClassView);  
CTabbedPane* pTabbedBar = NULL;  
m_wndResourceView.AttachToTabWnd (&m_wndClassView, DM_SHOW, TRUE,  
                                  (CDockablePane**) &pTabbedBar);  
m_wndFileView.AttachToTabWnd (pTabbedBar, DM_SHOW, TRUE,  
                              (CDockablePane**) &pTabbedBar);  
pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1, FALSE);  
```  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)  
  
## 要求  
 **标头：**afxTabbedPane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)