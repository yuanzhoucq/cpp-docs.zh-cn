---
title: "CReBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CReBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBar class"
  - "Internet Explorer 4.0 common controls"
  - "rebar controls, control bar"
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CReBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对于rebar控件提供布局、持久性和状态信息的控制条。  
  
## 语法  
  
```  
  
class CReBar : public CControlBar  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CReBar::AddBar](../Topic/CReBar::AddBar.md)|添加一个带区到rebar。|  
|[CReBar::Create](../Topic/CReBar::Create.md)|创建rebar控件并将它附加到 `CReBar` 对象。|  
|[CReBar::GetReBarCtrl](../Topic/CReBar::GetReBarCtrl.md)|允许直接访问基础公共控件。|  
  
## 备注  
 rebar对象可以包含各种子窗口，通常其他控件，包括编辑框，工具栏，而列表框。  rebar对象可以显示其在指定的位图的子窗口。  应用程序可以自动调整rebar，或者用户可以通过单击或拖动其手柄条手动调整rebar。  
  
 ![RebarMenu 示例](../../mfc/reference/media/vc4sc61.png "vc4SC61")  
  
## Rebar控件  
 rebar对象的行为类似于工具栏对象。  rebar使用单击和拖动结构调整其带区。  rebar控件可以包含一个或多个带区，在每个带区具有手柄栏、位图、文本标签和子窗口的任意组合。  但是，带区不能包含多个子窗口。  
  
 **CReBar** 使用 [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) 选件类提供其实现。  可以访问rebar控件通过利用控件的自定义选项的 [GetReBarCtrl](../Topic/CReBar::GetReBarCtrl.md)。  有关rebar控件的更多信息，请参见 `CReBarCtrl`。  有关使用rebar控件的更多信息，请参见 [使用CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
> [!CAUTION]
>  Rebar和rebar控件对象不支持MFC控件条停靠。  如果 **CRebar::EnableDocking** 调用，应用程序将断言。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [MFC示例MFCIE](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)