---
title: "CTreeView Class | Microsoft Docs"
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
  - "CTreeView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeView class"
  - "CTreeView class, 公共控件"
  - "directory lists"
  - "file lists [C++]"
  - "tree view controls"
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTreeView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

简化对树控件中使用和对 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)，封装树控件功能的选件类，在MFC文档的视图结构。  
  
## 语法  
  
```  
class CTreeView : public CCtrlView  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CTreeView::CTreeView](../Topic/CTreeView::CTreeView.md)|构造 `CTreeView` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTreeView::GetTreeCtrl](../Topic/CTreeView::GetTreeCtrl.md)|返回树控件与视图。|  
  
## 备注  
 有关此结构的更多信息，请对引用的 [CView](../../mfc/reference/cview-class.md) 选件类和交叉引用请参见概述存在。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CTreeView`  
  
## 要求  
 **Header:** afxcview.h  
  
## 请参阅  
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)