---
title: "CMFCRibbonSlider Class | Microsoft Docs"
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
  - "CMFCRibbonSlider"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonSlider class"
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
caps.latest.revision: 43
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonSlider Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonSlider` 选件类实现可以添加到功能区栏或功能区状态栏的滑块控件。  功能区滑块控件类似于出现在Office 2007应用程序的缩放滑块。  
  
## 语法  
  
```  
class CMFCRibbonSlider : public CMFCRibbonBaseElement  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonSlider::CMFCRibbonSlider](../Topic/CMFCRibbonSlider::CMFCRibbonSlider.md)|构造和初始化功能区滑块控件。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonSlider::GetPos](../Topic/CMFCRibbonSlider::GetPos.md)|返回滑块控件的当前位置。|  
|[CMFCRibbonSlider::GetRangeMax](../Topic/CMFCRibbonSlider::GetRangeMax.md)|返回滑块的最大值。|  
|[CMFCRibbonSlider::GetRangeMin](../Topic/CMFCRibbonSlider::GetRangeMin.md)|返回滑块的最小值。|  
|[CMFCRibbonSlider::GetRegularSize](../Topic/CMFCRibbonSlider::GetRegularSize.md)|返回功能区元素的常规大小。  （重写 [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)。）|  
|[CMFCRibbonSlider::GetZoomIncrement](../Topic/CMFCRibbonSlider::GetZoomIncrement.md)|返回缩放增加的大小滑块控件的。|  
|[CMFCRibbonSlider::HasZoomButtons](../Topic/CMFCRibbonSlider::HasZoomButtons.md)|指定滑块是否具有缩放按钮。|  
|[CMFCRibbonSlider::OnDraw](../Topic/CMFCRibbonSlider::OnDraw.md)|调用由框架绘制功能区元素。  （重写 [CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)。）|  
|[CMFCRibbonSlider::SetPos](../Topic/CMFCRibbonSlider::SetPos.md)|设置滑块控件的当前位置。|  
|[CMFCRibbonSlider::SetRange](../Topic/CMFCRibbonSlider::SetRange.md)|通过设置最小值和最大值指定滑块控件的大小。|  
|[CMFCRibbonSlider::SetZoomButtons](../Topic/CMFCRibbonSlider::SetZoomButtons.md)|显示或隐藏缩放按钮。|  
|[CMFCRibbonSlider::SetZoomIncrement](../Topic/CMFCRibbonSlider::SetZoomIncrement.md)|设置缩放增加的大小滑块控件的。|  
  
## 备注  
 可以使用 `SetRange` 方案配置缩放增加的大小滑块的。  使用 `SetPos` 方法，可以设置滑块的当前位置。  
  
 使用 `SetZoomButtons` 方法，可以显示在滑块控件的左右两侧均循环的缩放按钮。  默认情况下，滑块是水平的，左缩放按钮显示一个减号，并正确的缩放按钮显示加号。  
  
 当用户单击按钮时，缩放 `SetZoomIncrement` 方法定义增量添加或从当前位置减去。  
  
## 示例  
 下面的示例在 `CMFCRibbonSlider` 选件类演示如何使用各种方法设置滑块的属性。  此示例演示如何构造 `CMFCRibbonSlider` 对象，显示缩放按钮，将滑块控件的当前位置，并将值的范围滑块控件的。  
  
 [!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/CPP/cmfcribbonslider-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)  
  
## 要求  
 **标头:** afxribbonslider.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)