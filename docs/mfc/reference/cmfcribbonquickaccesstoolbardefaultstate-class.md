---
title: "CMFCRibbonQuickAccessToolBarDefaultState Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonQuickAccessToolBarDefaultState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonQuickAccessToolBarDefaultState class"
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCRibbonQuickAccessToolBarDefaultState Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理快速访问工具栏的默认状态在功能区栏的帮助器选件类\([CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)\)确定。  
  
## 语法  
  
```  
class CMFCRibbonQuickAccessToolBarDefaultState  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState.md)|构造 `CMFCRibbonQuickAccessToolbarDefaultState` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand.md)|添加一个命令快速访问工具栏的默认状态。  这不更改工具栏。|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom.md)|复制快速访问工具栏属性到另一个。|  
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll.md)|从快速访问工具栏上的所有命令。  这不更改工具栏。|  
  
## 备注  
 可以在您的应用程序中创建快速访问工具栏，建议您通过调用 [CMFCRibbonBar::SetQuickAccessDefaultState](../Topic/CMFCRibbonBar::SetQuickAccessDefaultState.md)设置其默认状态。  此默认状态下，当用户在应用程序中 **选项** 对话框时，**自定义** 页单击 **重置** 按钮还原。  
  
## 继承层次结构  
 [CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)  
  
## 示例  
 下面的示例演示如何构造对象 `CMFCRibbonQuickAccessToolbarDefaultState` 选件类以及如何将命令添加到快速访问工具栏的默认状态。  
  
 [!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/CPP/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]  
  
## 要求  
 **标头:** afxribbonquickaccesstoolbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBar::SetQuickAccessDefaultState](../Topic/CMFCRibbonBar::SetQuickAccessDefaultState.md)