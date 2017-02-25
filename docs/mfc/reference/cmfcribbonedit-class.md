---
title: "CMFCRibbonEdit Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonEdit class"
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CMFCRibbonEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现位于功能区栏的编辑控件。  
  
## 语法  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](../Topic/CMFCRibbonEdit::CMFCRibbonEdit.md)|构造 `CMFCRibbonEdit` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonEdit::CanBeStretched](../Topic/CMFCRibbonEdit::CanBeStretched.md)|指示 `CMFCRibbonEdit` 控件的高度是否可以垂直添加到功能区行的高度。|  
|[CMFCRibbonEdit::CMFCRibbonEdit](../Topic/CMFCRibbonEdit::CMFCRibbonEdit.md)|构造 `CMFCRibbonEdit` 对象。|  
|[CMFCRibbonEdit::CopyFrom](../Topic/CMFCRibbonEdit::CopyFrom.md)|复制指定的 `CMFCRibbonEdit` 对象的状态为当前 `CMFCRibbonEdit` 对象的。|  
|[CMFCRibbonEdit::CreateEdit](../Topic/CMFCRibbonEdit::CreateEdit.md)|创建 `CMFCRibbonEdit` 对象的新文本框。|  
|[CMFCRibbonEdit::DestroyCtrl](../Topic/CMFCRibbonEdit::DestroyCtrl.md)|销毁 `CMFCRibbonEdit` 对象。|  
|[CMFCRibbonEdit::DropDownList](../Topic/CMFCRibbonEdit::DropDownList.md)|删除拉列表框。|  
|[CMFCRibbonEdit::EnableSpinButtons](../Topic/CMFCRibbonEdit::EnableSpinButtons.md)|启用和设置旋转按钮的大小文本框。|  
|[CMFCRibbonEdit::GetCompactSize](../Topic/CMFCRibbonEdit::GetCompactSize.md)|检索 `CFMCRibbonEdit` 对象的袖珍型。|  
|[CMFCRibbonEdit::GetEditText](../Topic/CMFCRibbonEdit::GetEditText.md)|检索在文本框中的文本。|  
|[CMFCRibbonEdit::GetIntermediateSize](../Topic/CMFCRibbonEdit::GetIntermediateSize.md)|检索 `CMFCRibbonEdit` 对象的中间范围。|  
|[CMFCRibbonEdit::GetTextAlign](../Topic/CMFCRibbonEdit::GetTextAlign.md)|检索文本对齐方式在文本框中。|  
|[CMFCRibbonEdit::GetWidth](../Topic/CMFCRibbonEdit::GetWidth.md)|检索宽度，以像素，`CMFCRibbonEdit` 控件。|  
|[CMFCRibbonEdit::HasCompactMode](../Topic/CMFCRibbonEdit::HasCompactMode.md)|指示 `CMFCRibbonEdit` 控件显示范围是否可以是精简的。|  
|[CMFCRibbonEdit::HasFocus](../Topic/CMFCRibbonEdit::HasFocus.md)|指示 `CMFCRIbbonEdit` 控件是否具有焦点。|  
|[CMFCRibbonEdit::HasLargeMode](../Topic/CMFCRibbonEdit::HasLargeMode.md)|指示 `CMFCRibbonEdit` 控件显示范围是否可以用。|  
|[CMFCRibbonEdit::HasSpinButtons](../Topic/CMFCRibbonEdit::HasSpinButtons.md)|指示文本框是否具有旋转按钮。|  
|[CMFCRibbonEdit::IsHighlighted](../Topic/CMFCRibbonEdit::IsHighlighted.md)|指示 `CMFCRibbonEdit` 控件是否显示。|  
|[CMFCRibbonEdit::OnAfterChangeRect](../Topic/CMFCRibbonEdit::OnAfterChangeRect.md)|调用由框架，同时显示矩形的尺寸 `CMFCRibbonEdit` 控件中的。|  
|[CMFCRibbonEdit::OnDraw](../Topic/CMFCRibbonEdit::OnDraw.md)|调用由框架绘制 `CMFCRibbonEdit` 控件。|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](../Topic/CMFCRibbonEdit::OnDrawLabelAndImage.md)|调用由框架绘制标签和图像 `CMFCRibbonEdit` 控件的。|  
|[CMFCRibbonEdit::OnDrawOnList](../Topic/CMFCRibbonEdit::OnDrawOnList.md)|调用由框架绘制的 `CMFCRibbonEdit` 控件命令列表框。|  
|[CMFCRibbonEdit::OnEnable](../Topic/CMFCRibbonEdit::OnEnable.md)|调用由框架启用或禁用 `CMFCRibbonEdit` 控件。|  
|[CMFCRibbonEdit::OnHighlight](../Topic/CMFCRibbonEdit::OnHighlight.md)|调用由结构，当指针进入或离开 `CMFCRibbonEdit` 控件的区域。|  
|[CMFCRibbonEdit::OnKey](../Topic/CMFCRibbonEdit::OnKey.md)|调用由框架，当用户按下时keytip和 `CMFCRibbonEdit` 个控件具有焦点。|  
|[CMFCRibbonEdit::OnLButtonDown](../Topic/CMFCRibbonEdit::OnLButtonDown.md)|调用由框架更新 `CMFCRibbonEdit` 控件，当用户在某个控件的鼠标左键。|  
|[CMFCRibbonEdit::OnLButtonUp](../Topic/CMFCRibbonEdit::OnLButtonUp.md)|调用由结构，当用户松开鼠标左键。|  
|[CMFCRibbonEdit::OnRTLChanged](../Topic/CMFCRibbonEdit::OnRTLChanged.md)|调用由框架更新 `CMFCRibbonEdit` 控件，当该布局更改方向。|  
|[CMFCRibbonEdit::OnShow](../Topic/CMFCRibbonEdit::OnShow.md)|调用由结构显示或隐藏 `CMFCRibbonEdit` 控件。|  
|[CMFCRibbonEdit::Redraw](../Topic/CMFCRibbonEdit::Redraw.md)|更新 `CMFCRibbonEdit` 控件的显示。|  
|[CMFCRibbonEdit::SetACCData](../Topic/CMFCRibbonEdit::SetACCData.md)|用户可以设置数据。`CMFCRibbonEdit` 对象。|  
|[CMFCRibbonEdit::SetEditText](../Topic/CMFCRibbonEdit::SetEditText.md)|设置在文本框中的文本。|  
|[CMFCRibbonEdit::SetTextAlign](../Topic/CMFCRibbonEdit::SetTextAlign.md)|设置文本框中的文本对齐方式。|  
|[CMFCRibbonEdit::SetWidth](../Topic/CMFCRibbonEdit::SetWidth.md)|设置文本框的宽度 `CMFCRibbonEdit` 控件的。|  
  
## 备注  
  
## 示例  
 下面的示例演示如何构造 `CMFCRibbonEdit` 对象，在编辑控件旁显示旋转按钮，并将编辑控件的文本。  此代码段是 [MS办公室2007中演示的示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/CPP/cmfcribbonedit-class_1.cpp)]  
  
## 要求  
 **标头:** afxRibbonEdit.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)