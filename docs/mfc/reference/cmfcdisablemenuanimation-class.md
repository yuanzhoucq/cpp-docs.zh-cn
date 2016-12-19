---
title: "CMFCDisableMenuAnimation Class | Microsoft Docs"
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
  - "CMFCDisableMenuAnimation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDisableMenuAnimation class"
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDisableMenuAnimation Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

禁用弹出菜单动画。  
  
## 语法  
  
```  
class CMFCDisableMenuAnimation  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|构造 `CMFCDisableMenuAnimation` 对象。|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCDisableMenuAnimation::Restore](../Topic/CMFCDisableMenuAnimation::Restore.md)|还原使用的结构显示弹出菜单的前一动画。|  
  
### 数据成员  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCDisableMenuAnimation::m_animType`|存储以前的弹出菜单动画类型。|  
  
### 备注  
 使用此帮助器类选件暂时禁用弹出菜单动画\(例如，那么，当您处理鼠标或键盘命令时）。  
  
 在其生存期内，`CMFCDisableMenuAnimation` 对象禁用弹出菜单动画。  构造函数存储当前弹出菜单动画输入 `m_animType` 字段并设置当前动画类型。`CMFCPopupMenu::NO_ANIMATION`。  析构函数恢复前一动画类型。  
  
 可以在堆栈上创建 `CMFCDisableMenuAnimation` 对象来禁用了一个功能中的弹出菜单动画。  如果想要禁用功能之间的弹出菜单动画，请创建一个堆的一 `CMFCDisableMenuAnimation` 对象并将其删除，当您希望还原弹出菜单动画时。  
  
## 示例  
 下面的示例演示如何使用堆栈暂时禁用菜单动画。  
  
 [!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/CPP/cmfcdisablemenuanimation-class_1.h)]  
  
## 继承层次结构  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## 要求  
 **标头:** afxpopupmenu.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)