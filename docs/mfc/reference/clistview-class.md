---
title: "CListView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CListView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListView class"
  - "视图, and common controls"
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CListView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

简化对列表控件中使用和对 [CListCtrl](../../mfc/reference/clistctrl-class.md)，封装列表控件的功能选件类，在MFC文档的视图结构。  
  
## 语法  
  
```  
class CListView : public CCtrlView  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CListView::CListView](../Topic/CListView::CListView.md)|构造 `CListView` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CListView::GetListCtrl](../Topic/CListView::GetListCtrl.md)|返回列表控件与视图。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CListView::RemoveImageList](../Topic/CListView::RemoveImageList.md)|中移除指定的图像从列表视图中列出。|  
  
## 备注  
 有关此结构的更多信息，请对引用的 [CView](../../mfc/reference/cview-class.md) 选件类和交叉引用请参见概述存在。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CListView`  
  
## 要求  
 **Header:** afxcview.h  
  
## 请参阅  
 [MFC示例ROWLIST](../../top/visual-cpp-samples.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)