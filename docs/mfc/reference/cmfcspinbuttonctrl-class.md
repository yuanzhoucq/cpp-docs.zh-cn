---
title: "CMFCSpinButtonCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCSpinButtonCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCSpinButtonCtrl class"
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CMFCSpinButtonCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCSpinButtonCtrl` 选件类支持绘制旋转按钮控件的可视管理器。  
  
## 语法  
  
```  
class CMFCSpinButtonCtrl : public CSpinButtonCtrl  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|默认构造函数。|  
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCSpinButtonCtrl::OnDraw](../Topic/CMFCSpinButtonCtrl::OnDraw.md)|重绘当前旋转按钮控件。|  
  
## 备注  
 若要使用可视管理器绘制旋转按钮控件在您的应用程序，请 `CMFCSpinButtonCtrl` 选件类替换为 `CSpinButtonCtrl` 选件类的所有实例。  
  
## 示例  
 下面的示例演示如何创建 `CMFCSpinButtonCtrl` 选件类的对象并使用其 `Create` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/CPP/cmfcspinbuttonctrl-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## 要求  
 **标头:** afxspinbuttonctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)