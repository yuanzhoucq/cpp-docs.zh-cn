---
title: "CMFCAutoHideButton Class | Microsoft Docs"
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
  - "CMFCAutoHideButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAutoHideButton class"
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCAutoHideButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显示或隐藏配置为隐藏的 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的按钮。  
  
## 语法  
  
```  
class CMFCAutoHideButton : public CObject  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCAutoHideButton::BringToTop](../Topic/CMFCAutoHideButton::BringToTop.md)||  
|[CMFCAutoHideButton::Create](../Topic/CMFCAutoHideButton::Create.md)|创建并初始化自动隐藏按钮。|  
|[CMFCAutoHideButton::GetAlignment](../Topic/CMFCAutoHideButton::GetAlignment.md)|检索自动隐藏按钮的对齐方式。|  
|[CMFCAutoHideButton::GetAutoHideWindow](../Topic/CMFCAutoHideButton::GetAutoHideWindow.md)|返回与自动隐藏按钮关联的 [CDockablePane](../../mfc/reference/cdockablepane-class.md) 对象。|  
|[CMFCAutoHideButton::GetParentToolBar](../Topic/CMFCAutoHideButton::GetParentToolBar.md)||  
|[CMFCAutoHideButton::GetRect](../Topic/CMFCAutoHideButton::GetRect.md)||  
|[CMFCAutoHideButton::GetSize](../Topic/CMFCAutoHideButton::GetSize.md)|确定自动隐藏按钮的大小。|  
|[CMFCAutoHideButton::GetTextSize](../Topic/CMFCAutoHideButton::GetTextSize.md)|返回自动隐藏按钮的文本标签大小。|  
|[CMFCAutoHideButton::HighlightButton](../Topic/CMFCAutoHideButton::HighlightButton.md)|突出显示自动隐藏按钮。|  
|[CMFCAutoHideButton::IsActive](../Topic/CMFCAutoHideButton::IsActive.md)|指示自动隐藏按钮是否处于活动状态。|  
|[CMFCAutoHideButton::IsHighlighted](../Topic/CMFCAutoHideButton::IsHighlighted.md)|返回自动隐藏按钮的突出显示状态。|  
|[CMFCAutoHideButton::IsHorizontal](../Topic/CMFCAutoHideButton::IsHorizontal.md)|确定自动隐藏按钮的方向是水平还是垂直。|  
|[CMFCAutoHideButton::IsTop](../Topic/CMFCAutoHideButton::IsTop.md)||  
|[CMFCAutoHideButton::IsVisible](../Topic/CMFCAutoHideButton::IsVisible.md)|指示按钮是否可见。|  
|[CMFCAutoHideButton::Move](../Topic/CMFCAutoHideButton::Move.md)||  
|[CMFCAutoHideButton::OnDraw](../Topic/CMFCAutoHideButton::OnDraw.md)|框架在绘制自动隐藏按钮时调用此方法。|  
|[CMFCAutoHideButton::OnDrawBorder](../Topic/CMFCAutoHideButton::OnDrawBorder.md)|框架在绘制自动隐藏按钮的边框时调用此方法。|  
|[CMFCAutoHideButton::OnFillBackground](../Topic/CMFCAutoHideButton::OnFillBackground.md)|框架在填充自动隐藏按钮的背景时调用此方法。|  
|[CMFCAutoHideButton::ReplacePane](../Topic/CMFCAutoHideButton::ReplacePane.md)||  
|[CMFCAutoHideButton::ShowAttachedWindow](../Topic/CMFCAutoHideButton::ShowAttachedWindow.md)|显示或隐藏关联的 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)。|  
|[CMFCAutoHideButton::ShowButton](../Topic/CMFCAutoHideButton::ShowButton.md)|显示或隐藏自动隐藏按钮。|  
|[CMFCAutoHideButton::UnSetAutoHideMode](../Topic/CMFCAutoHideButton::UnSetAutoHideMode.md)||  
  
## 备注  
 在创建过程中，`CMFCAutoHideButton` 对象附加到 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)。  `CDockablePane` 对象随着用户与 `CMFCAutoHideButton` 对象交互而隐藏或显示。  
  
 默认情况下，框架在用户打开“自动隐藏”时自动创建 `CMFCAutoHideButton`。  框架可创建自定义 UI 类的元素而不是 `CMFCAutoHideButton` 类。  若要指定框架应使用的自定义 UI 类，请将静态成员变量 `CMFCAutoHideBar::m_pAutoHideButtonRTS` 设置为自定义 UI 类。  默认情况下，此变量设置为 `CMFCAutoHideButton`。  
  
## 示例  
 下面的示例演示如何构造 `CMFCAutoHideButton` 对象和在 `CMFCAutoHideButton` 类中使用各种方法。  该示例演示如何使用 `CMFCAutoHideButton` 对象的 `Create` 方法来初始化该对象，并显示关联的 `CDockablePane` 类和自动隐藏按钮。  
  
 [!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/CPP/cmfcautohidebutton-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)  
  
## 要求  
 **标头：**afxautohidebutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCAutoHideBar Class](../../mfc/reference/cmfcautohidebar-class.md)   
 [CAutoHideDockSite Class](../../mfc/reference/cautohidedocksite-class.md)