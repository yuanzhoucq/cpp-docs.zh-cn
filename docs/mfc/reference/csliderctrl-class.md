---
title: "CSliderCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSliderCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSliderCtrl class"
  - "CSliderCtrl class, 公共控件"
  - "滑块控件, CSliderCtrl class"
  - "Windows common controls [C++], CSliderCtrl"
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CSliderCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常见滑块控件的功能。  
  
## 语法  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSliderCtrl::CSliderCtrl](../Topic/CSliderCtrl::CSliderCtrl.md)|构造 `CSliderCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSliderCtrl::ClearSel](../Topic/CSliderCtrl::ClearSel.md)|清除在滑块控件的当前选择。|  
|[CSliderCtrl::ClearTics](../Topic/CSliderCtrl::ClearTics.md)|从滑块控件中移除当前刻度线。|  
|[CSliderCtrl::Create](../Topic/CSliderCtrl::Create.md)|创建一个滑块控件并将它附加到 `CSliderCtrl` 对象。|  
|[CSliderCtrl::CreateEx](../Topic/CSliderCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个滑块控件并将它附加到 `CSliderCtrl` 对象。|  
|[CSliderCtrl::GetBuddy](../Topic/CSliderCtrl::GetBuddy.md)|检索句柄滑块控件合作者窗口在特定位置。|  
|[CSliderCtrl::GetChannelRect](../Topic/CSliderCtrl::GetChannelRect.md)|检索滑块控件通道的大小。|  
|[CSliderCtrl::GetLineSize](../Topic/CSliderCtrl::GetLineSize.md)|检索滑块控件的行的大小。|  
|[CSliderCtrl::GetNumTics](../Topic/CSliderCtrl::GetNumTics.md)|检索刻度线的数目。滑块控件的。|  
|[CSliderCtrl::GetPageSize](../Topic/CSliderCtrl::GetPageSize.md)|检索滑块控件的页大小。|  
|[CSliderCtrl::GetPos](../Topic/CSliderCtrl::GetPos.md)|检索滑块的当前位置。|  
|[CSliderCtrl::GetRange](../Topic/CSliderCtrl::GetRange.md)|检索滑块的最小和最大位置。|  
|[CSliderCtrl::GetRangeMax](../Topic/CSliderCtrl::GetRangeMax.md)|检索滑块的最大位置。|  
|[CSliderCtrl::GetRangeMin](../Topic/CSliderCtrl::GetRangeMin.md)|检索滑块的最小的位置。|  
|[CSliderCtrl::GetSelection](../Topic/CSliderCtrl::GetSelection.md)|检索当前选择的大小。|  
|[CSliderCtrl::GetThumbLength](../Topic/CSliderCtrl::GetThumbLength.md)|检索滑块的长度在当前trackbar控件的。|  
|[CSliderCtrl::GetThumbRect](../Topic/CSliderCtrl::GetThumbRect.md)|检索滑块控件的滚动块的大小。|  
|[CSliderCtrl::GetTic](../Topic/CSliderCtrl::GetTic.md)|检索指定的刻度线的位置。|  
|[CSliderCtrl::GetTicArray](../Topic/CSliderCtrl::GetTicArray.md)|检索滴答滑块控件的标记位置。|  
|[CSliderCtrl::GetTicPos](../Topic/CSliderCtrl::GetTicPos.md)|检索指定的刻度线的位置，在工作区坐标。|  
|[CSliderCtrl::GetToolTips](../Topic/CSliderCtrl::GetToolTips.md)|检索处理与工具提示控件分配给滑块控件，因此，如果有的话）。|  
|[CSliderCtrl::SetBuddy](../Topic/CSliderCtrl::SetBuddy.md)|分布窗口作为合作者窗口对slider控件。|  
|[CSliderCtrl::SetLineSize](../Topic/CSliderCtrl::SetLineSize.md)|设置滑块控件的行的大小。|  
|[CSliderCtrl::SetPageSize](../Topic/CSliderCtrl::SetPageSize.md)|设置滑块控件的页大小。|  
|[CSliderCtrl::SetPos](../Topic/CSliderCtrl::SetPos.md)|设置滑块的当前位置。|  
|[CSliderCtrl::SetRange](../Topic/CSliderCtrl::SetRange.md)|设置滑块的最小和最大位置。|  
|[CSliderCtrl::SetRangeMax](../Topic/CSliderCtrl::SetRangeMax.md)|设置滑块的最大位置。|  
|[CSliderCtrl::SetRangeMin](../Topic/CSliderCtrl::SetRangeMin.md)|设置滑块的最小的位置。|  
|[CSliderCtrl::SetSelection](../Topic/CSliderCtrl::SetSelection.md)|将当前选择的大小。|  
|[CSliderCtrl::SetThumbLength](../Topic/CSliderCtrl::SetThumbLength.md)|设置滑块的长度在当前trackbar控件的。|  
|[CSliderCtrl::SetTic](../Topic/CSliderCtrl::SetTic.md)|设置指定的刻度线的位置。|  
|[CSliderCtrl::SetTicFreq](../Topic/CSliderCtrl::SetTicFreq.md)|设置刻度线频率每个滑块控件递增。|  
|[CSliderCtrl::SetTipSide](../Topic/CSliderCtrl::SetTipSide.md)|确定一个trackbar控件使用的工具提示控件。|  
|[CSliderCtrl::SetToolTips](../Topic/CSliderCtrl::SetToolTips.md)|分配工具提示控件添加到滑块控件。|  
  
## 备注  
 “滑块控件” \(也称为trackbar\)是包含滑块和选项刻度线的窗口。  当用户移动滑块时，使用鼠标或方向键，控件发送通知消息指示更改。  
  
 当您希望用户选择离散值或设置在范围时，将会触发的滑块控件很有用。  例如，可以使用滑块控件允许用户通过移动滑块设置键盘重复速率移动到特定刻度线。  
  
 此控件\(并 `CSliderCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 滑块移动到指定的增量您在创建它。  例如，因此，如果指定滑块应具有一个范围的五个滑块，只能占据六个位置:在滑块控件的左侧的一个位置和每个增量中的位置在范围内。  通常，这些位置中的每一个由刻度线确定的。  
  
 您创建一个滑块通过使用构造函数和 `CSliderCtrl`的 **Create** 成员函数。  一旦创建了一个滑块控件，可以在 `CSliderCtrl` 可使用成员函数更改其许多属性。  更改可以创建包含一组滑块的最小和最大位置，绘制刻度线，将选择大小和重新定位滑块。  
  
 有关使用 `CSliderCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [MFC示例CMNCTRL2](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl Class](../../mfc/reference/cprogressctrl-class.md)