---
title: "CSpinButtonCtrl Class | Microsoft Docs"
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
  - "CSpinButtonCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSpinButtonCtrl class"
  - "CSpinButtonCtrl class, 公共控件"
  - "数值调节钮控件"
  - "up-down 控件, 数值调节钮控件"
  - "Windows common controls [C++], CSpinButtonCtrl"
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSpinButtonCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常见旋转按钮控件的功能。  
  
## 语法  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](../Topic/CSpinButtonCtrl::CSpinButtonCtrl.md)|构造 `CSpinButtonCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSpinButtonCtrl::Create](../Topic/CSpinButtonCtrl::Create.md)|创建旋转按钮控件并将它附加到 `CSpinButtonCtrl` 对象。|  
|[CSpinButtonCtrl::CreateEx](../Topic/CSpinButtonCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建旋转按钮控件并将它附加到 `CSpinButtonCtrl` 对象。|  
|[CSpinButtonCtrl::GetAccel](../Topic/CSpinButtonCtrl::GetAccel.md)|检索旋转按钮控件的加速信息。|  
|[CSpinButtonCtrl::GetBase](../Topic/CSpinButtonCtrl::GetBase.md)|检索旋转按钮控件的当前基础。|  
|[CSpinButtonCtrl::GetBuddy](../Topic/CSpinButtonCtrl::GetBuddy.md)|检索指向当前合作者窗口。|  
|[CSpinButtonCtrl::GetPos](../Topic/CSpinButtonCtrl::GetPos.md)|检索旋转按钮控件的当前位置。|  
|[CSpinButtonCtrl::GetRange](../Topic/CSpinButtonCtrl::GetRange.md)|检索旋转按钮控件的上限和下限（大小）。|  
|[CSpinButtonCtrl::SetAccel](../Topic/CSpinButtonCtrl::SetAccel.md)|设置旋转按钮控件的加速。|  
|[CSpinButtonCtrl::SetBase](../Topic/CSpinButtonCtrl::SetBase.md)|设置旋转按钮控件的基础。|  
|[CSpinButtonCtrl::SetBuddy](../Topic/CSpinButtonCtrl::SetBuddy.md)|设置旋转按钮控件的合作者窗口。|  
|[CSpinButtonCtrl::SetPos](../Topic/CSpinButtonCtrl::SetPos.md)|设置控件的当前位置。|  
|[CSpinButtonCtrl::SetRange](../Topic/CSpinButtonCtrl::SetRange.md)|设置旋转按钮控件的上限和下限（大小）。|  
  
## 备注  
 “旋转按钮控件” \(也称为up\-down控件\)是中的箭头按钮对用户可以单击以递增或递减值，如显示的滚动位置或一个数字在该控件。  该值与旋转按钮控件调用其当前位置。  旋转按钮控件是最常用于该控件，称为“合作者窗口”。  
  
 此控件\(并 `CSpinButtonCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 对用户，则旋转按钮控件及其合作者窗口经常类似于单个控件。  可以指定旋转按钮控件在其合作者窗口旁自动确定自身，因此，它自动设置合作者窗口的标题为其当前位置。  可以使用旋转按钮控件来编辑控件数字提示用户输入。  
  
 单击箭头将当前位置沿最大，并且，单击箭头下移当前位置沿最小值方向。  默认情况下，最小为100，并且该最大值为0。  在最小权限均设置为中的最大值大于\(例如时间，那么，当使用默认设置\)时，请单击箭头以减少位置值，单击向下键增大。  
  
 没有合作者windows函数的旋转按钮控件作为一种简化的滚动条。  例如，选项卡控件有时显示旋转按钮控件使用户能够移动附加选项到视图。  
  
 有关使用 `CSpinButtonCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [MFC示例CMNCTRL2](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl Class](../../mfc/reference/csliderctrl-class.md)