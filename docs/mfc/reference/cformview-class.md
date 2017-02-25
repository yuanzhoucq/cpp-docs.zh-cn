---
title: "CFormView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFormView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFormView class"
  - "form views"
  - "视图, containing controls"
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CFormView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于窗体视图的基类。  
  
## 语法  
  
```  
class CFormView : public CScrollView  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFormView::CFormView](../Topic/CFormView::CFormView.md)|构造 `CFormView` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFormView::IsInitDlgCompleted](../Topic/CFormView::IsInitDlgCompleted.md)|用于在初始化期间同步。|  
  
## 备注  
 窗体视图是实质上是一个包含控件的视图。  这些控件基于对话框模板资源进行布局。  如果你想要你的应用程序具有窗体，请使用 `CFormView`。  根据需要，使用 [CScrollView](../../mfc/reference/cscrollview-class.md) 功能，这些视图支持滚动。  
  
 当你[创建基于窗体的应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)时，可以将其视图类作为 `CFormView` 的基础，使其成为基于窗体的应用程序。  
  
 还可以将新的[窗体主题](../../mfc/form-views-mfc.md)插入基于文档视图的应用程序。  即使你的应用程序最初不支持窗体，当你插入一个新窗体时 Visual C\+\+ 将添加这一支持。  
  
 MFC 应用程序向导和“添加类”命令是创建基于窗体的应用程序的首选的方法。  如果你需要创建一个基于窗体应用程序，而不使用这些方法，请参阅[创建基于窗体的应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 `CFormView`  
  
## 要求  
 **标头：**afxext.h  
  
## 请参阅  
 [MFC 示例 SNAPVW](../../top/visual-cpp-samples.md)   
 [MFC 示例 VIEWEX](../../top/visual-cpp-samples.md)   
 [CScrollView Class](../../mfc/reference/cscrollview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [CScrollView Class](../../mfc/reference/cscrollview-class.md)   
 [CView::OnUpdate](../Topic/CView::OnUpdate.md)   
 [CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)   
 [CView::OnPrint](../Topic/CView::OnPrint.md)   
 [CWnd::UpdateData](../Topic/CWnd::UpdateData.md)   
 [CScrollView::ResizeParentToFit](../Topic/CScrollView::ResizeParentToFit.md)