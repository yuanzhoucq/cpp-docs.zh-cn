---
title: "COleDropTarget Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDropTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDropTarget class"
  - "拖放, drop target"
  - "drop commands"
  - "drop commands, 接受"
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COleDropTarget Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供在窗口和OLE库之间的通信机制。  
  
## 语法  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleDropTarget::COleDropTarget](../Topic/COleDropTarget::COleDropTarget.md)|构造 `COleDropTarget` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDropTarget::OnDragEnter](../Topic/COleDropTarget::OnDragEnter.md)|调用，当光标首次进入窗口。|  
|[COleDropTarget::OnDragLeave](../Topic/COleDropTarget::OnDragLeave.md)|调用，当光标拖动到窗口之外。|  
|[COleDropTarget::OnDragOver](../Topic/COleDropTarget::OnDragOver.md)|重复调用，当光标拖动到窗口。|  
|[COleDropTarget::OnDragScroll](../Topic/COleDropTarget::OnDragScroll.md)|调用确定光标是否拖入窗口中滚动区域。|  
|[COleDropTarget::OnDrop](../Topic/COleDropTarget::OnDrop.md)|调用时，数据放置到窗口，默认处理程序。|  
|[COleDropTarget::OnDropEx](../Topic/COleDropTarget::OnDropEx.md)|调用时，数据放置到窗口，初始处理程序。|  
|[COleDropTarget::Register](../Topic/COleDropTarget::Register.md)|注册窗口作为有效的放置目标。|  
|[COleDropTarget::Revoke](../Topic/COleDropTarget::Revoke.md)|使窗口停止是有效的放置目标。|  
  
## 备注  
 创建此选件类对象允许窗口通过OLE拖放框架接受数据。  
  
 获取接受放置命令的窗口，应先创建 `COleDropTarget` 选件类的对象，然后调用于指针的 [注册](../Topic/COleDropTarget::Register.md) 功能设置为所需 `CWnd` 对象作为唯一参数传递。  
  
 有关使用OLE拖放操作的更多信息，请参见文章 [拖放\(OLE\)](../../mfc/drag-and-drop-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [MFC示例HIERSVR](../../top/visual-cpp-samples.md)   
 [MFC示例OCLIENT](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDropSource Class](../../mfc/reference/coledropsource-class.md)