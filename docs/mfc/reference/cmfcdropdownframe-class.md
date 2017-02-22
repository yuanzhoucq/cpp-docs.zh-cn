---
title: "CMFCDropDownFrame Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDropDownFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDropDownFrame class"
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMFCDropDownFrame Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供下拉式框架窗口的功能。下拉式工具栏和下拉式工具栏按钮。  
  
## 语法  
  
```  
class CMFCDropDownFrame : public CMiniFrameWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCDropDownFrame::CMFCDropDownFrame`|默认构造函数。|  
|`CMFCDropDownFrame::~CMFCDropDownFrame`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCDropDownFrame::Create](../Topic/CMFCDropDownFrame::Create.md)|创建一个 `CMFCDropDownFrame` 对象。|  
|`CMFCDropDownFrame::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCDropDownFrame::GetParentMenuBar](../Topic/CMFCDropDownFrame::GetParentMenuBar.md)|检索下拉式帧的父级菜单栏。|  
|[CMFCDropDownFrame::GetParentPopupMenu](../Topic/CMFCDropDownFrame::GetParentPopupMenu.md)|检索下拉式帧的父级弹出菜单。|  
|`CMFCDropDownFrame::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCDropDownFrame::RecalcLayout](../Topic/CMFCDropDownFrame::RecalcLayout.md)|重新定位下拉式帧。|  
|[CMFCDropDownFrame::SetAutoDestroy](../Topic/CMFCDropDownFrame::SetAutoDestroy.md)|设置是否自动销毁子下拉式工具栏窗口。|  
  
### 备注  
 此类不适于在您的代码中直接使用。  
  
 框架使用此选件类提供框架行为。`CMFCDropDownToolbar` 和 `CMFCDropDownToolbarButton` 选件类。  有关这些类的更多信息，请参见 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md) 和 [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。  
  
## 示例  
 下面的示例演示如何检索指向 `CMFCDropDownFrame` 对象从 `CFrameWnd` 选件类以及如何设置将自动销毁的子下拉式工具栏窗口。  
  
 [!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/CPP/cmfcdropdownframe-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)  
  
## 要求  
 **标头:** afxdropdowntoolbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)