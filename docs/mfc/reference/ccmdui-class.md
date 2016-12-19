---
title: "CCmdUI Class | Microsoft Docs"
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
  - "CCmdUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "按钮 [C++], 在上下文更改时更新"
  - "CCmdUI class"
  - "command user interface"
  - "命令 [C++], updating UI"
  - "menus [C++], 在上下文更改时更新"
  - "states, updating user interface object"
  - "工具栏 [C++], 更新"
  - "updating user interfaces for commands"
  - "用户界面, 更新"
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCmdUI Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 `ON_UPDATE_COMMAND_UI` 处理程序在 `CCmdTarget`派生类内使用。  
  
## 语法  
  
```  
class CCmdUI  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCmdUI::ContinueRouting](../Topic/CCmdUI::ContinueRouting.md)|调用命令传送结构继续路由在处理程序中链的当前消息。|  
|[CCmdUI::Enable](../Topic/CCmdUI::Enable.md)|启用或禁用此命令的用户界面项。|  
|[CCmdUI::SetCheck](../Topic/CCmdUI::SetCheck.md)|设置用户界面项的复选状态此命令的。|  
|[CCmdUI::SetRadio](../Topic/CCmdUI::SetRadio.md)|与 `SetCheck` 成员函数，但是，在无线组。|  
|[CCmdUI::SetText](../Topic/CCmdUI::SetText.md)|设置用户界面项的文本此命令的。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CCmdUI::m\_nID](../Topic/CCmdUI::m_nID.md)|用户界面对象的ID。|  
|[CCmdUI::m\_nIndex](../Topic/CCmdUI::m_nIndex.md)|用户界面对象的索引。|  
|[CCmdUI::m\_pMenu](../Topic/CCmdUI::m_pMenu.md)|指向 `CCmdUI` 对象表示的菜单。|  
|[CCmdUI::m\_pOther](../Topic/CCmdUI::m_pOther.md)|指向窗口发送通知的对象。|  
|[CCmdUI::m\_pSubMenu](../Topic/CCmdUI::m_pSubMenu.md)|指向 `CCmdUI` 对象表示的该包含的子菜单。|  
  
## 备注  
 `CCmdUI` 没有基类。  
  
 当您的应用程序的用户拉下菜单时，每个菜单项需要知道是否应显示为启用或禁用。  菜单命令的目标通过实现 `ON_UPDATE_COMMAND_UI` 处理程序提供此信息。  对于每个在应用程序的命令用户界面对象，请使用"属性"窗口创建每个处理程序的消息映射项和函数原型。  
  
 当菜单中拉下时，框架搜索并对每 `ON_UPDATE_COMMAND_UI` 处理程序，每个处理程序调用 `CCmdUI` 成员函数例如 **Enable** 和 **Check**，并且，框架然后适当地显示每个菜单项。  
  
 菜单项可以用控件栏按钮或其他命令用户界面对象替换，而不更改在 `ON_UPDATE_COMMAND_UI` 处理程序内的代码。  
  
 下表总结了功能在不同的命令用户界面项目中的角色`CCmdUI`的成员。  
  
|用户界面项|启用|SetCheck|SetRadio|SetText|  
|-----------|--------|--------------|--------------|-------------|  
|Menu item|启用或禁用|检查\(×\)或取消选中|使用点的检查\(•\)|设置项目文本|  
|工具栏按钮|启用或禁用|选择，unselects或不确定|和 `SetCheck`相同|（不适用）|  
|状态栏窗格|使文本可见或不可见|设置方式安排或规则边框|和 `SetCheck`相同|设置窗格文本|  
|在 `CDialogBar`的普通按钮|启用或禁用|检查或取消选中复选框|和 `SetCheck`相同|设置按钮文本|  
|在 `CDialogBar`的规则控件|启用或禁用|（不适用）|（不适用）|设置窗口文本|  
  
 有关更多选件在使用此类，请参见 [如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)。  
  
## 继承层次结构  
 `CCmdUI`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC MDI示例](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)