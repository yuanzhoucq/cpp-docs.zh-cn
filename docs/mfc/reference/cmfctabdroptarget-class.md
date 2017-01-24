---
title: "CMFCTabDropTarget Class | Microsoft Docs"
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
  - "CMFCTabDropTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTabDropTarget class"
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCTabDropTarget Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供在选项卡控件和OLE库之间的通信机制。  
  
## 语法  
  
```  
class CMFCTabDropTarget : public COleDropTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCTabDropTarget::CMFCTabDropTarget`|默认构造函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCTabDropTarget::OnDragEnter](../Topic/CMFCTabDropTarget::OnDragEnter.md)|调用由结构，当用户拖动对象到选项卡窗口。  （重写 [COleDropTarget::OnDragEnter](../Topic/COleDropTarget::OnDragEnter.md)。）|  
|[CMFCTabDropTarget::OnDragLeave](../Topic/CMFCTabDropTarget::OnDragLeave.md)|调用由结构，当用户拖动对象在具有焦点的选项窗口之外。  （重写 [COleDropTarget::OnDragLeave](../Topic/COleDropTarget::OnDragLeave.md)。）|  
|[CMFCTabDropTarget::OnDragOver](../Topic/CMFCTabDropTarget::OnDragOver.md)|调用由结构，当用户拖动具有焦点的选项"窗口中的对象。  （重写 [COleDropTarget::OnDragOver](../Topic/COleDropTarget::OnDragOver.md)。）|  
|[CMFCTabDropTarget::OnDropEx](../Topic/CMFCTabDropTarget::OnDropEx.md)|调用由结构，当用户松开鼠标按钮拖动操作结束时。  （重写 [COleDropTarget::OnDropEx](../Topic/COleDropTarget::OnDropEx.md)。）|  
|[CMFCTabDropTarget::Register](../Topic/CMFCTabDropTarget::Register.md)|将控件注册为可以是OLE拖放操作的目标的一个。|  
  
### 备注  
 此选件类提供拖放支持。`CMFCBaseTabCtrl` 选件类。  如果您的应用程序初始化使用 [AfxOleInit](../Topic/AfxOleInit.md) 的OLE库函数，`CMFCBaseTabCtrl` 对象注册拖放操作的。  
  
 `CMFCTabDropTarget` 选件类通过在光标下的选项来扩展其基类，在对拖动操作将激活时。  有关拖放操作的更多信息，请参见 [拖放\(OLE\)](../../mfc/drag-and-drop-ole.md)。  
  
## 示例  
 下面的示例演示如何构造 `CMFCTabDropTarget` 对象并使用其 `Register` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/CPP/cmfctabdroptarget-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)  
  
 [CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)  
  
## 要求  
 **标头:** afxbasetabctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [拖放\(OLE\)](../../mfc/drag-and-drop-ole.md)