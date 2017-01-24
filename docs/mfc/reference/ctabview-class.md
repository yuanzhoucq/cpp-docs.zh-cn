---
title: "CTabView Class | Microsoft Docs"
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
  - "CTabView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabView class"
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
caps.latest.revision: 32
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTabView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CTabView` 选件类简化使用选项卡控件选件类\([CMFCTabCtrl](../../mfc/reference/ctabview-class.md)\)在使用MFC文档\/视图结构的应用程序。  
  
## 语法  
  
```  
class CTabbedView : public CView  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTabView::AddView](../Topic/CTabView::AddView.md)|添加新视图到选项卡控件。|  
|[CTabView::FindTab](../Topic/CTabView::FindTab.md)|返回指定视图的索引在选项卡控件的。|  
|[CTabView::GetActiveView](../Topic/CTabView::GetActiveView.md)|返回指向的指针为当前活动的视图|  
|[CTabView::GetTabControl](../Topic/CTabView::GetTabControl.md)|返回对选项卡控件与视图。|  
|[CTabView::RemoveView](../Topic/CTabView::RemoveView.md)|从的选项卡控件中移除视图。|  
|[CTabView::SetActiveView](../Topic/CTabView::SetActiveView.md)|使视图激活。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CTabView::IsScrollBar](../Topic/CTabView::IsScrollBar.md)|调用由结构，当创建选项视图认为可选视图是否具有共享水平滚动条。|  
|[CTabView::OnActivateView](../Topic/CTabView::OnActivateView.md)|调用由结构，当选项使用视图活动或非活动。|  
  
## 备注  
 此选件类可以轻松地将一个选项卡式视图到文档\/视图应用程序。  `CTabView` 是 `CView`\-包含嵌入 `CMFCTabCtrl` 对象的派生类。  `CTabView` 处理所需的所有消息支持 `CMFCTabCtrl` 对象。  从 `CTabView` 派生选件类并粘贴到您的应用程序，然后添加 `CView`\-使用 `AddView` 方法的派生类。  选项卡控件将显示这些视图作为选项。  
  
 例如，您可能有一个可以用不同方式表示的文档:作为电子表格，图表，一个可编辑窗体，依此类推。  可以创建绘制各个数据视图根据需要，插入到您的 `CTabView`中派生的对象并将这些选项卡式，而无需任何其他代码。  
  
 [TabbedView示例:MFC选项卡式视图应用程序](../../top/visual-cpp-samples.md) 声明 `CTabView`用法。  
  
## 示例  
 下面的示例演示 `CTabView` 如何在TabbedView示例。  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/CPP/ctabview-class_1.h)]  
  
## 要求  
 **标头:** afxTabView.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CTabView Class](../../mfc/reference/ctabview-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)