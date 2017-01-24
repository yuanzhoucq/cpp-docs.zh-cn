---
title: "CProgressCtrl Class | Microsoft Docs"
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
  - "CProgressCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CProgressCtrl class"
  - "Internet Explorer 4.0 common controls"
  - "progress controls [C++], CProgressCtrl class"
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CProgressCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常见进度栏控件的功能。  
  
## 语法  
  
```  
class CProgressCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CProgressCtrl::CProgressCtrl](../Topic/CProgressCtrl::CProgressCtrl.md)|构造 `CProgressCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CProgressCtrl::Create](../Topic/CProgressCtrl::Create.md)|创建一个进度栏控件并将它附加到 `CProgressCtrl` 对象。|  
|[CProgressCtrl::CreateEx](../Topic/CProgressCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个进度并将它附加到 `CProgressCtrl` 对象。|  
|[CProgressCtrl::GetBarColor](../Topic/CProgressCtrl::GetBarColor.md)|获取显示进度栏的颜色当前进度栏控件的。|  
|[CProgressCtrl::GetBkColor](../Topic/CProgressCtrl::GetBkColor.md)|获取当前进度栏的背景色。|  
|[CProgressCtrl::GetPos](../Topic/CProgressCtrl::GetPos.md)|获取进度栏的当前位置。|  
|[CProgressCtrl::GetRange](../Topic/CProgressCtrl::GetRange.md)|获取进度栏控件大小的下限和上限。|  
|[CProgressCtrl::GetState](../Topic/CProgressCtrl::GetState.md)|获取当前进度栏控件的状态。|  
|[CProgressCtrl::GetStep](../Topic/CProgressCtrl::GetStep.md)|检索当前进度栏控件的进度栏的步骤递增。|  
|[CProgressCtrl::OffsetPos](../Topic/CProgressCtrl::OffsetPos.md)|将一个指定的增量提升进度栏控件的当前位置并重画该线条反映新位置。|  
|[CProgressCtrl::SetBarColor](../Topic/CProgressCtrl::SetBarColor.md)|显示安装进度栏的颜色在当前进度栏控件的。|  
|[CProgressCtrl::SetBkColor](../Topic/CProgressCtrl::SetBkColor.md)|设置进度栏的背景色。|  
|[CProgressCtrl::SetMarquee](../Topic/CProgressCtrl::SetMarquee.md)|启用marquee模式打开或关闭为当前进度栏控件。|  
|[CProgressCtrl::SetPos](../Topic/CProgressCtrl::SetPos.md)|设置进度栏控件的当前位置并重画该线条反映新位置。|  
|[CProgressCtrl::SetRange](../Topic/CProgressCtrl::SetRange.md)|设置进度栏控件的最小和最大大小并重画该线条反映新的范围。|  
|[CProgressCtrl::SetState](../Topic/CProgressCtrl::SetState.md)|设置当前进度栏控件的状态。|  
|[CProgressCtrl::SetStep](../Topic/CProgressCtrl::SetStep.md)|对于进度栏控件指定步骤递增。|  
|[CProgressCtrl::StepIt](../Topic/CProgressCtrl::StepIt.md)|通过一系列步骤增量提升进度栏控件的当前位置\(请参见 [SetStep](../Topic/CProgressCtrl::SetStep.md)\)并重画该线条反映新位置。|  
  
## 备注  
 进度栏控件是应用程序可以使用指示较长操作的进度的窗口。  它包括逐渐加载，从左向右的一个矩形，与系统突出显示颜色，当操作进行时  
  
 进度栏控件有大小和当前位置。  该范围表示操作的总时间限制，因此，当前位置表示应用程序取得在完成操作的进度。  窗口过程使用该大小和当前位置决定进度栏的百分比用突出显示颜色填充。  由于大小和当前位置值表示为有符号整数，当前位置值的范围是从2,147,483,648到2,147,483,647 –包含。  
  
 有关使用 `CProgressCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CProgressCtrl](../../mfc/using-cprogressctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CProgressCtrl`  
  
## 要求  
 **标头:** afxcmn.h  
  
## 请参阅  
 [MFC示例CMNCTRL2](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)