---
title: "COleDropSource Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDropSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDropSource class"
  - "拖放, drop source"
  - "拖动操作"
  - "drop target, dragging data to"
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleDropSource Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允许数据拖至放置目标。  
  
## 语法  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleDropSource::COleDropSource](../Topic/COleDropSource::COleDropSource.md)|构造 `COleDropSource` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDropSource::GiveFeedback](../Topic/COleDropSource::GiveFeedback.md)|在拖放操作过程中更改光标。|  
|[COleDropSource::OnBeginDrag](../Topic/COleDropSource::OnBeginDrag.md)|处理鼠标捕获在拖放操作过程。|  
|[COleDropSource::QueryContinueDrag](../Topic/COleDropSource::QueryContinueDrag.md)|检查拖动是否应继续。|  
  
## 备注  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md) 选件类处理拖放操作接收的一部分。  `COleDropSource` 对象以确定拖动操作开始，提供反馈在拖动操作过程并确定负责，在拖动操作的末尾。  
  
 若要使用 `COleDropSource` 对象，请调用构造函数。  这简化了处理确定使用 [COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)、 [COleClientItem::DoDragDrop](../Topic/COleClientItem::DoDragDrop.md)或 [COleServerItem::DoDragDrop](../Topic/COleServerItem::DoDragDrop.md) 功能，哪些操作，如鼠标单击，启动拖动操作。  这些功能将会为您创建一 `COleDropSource` 对象。  您可能需要修改 `COleDropSource` 可重写的函数的默认行为。  这些成员函数将调用相应的时间由框架。  
  
 有关使用OLE拖放操作的更多信息，请参见文章 [拖放\(OLE\)](../../mfc/drag-and-drop-ole.md)。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [MFC示例OCLIENT](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)