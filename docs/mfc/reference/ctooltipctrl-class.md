---
title: "CToolTipCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolTipCtrl class"
  - "data tips [C++]"
  - "工具提示 [C++], tool tip controls"
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CToolTipCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装“工具提示控件的功能，”显示描述工具的目的单行文本在应用程序的小型弹出窗口。  
  
## 语法  
  
```  
class CToolTipCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CToolTipCtrl::CToolTipCtrl](../Topic/CToolTipCtrl::CToolTipCtrl.md)|构造 `CToolTipCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CToolTipCtrl::Activate](../Topic/CToolTipCtrl::Activate.md)|激活和停用工具提示控件。|  
|[CToolTipCtrl::AddTool](../Topic/CToolTipCtrl::AddTool.md)|注册具有以下工具提示控件的工具。|  
|[CToolTipCtrl::AdjustRect](../Topic/CToolTipCtrl::AdjustRect.md)|在工具提示控件的文本显示矩形和窗口矩形之间的转换。|  
|[CToolTipCtrl::Create](../Topic/CToolTipCtrl::Create.md)|创建一个工具提示控件并将它附加到 `CToolTipCtrl` 对象。|  
|[CToolTipCtrl::CreateEx](../Topic/CToolTipCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个工具提示控件并将它附加到 `CToolTipCtrl` 对象。|  
|[CToolTipCtrl::DelTool](../Topic/CToolTipCtrl::DelTool.md)|从工具提示控件移除工具。|  
|[CToolTipCtrl::GetBubbleSize](../Topic/CToolTipCtrl::GetBubbleSize.md)|检索工具提示的大小。|  
|[CToolTipCtrl::GetCurrentTool](../Topic/CToolTipCtrl::GetCurrentTool.md)|检索信息，如大小、位置和文本当前工具提示控件公开的，工具提示窗口。|  
|[CToolTipCtrl::GetDelayTime](../Topic/CToolTipCtrl::GetDelayTime.md)|检索为工具提示控件当前设置的首字母、弹出窗口以及reshow持续时间。|  
|[CToolTipCtrl::GetMargin](../Topic/CToolTipCtrl::GetMargin.md)|检索为工具提示窗口中设置的顶部，左侧，底部和右边距。|  
|[CToolTipCtrl::GetMaxTipWidth](../Topic/CToolTipCtrl::GetMaxTipWidth.md)|检索工具提示窗口的最大宽度。|  
|[CToolTipCtrl::GetText](../Topic/CToolTipCtrl::GetText.md)|检索工具提示控件为工具维护的文本。|  
|[CToolTipCtrl::GetTipBkColor](../Topic/CToolTipCtrl::GetTipBkColor.md)|检索在工具提示窗口的背景色。|  
|[CToolTipCtrl::GetTipTextColor](../Topic/CToolTipCtrl::GetTipTextColor.md)|检索在工具提示窗口的文本颜色。|  
|[CToolTipCtrl::GetTitle](../Topic/CToolTipCtrl::GetTitle.md)|检索当前工具提示控件的标题。|  
|[CToolTipCtrl::GetToolCount](../Topic/CToolTipCtrl::GetToolCount.md)|检索工具提示控件维护工具的计数。|  
|[CToolTipCtrl::GetToolInfo](../Topic/CToolTipCtrl::GetToolInfo.md)|检索工具提示控件维护有关工具的信息。|  
|[CToolTipCtrl::HitTest](../Topic/CToolTipCtrl::HitTest.md)|测试点确定它是否在特定工具的边框内。  如果是这样，检索有关工具的信息。|  
|[CToolTipCtrl::Pop](../Topic/CToolTipCtrl::Pop.md)|从视图中移除一个突出显示的工具提示窗口。|  
|[CToolTipCtrl::Popup](../Topic/CToolTipCtrl::Popup.md)|使当前工具提示控件显示上次鼠标消息的坐标。|  
|[CToolTipCtrl::RelayEvent](../Topic/CToolTipCtrl::RelayEvent.md)|通过鼠标消息处理的工具提示控件。|  
|[CToolTipCtrl::SetDelayTime](../Topic/CToolTipCtrl::SetDelayTime.md)|设置初始、弹出窗口以及reshow持续时间工具提示控件的。|  
|[CToolTipCtrl::SetMargin](../Topic/CToolTipCtrl::SetMargin.md)|设置工具提示窗口的顶部，左侧，底部和右边距。|  
|[CToolTipCtrl::SetMaxTipWidth](../Topic/CToolTipCtrl::SetMaxTipWidth.md)|设置工具提示窗口的最大宽度。|  
|[CToolTipCtrl::SetTipBkColor](../Topic/CToolTipCtrl::SetTipBkColor.md)|设置在工具提示窗口的背景色。|  
|[CToolTipCtrl::SetTipTextColor](../Topic/CToolTipCtrl::SetTipTextColor.md)|设置在工具提示窗口的文本颜色。|  
|[CToolTipCtrl::SetTitle](../Topic/CToolTipCtrl::SetTitle.md)|添加标准图标和前缀字符串传递到工具提示。|  
|[CToolTipCtrl::SetToolInfo](../Topic/CToolTipCtrl::SetToolInfo.md)|设置工具提示中为工具维护的信息。|  
|[CToolTipCtrl::SetToolRect](../Topic/CToolTipCtrl::SetToolRect.md)|设置工具的一个新的边框。|  
|[CToolTipCtrl::SetWindowTheme](../Topic/CToolTipCtrl::SetWindowTheme.md)|设置工具提示窗口的视觉样式。|  
|[CToolTipCtrl::Update](../Topic/CToolTipCtrl::Update.md)|强制当前工具都重绘。|  
|[CToolTipCtrl::UpdateTipText](../Topic/CToolTipCtrl::UpdateTipText.md)|设置工具的工具提示文本。|  
  
## 备注  
 “工具”是一个窗口，例如子窗口或控件或在窗口的工作区的应用程序定义的矩形区域。  工具提示在大多数情况下隐藏，仅当用户在工具中将光标放在并为大约一半一秒保持原样存在。  当用户单击鼠标按钮或移动光标工具，工具提示在光标旁边显示和消失。  
  
 `CToolTipCtrl` 提供功能控制工具提示、边距宽度包围工具提示文本的早期时间和时间，宽度的工具提示窗口和工具提示的背景和文本颜色的。  一个工具提示控件可以针对多个工具的信息。  
  
 `CToolTipCtrl` 选件类提供Windows常用工具提示控件的功能。  此控件\(并 `CToolTipCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 有关启用工具提示的更多信息，请参见 [在从CFrameWnd未派生的Windows的工具提示](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。  
  
 有关使用 `CToolTipCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CToolTipCtrl](../../mfc/using-ctooltipctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolTipCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)