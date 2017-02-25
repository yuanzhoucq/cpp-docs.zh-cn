---
title: "CPaneDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPaneDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneDialog class"
  - "CPaneDialog constructor"
  - "CPaneDialog::CreateObject method"
  - "CPaneDialog::OnEraseBkgnd method"
  - "CPaneDialog::OnLButtonDblClk method"
  - "CPaneDialog::OnLButtonDown method"
  - "CPaneDialog::OnUpdateCmdUI method"
  - "CPaneDialog::OnWindowPosChanging method"
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CPaneDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CPaneDialog` 选件类支持无模式，停靠对话框。  
  
## 语法  
  
```  
class CPaneDialog : public CDockablePane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CPaneDialog::CPaneDialog`|默认构造函数。|  
|`CPaneDialog::~CPaneDialog`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPaneDialog::Create](../Topic/CPaneDialog::Create.md)|创建可停靠对话框并将它附加到 `CPaneDialog` 对象。|  
|`CPaneDialog::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|`CPaneDialog::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CPaneDialog::HandleInitDialog](../Topic/CPaneDialog::HandleInitDialog.md)|处理 [WM\_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) 消息。  （重新定义 `CBasePane::HandleInitDialog`。）|  
|`CPaneDialog::OnEraseBkgnd`|处理 [WM\_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) 消息。  （重新定义 [CWnd::OnEraseBkgnd](../Topic/CWnd::OnEraseBkgnd.md)。）|  
|`CPaneDialog::OnLButtonDblClk`|处理 [WM\_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) 消息。  （重新定义 [CWnd::OnLButtonDblClk](../Topic/CWnd::OnLButtonDblClk.md)。）|  
|`CPaneDialog::OnLButtonDown`|处理 [WM\_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607) 消息。  （重新定义 [CWnd::OnLButtonDown](../Topic/CWnd::OnLButtonDown.md)。）|  
|`CPaneDialog::OnUpdateCmdUI`|调用由框架更新该对话框的窗口。  （重写 [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/zh-cn/5dd61606-1c12-40d4-b024-f3839aa5e2e0)。）|  
|`CPaneDialog::OnWindowPosChanging`|处理 [WM\_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653) 消息。  （重新定义 [CWnd::OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)。）|  
|[CPaneDialog::SetOccDialogInfo](../Topic/CPaneDialog::SetOccDialogInfo.md)|为OLE控件容器的对话框指定模板。|  
  
## 备注  
 构造在两个步骤的一 `CPaneDialog` 对象。  首先，构造在您的代码的对象。  接下来，调用 [CPaneDialog::Create](../Topic/CPaneDialog::Create.md)。  必须指定有效的资源模板名称或模板ID和通过指针到父窗口。  否则，创建过程将失败。  对话框必须指定WS\_CHILD和WS\_VISIBLE样式。  建议您还可以指定WS\_CLIPCHILDREN和WS\_CLIPSIBLINGS样式。  有关更多信息，请参见 [窗口样式](../../mfc/reference/window-styles.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CPaneDialog](../../mfc/reference/cpanedialog-class.md)  
  
## 要求  
 **标头:** afxpanedialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [窗口样式](../../mfc/reference/window-styles.md)