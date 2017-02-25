---
title: "CMFCPropertyGridToolTipCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyGridToolTipCtrl::PreTranslateMessage"
  - "~CMFCPropertyGridToolTipCtrl"
  - "PreTranslateMessage"
  - "CMFCPropertyGridToolTipCtrl.~CMFCPropertyGridToolTipCtrl"
  - "CMFCPropertyGridToolTipCtrl"
  - "CMFCPropertyGridToolTipCtrl.PreTranslateMessage"
  - "CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCPropertyGridToolTipCtrl destructor"
  - "CMFCPropertyGridToolTipCtrl class"
  - "CMFCPropertyGridToolTipCtrl class, 析构函数"
  - "PreTranslateMessage method"
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CMFCPropertyGridToolTipCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md) 使用显示工具提示的工具提示控件。  
  
## 语法  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](../Topic/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl.md)|构造 `CMFCPropertyGridToolTipCtrl` 对象。|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCPropertyGridToolTipCtrl::Create](../Topic/CMFCPropertyGridToolTipCtrl::Create.md)|创建工具提示控件的窗口。|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](../Topic/CMFCPropertyGridToolTipCtrl::Deactivate.md)|停用和隐藏工具提示控件。|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](../Topic/CMFCPropertyGridToolTipCtrl::GetLastRect.md)|返回工具提示控件的最后位置的坐标。|  
|[CMFCPropertyGridToolTipCtrl::Hide](../Topic/CMFCPropertyGridToolTipCtrl::Hide.md)|隐藏工具提示控件。|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|用于使选件类 [CWinApp](../../mfc/reference/cwinapp-class.md) 转换窗口消息，并在调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前。  （重写 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。）|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](../Topic/CMFCPropertyGridToolTipCtrl::SetTextMargin.md)|将工具提示文本和工具提示窗口的边框之间的间隔。|  
|[CMFCPropertyGridToolTipCtrl::Track](../Topic/CMFCPropertyGridToolTipCtrl::Track.md)|显示工具提示控件。|  
  
## 备注  
 当指针停留属性名称时，工具提示中。  [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) 选件类显示工具提示，以便仅由用户轻松可读的。  通常，工具提示的位置取决于指针的位置。  通过使用此选件类，工具提示显示在属性名称和类似于自然属性扩展，因此，属性名称完全可见。  
  
 MFC在 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)自动创建此控件并使用它。  
  
## 示例  
 下面的示例演示如何构造对象 `CMFCPropertyGridToolTipCtrl` 选件类以及如何显示工具提示控件。  
  
 [!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/CPP/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## 要求  
 **标头:** afxpropertygridtooltipctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)