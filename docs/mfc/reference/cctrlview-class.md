---
title: "CCtrlView Class | Microsoft Docs"
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
  - "CCtrlView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCtrlView class"
  - "控件 [MFC], common"
  - "视图, and common controls"
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCtrlView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调整文档视图结构Windows 98和Windows NT支持的公共控件版本3.51和更高版本。  
  
## 语法  
  
```  
class CCtrlView : public CView  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CCtrlView::CCtrlView](../Topic/CCtrlView::CCtrlView.md)|构造 `CCtrlView` 对象。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CCtrlView::OnDraw](../Topic/CCtrlView::OnDraw.md)|使用指定的设备上下文，调用由框架绘制。|  
|[CCtrlView::PreCreateWindow](../Topic/CCtrlView::PreCreateWindow.md)|调用在Windows窗口中先前创建附加到此 `CCtrlView` 对象。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CCtrlView::m\_dwDefaultStyle](../Topic/CCtrlView::m_dwDefaultStyle.md)|包含视图选件类的默认样式。|  
|[CCtrlView::m\_strClass](../Topic/CCtrlView::m_strClass.md)|包含Windows类名视图选件类。|  
  
## 备注  
 选件类 `CCtrlView` 及其派生对象，[CEditView](../../mfc/reference/ceditview-class.md)、 [CListView](../../mfc/reference/clistview-class.md)、 [CTreeView](../../mfc/reference/ctreeview-class.md)和 [CRichEditView](../../mfc/reference/cricheditview-class.md)，以适应文档视图结构\/98 \(Windows 95和Windows NT支持的新公共控件版本3.51和更高版本。  有关文档视图结构的更多信息，请参见 [文档\/视图结构](../../mfc/document-view-architecture.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CView Class](../../mfc/reference/cview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CTreeView Class](../../mfc/reference/ctreeview-class.md)   
 [CListView Class](../../mfc/reference/clistview-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)