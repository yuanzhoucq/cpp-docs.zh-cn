---
title: "COleResizeBar Class | Microsoft Docs"
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
  - "COleResizeBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleResizeBar class"
  - "control bars, 调整大小"
  - "in-place items"
  - "in-place items, 调整大小"
  - "OLE items, 调整大小"
  - "resizing in-place OLE items"
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleResizeBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

的控件条的类型支持调整就地OLE项。  
  
## 语法  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleResizeBar::COleResizeBar](../Topic/COleResizeBar::COleResizeBar.md)|构造 `COleResizeBar` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleResizeBar::Create](../Topic/COleResizeBar::Create.md)|创建和初始化一Windows子窗口并将它设置为 `COleResizeBar` 对象。|  
  
## 备注  
 在使用一个阴影框的 [CRectTracker](../../mfc/reference/crecttracker-class.md) 和外部大小调整句柄，`COleResizeBar` 对象显示。  
  
 `COleResizeBar` 对象通常是框架窗口对象的嵌入成员从 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) 选件类派生的。  
  
 有关更多信息，请参见文章 [启动](../../mfc/activation-cpp.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例SUPERPAD](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)