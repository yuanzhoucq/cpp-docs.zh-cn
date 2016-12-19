---
title: "CPagerCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPagerCtrl class"
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
caps.latest.revision: 26
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPagerCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CPagerCtrl` 选件类包装Windows页导航控件，可以滚动到视图中包含的窗口不适合包含窗口。  
  
## 语法  
  
```  
class CPagerCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPagerCtrl::CPagerCtrl](../Topic/CPagerCtrl::CPagerCtrl.md)|构造 `CPagerCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPagerCtrl::Create](../Topic/CPagerCtrl::Create.md)|使用指定的样式创建一个页导航控件并将其附加到当前 `CPagerCtrl` 对象。|  
|[CPagerCtrl::CreateEx](../Topic/CPagerCtrl::CreateEx.md)|使用指定的扩展样式创建一个页导航控件并将其附加到当前 `CPagerCtrl` 对象。|  
|[CPagerCtrl::ForwardMouse](../Topic/CPagerCtrl::ForwardMouse.md)|启用或禁用 [WM\_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) 消息转发到当前页导航控件中包含的窗口。|  
|[CPagerCtrl::GetBkColor](../Topic/CPagerCtrl::GetBkColor.md)|检索当前页导航控件的背景色。|  
|[CPagerCtrl::GetBorder](../Topic/CPagerCtrl::GetBorder.md)|检索当前页导航控件的边框大小。|  
|[CPagerCtrl::GetButtonSize](../Topic/CPagerCtrl::GetButtonSize.md)|检索当前页导航控件的按钮大小。|  
|[CPagerCtrl::GetButtonState](../Topic/CPagerCtrl::GetButtonState.md)|检索指定的按钮的状态在当前页导航控件的。|  
|[CPagerCtrl::GetDropTarget](../Topic/CPagerCtrl::GetDropTarget.md)|检索当前页导航控件的 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) 接口。|  
|[CPagerCtrl::GetScrollPos](../Topic/CPagerCtrl::GetScrollPos.md)|检索当前页导航控件的滚动位置。|  
|[CPagerCtrl::IsButtonDepressed](../Topic/CPagerCtrl::IsButtonDepressed.md)|指示当前页导航控件的指定按钮是否在 `pressed` 状态。|  
|[CPagerCtrl::IsButtonGrayed](../Topic/CPagerCtrl::IsButtonGrayed.md)|指示当前页导航控件的指定按钮是否在 `grayed` 状态。|  
|[CPagerCtrl::IsButtonHot](../Topic/CPagerCtrl::IsButtonHot.md)|指示当前页导航控件的指定按钮是否在 `hot` 状态。|  
|[CPagerCtrl::IsButtonInvisible](../Topic/CPagerCtrl::IsButtonInvisible.md)|指示当前页导航控件的指定按钮是否在 `invisible` 状态。|  
|[CPagerCtrl::IsButtonNormal](../Topic/CPagerCtrl::IsButtonNormal.md)|指示当前页导航控件的指定按钮是否在 `normal` 状态。|  
|[CPagerCtrl::RecalcSize](../Topic/CPagerCtrl::RecalcSize.md)|使当前页导航控件重新计算包含的窗口的大小。|  
|[CPagerCtrl::SetBkColor](../Topic/CPagerCtrl::SetBkColor.md)|设置当前页导航控件的背景色。|  
|[CPagerCtrl::SetBorder](../Topic/CPagerCtrl::SetBorder.md)|设置当前页导航控件的边框大小。|  
|[CPagerCtrl::SetButtonSize](../Topic/CPagerCtrl::SetButtonSize.md)|设置当前页导航控件的按钮大小。|  
|[CPagerCtrl::SetChild](../Topic/CPagerCtrl::SetChild.md)|设置当前页导航控件所包含的窗口。|  
|[CPagerCtrl::SetScrollPos](../Topic/CPagerCtrl::SetScrollPos.md)|设置当前页导航控件的滚动位置。|  
  
## 备注  
 页导航控件是包含另一个窗口大于包含窗口线性和，并使您可以将包含窗口到视图的窗口。  页导航控件显示自动消失的两个滚动按钮，当包含窗口移动到其最多的程度，而否则再次出现。  可以创建水平或垂直滚动的页导航控件。  
  
 例如，在中，如果应用程序具有不够宽显示其所有项目的工具栏，可以将工具栏添加到页导航控件，用户可以移动工具栏向左或向右到项目的所有访问。  Microsoft Internet Explorer 4.0版\(commctrl.dll 4.71版\)引入页导航控件。  
  
 `CPagerCtrl` 选件类从 [CWnd](../../mfc/reference/cwnd-class.md) 选件类派生。  有关更多信息和寻呼机控件的说明，请参见 [页导航控件](http://msdn.microsoft.com/library/windows/desktop/bb760855)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## 要求  
 **标头:** afxcmn.h  
  
## 请参阅  
 [CPagerCtrl Class](../../mfc/reference/cpagerctrl-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [页导航控件](http://msdn.microsoft.com/library/windows/desktop/bb760855)