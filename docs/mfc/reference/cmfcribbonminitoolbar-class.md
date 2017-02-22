---
title: "CMFCRibbonMiniToolBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonMiniToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonMiniToolBar class"
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CMFCRibbonMiniToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现上下文快捷工具栏。  
  
## 语法  
  
```  
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|默认构造函数。|  
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|`CMFCRibbonMiniToolBar::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCRibbonMiniToolBar::GetThisClass`|由框架用于获取指向与此类类型关联的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象的指针。|  
|[CMFCRibbonMiniToolBar::IsContextMenuMode](../Topic/CMFCRibbonMiniToolBar::IsContextMenuMode.md)||  
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](../Topic/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar.md)|（重写 `CMFCPopupMenu::IsRibbonMiniToolBar`。）|  
|[CMFCRibbonMiniToolBar::SetCommands](../Topic/CMFCRibbonMiniToolBar::SetCommands.md)|设置要在工具栏上显示的命令的列表。|  
|[CMFCRibbonMiniToolBar::Show](../Topic/CMFCRibbonMiniToolBar::Show.md)|在指定的屏幕坐标上显示浮动工具栏。|  
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](../Topic/CMFCRibbonMiniToolBar::ShowWithContextMenu.md)|显示浮动工具栏以及上下文菜单。|  
  
## 备注  
 通常于用户在文档中选择对象后显示浮动工具栏。  例如，用户在文字处理程序中选择文本块后，应用程序将显示包含文本格式设置命令的浮动工具栏。  
  
 鼠标指针位于浮动工具栏边界之外时，浮动工具栏将变透明。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 `CMFCRibbonPanelMenu`  
  
 [CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)  
  
## 要求  
 **标头：**afxRibbonMiniToolBar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)