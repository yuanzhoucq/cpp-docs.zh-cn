---
title: "CMFCReBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCReBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCReBar class"
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CMFCReBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCReBar` 对象是对于rebar控件提供布局、持久性和状态信息的控制条。  
  
## 语法  
  
```  
class CMFCReBar : public CPane  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCReBar::AddBar](../Topic/CMFCReBar::AddBar.md)|添加一个带区到rebar。|  
|[CMFCReBar::CalcFixedLayout](../Topic/CMFCReBar::CalcFixedLayout.md)|（重写 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)。）|  
|[CMFCReBar::CanFloat](../Topic/CMFCReBar::CanFloat.md)|（重写 [CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md)。）|  
|[CMFCReBar::Create](../Topic/CMFCReBar::Create.md)|创建rebar控件并将它附加到 `CMFCReBar` 对象。|  
|[CMFCReBar::EnableDocking](../Topic/CMFCReBar::EnableDocking.md)|（重写 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)。）|  
|[CMFCReBar::GetReBarBandInfoSize](../Topic/CMFCReBar::GetReBarBandInfoSize.md)||  
|[CMFCReBar::GetReBarCtrl](../Topic/CMFCReBar::GetReBarCtrl.md)|提供直接访问基础 [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) 公共控件。|  
|[CMFCReBar::OnShowControlBarMenu](../Topic/CMFCReBar::OnShowControlBarMenu.md)|（重写 [CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)。）|  
|[CMFCReBar::OnToolHitTest](../Topic/CMFCReBar::OnToolHitTest.md)|（重写 [CWnd::OnToolHitTest](../Topic/CWnd::OnToolHitTest.md)。）|  
|[CMFCReBar::OnUpdateCmdUI](../Topic/CMFCReBar::OnUpdateCmdUI.md)|（重写 [CBasePane::OnUpdateCmdUI](http://msdn.microsoft.com/zh-cn/e139f06a-9793-4ee2-bc3d-517389368c77)。）|  
|[CMFCReBar::SetPaneAlignment](../Topic/CMFCReBar::SetPaneAlignment.md)|（重写 [CBasePane::SetPaneAlignment](../Topic/CBasePane::SetPaneAlignment.md)。）|  
  
## 备注  
 `CMFCReBar` 对象可以包含各种子窗口。  这包括编辑框，工具栏，而列表框。  可以调整rebar程序模型，或者用户可以通过拖动其手柄条手动调整rebar。  还可以设置一rebar对象的背景为您的选择位图的。  
  
 rebar对象的行为类似于工具栏对象。  rebar控件可以包含一个或多个带区，因此，每个带区可以包含手柄栏、位图、文本标签和子窗口。  
  
## 示例  
 下面的示例在 `CMFCReBar` 选件类演示如何使用各种方法。  此示例演示如何创建rebar控件并添加带区到它。  带区用作内部工具栏。  此代码段是 [Rebar测试示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/CPP/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/CPP/cmfcrebar-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)  
  
## 要求  
 **标头:** afxRebar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CReBarCtrl Class](../../mfc/reference/crebarctrl-class.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)