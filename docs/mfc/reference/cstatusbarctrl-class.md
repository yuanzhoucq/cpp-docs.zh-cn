---
title: "CStatusBarCtrl Class | Microsoft Docs"
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
  - "CStatusBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBarCtrl class"
  - "status bar controls"
  - "Windows common controls [C++], CStatusBarCtrl"
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStatusBarCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常见状态栏控件的功能。  
  
## 语法  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CStatusBarCtrl::CStatusBarCtrl](../Topic/CStatusBarCtrl::CStatusBarCtrl.md)|构造 `CStatusBarCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CStatusBarCtrl::Create](../Topic/CStatusBarCtrl::Create.md)|创建状态栏控件并将它附加到 `CStatusBarCtrl` 对象。|  
|[CStatusBarCtrl::CreateEx](../Topic/CStatusBarCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建状态栏控件并将它附加到 `CStatusBarCtrl` 对象。|  
|[CStatusBarCtrl::DrawItem](../Topic/CStatusBarCtrl::DrawItem.md)|调用，当所有者描述状态栏控件中的可视方面是。|  
|[CStatusBarCtrl::GetBorders](../Topic/CStatusBarCtrl::GetBorders.md)|检索状态栏控件的水平和垂直边框的当前宽度。|  
|[CStatusBarCtrl::GetIcon](../Topic/CStatusBarCtrl::GetIcon.md)|检索一部分\(也称为窗格\)图标在当前状态栏控件。|  
|[CStatusBarCtrl::GetParts](../Topic/CStatusBarCtrl::GetParts.md)|从中检索节的计数在状态栏控件的。|  
|[CStatusBarCtrl::GetRect](../Topic/CStatusBarCtrl::GetRect.md)|检索一部分的边框在状态栏控件的。|  
|[CStatusBarCtrl::GetText](../Topic/CStatusBarCtrl::GetText.md)|从状态栏控件的特定部分检索文本。|  
|[CStatusBarCtrl::GetTextLength](../Topic/CStatusBarCtrl::GetTextLength.md)|从状态栏控件的特定部分检索长度，在字符，该文本。|  
|[CStatusBarCtrl::GetTipText](../Topic/CStatusBarCtrl::GetTipText.md)|检索一个窗格的工具提示文本在状态栏。|  
|[CStatusBarCtrl::IsSimple](../Topic/CStatusBarCtrl::IsSimple.md)|检查一种状态windows控件确定它是否在简单的模式。|  
|[CStatusBarCtrl::SetBkColor](../Topic/CStatusBarCtrl::SetBkColor.md)|设置在状态栏的背景色。|  
|[CStatusBarCtrl::SetIcon](../Topic/CStatusBarCtrl::SetIcon.md)|设置一个窗格中的图标状态栏。|  
|[CStatusBarCtrl::SetMinHeight](../Topic/CStatusBarCtrl::SetMinHeight.md)|设置状态栏控件的绘图区的最小高度。|  
|[CStatusBarCtrl::SetParts](../Topic/CStatusBarCtrl::SetParts.md)|设置节的数量在状态栏控件的和每个部分右边缘的坐标。|  
|[CStatusBarCtrl::SetSimple](../Topic/CStatusBarCtrl::SetSimple.md)|指定状态栏控件是否显示简单的文本或显示先前的设置的所有控件部件调用 `SetParts`。|  
|[CStatusBarCtrl::SetText](../Topic/CStatusBarCtrl::SetText.md)|设置在状态栏控件特定部分的文本。|  
|[CStatusBarCtrl::SetTipText](../Topic/CStatusBarCtrl::SetTipText.md)|设置一个窗格的工具提示文本在状态栏。|  
  
## 备注  
 “状态栏控件”是一级别的窗口，通常显示在父窗口的底部，应用程序可以显示各种状态信息。  状态栏控件可分为部件显示多信息的一种类型。  
  
 此控件\(并 `CStatusBarCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 有关使用 `CStatusBarCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl Class](../../mfc/reference/ctoolbarctrl-class.md)