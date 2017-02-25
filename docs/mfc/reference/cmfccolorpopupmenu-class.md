---
title: "CMFCColorPopupMenu Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCColorPopupMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorPopupMenu class"
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CMFCColorPopupMenu Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示用户使用选择在文档或应用程序的颜色的弹出菜单。  
  
## 语法  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](../Topic/CMFCColorPopupMenu::CMFCColorPopupMenu.md)|构造 `CMFCColorPopupMenu` 对象。|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCColorPopupMenu::CreateTearOffBar](../Topic/CMFCColorPopupMenu::CreateTearOffBar.md)|创建可停靠拖曳到有色人种的区别不同。  （重写 [CMFCPopupMenu::CreateTearOffBar](../Topic/CMFCPopupMenu::CreateTearOffBar.md)。）|  
|[CMFCColorPopupMenu::GetMenuBar](../Topic/CMFCColorPopupMenu::GetMenuBar.md)|返回嵌入在弹出菜单中的 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)。  （重写 [CMFCPopupMenu::GetMenuBar](../Topic/CMFCPopupMenu::GetMenuBar.md)。）|  
|`CMFCColorPopupMenu::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCColorPopupMenu::SetPropList](../Topic/CMFCColorPopupMenu::SetPropList.md)|设置嵌入 `CMFCColorBar` 对象的属性网格控件对象。|  
  
### 数据成员  
  
|||  
|-|-|  
|名称|说明|  
|`m_bEnabledInCustomizeMode`|确定是否显示中的布尔值。|  
|`m_wndColorBar`|提供颜色选择的 `CMFCColorBar` 对象。|  
  
### 备注  
 此选件类继承 `CMFCPopupMenu` 选件类的弹出菜单功能和管理提供颜色选择的 `CMFCColorBar` 对象。  当工具栏结构在自定义模式时，并 `m_bEnabledInCustomizeMode` 成员设置为 `FALSE`，对有色人种的、对象不会显示。  有关自定义模式的更多信息，请参见 [CMFCToolBar::IsCustomizeMode](../Topic/CMFCToolBar::IsCustomizeMode.md)  
  
 有关 `CMFCColorBar`的更多信息，请参见[CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## 要求  
 **标头:** afxcolorpopupmenu.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)