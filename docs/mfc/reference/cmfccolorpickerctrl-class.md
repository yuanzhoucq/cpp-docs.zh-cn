---
title: "CMFCColorPickerCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCColorPickerCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorPickerCtrl class"
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCColorPickerCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorPickerCtrl` 选件类提供用于选择颜色的控件的功能。  
  
## 语法  
  
```  
class CMFCColorPickerCtrl : public CButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](../Topic/CMFCColorPickerCtrl::CMFCColorPickerCtrl.md)|构造 `CMFCColorPickerCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorPickerCtrl::GetColor](../Topic/CMFCColorPickerCtrl::GetColor.md)|检索用户选择的颜色。|  
|[CMFCColorPickerCtrl::GetHLS](../Topic/CMFCColorPickerCtrl::GetHLS.md)|检索用户选定颜色的颜色、文件和该值。|  
|[CMFCColorPickerCtrl::GetHue](../Topic/CMFCColorPickerCtrl::GetHue.md)|检索用户选定颜色的颜色分量。|  
|[CMFCColorPickerCtrl::GetLuminance](../Topic/CMFCColorPickerCtrl::GetLuminance.md)|检索用户选定颜色的亮度元素。|  
|[CMFCColorPickerCtrl::GetSaturation](../Topic/CMFCColorPickerCtrl::GetSaturation.md)|检索用户选定颜色的该元素。|  
|[CMFCColorPickerCtrl::SelectCellHexagon](../Topic/CMFCColorPickerCtrl::SelectCellHexagon.md)|将当前颜色到指定的RGB颜色分量或指定的单元格十六进制定义的颜色。|  
|[CMFCColorPickerCtrl::SetColor](../Topic/CMFCColorPickerCtrl::SetColor.md)|将当前颜色到指定的RGB颜色值。|  
|[CMFCColorPickerCtrl::SetHLS](../Topic/CMFCColorPickerCtrl::SetHLS.md)|将当前颜色到指定的HLS颜色值。|  
|[CMFCColorPickerCtrl::SetHue](../Topic/CMFCColorPickerCtrl::SetHue.md)|更改当前选定的颜色的颜色分量。|  
|[CMFCColorPickerCtrl::SetLuminance](../Topic/CMFCColorPickerCtrl::SetLuminance.md)|更改当前选定的颜色的亮度元素。|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](../Topic/CMFCColorPickerCtrl::SetLuminanceBarWidth.md)|设置亮度栏的宽度在颜色选取器控件的。|  
|[CMFCColorPickerCtrl::SetOriginalColor](../Topic/CMFCColorPickerCtrl::SetOriginalColor.md)|设置最初选定的颜色。|  
|[CMFCColorPickerCtrl::SetPalette](../Topic/CMFCColorPickerCtrl::SetPalette.md)|设置当前调色板。|  
|[CMFCColorPickerCtrl::SetSaturation](../Topic/CMFCColorPickerCtrl::SetSaturation.md)|更改当前选定的颜色该元素。|  
|[CMFCColorPickerCtrl::SetType](../Topic/CMFCColorPickerCtrl::SetType.md)|设置颜色选取器控件的类型显示。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorPickerCtrl::DrawCursor](../Topic/CMFCColorPickerCtrl::DrawCursor.md)|调用由框架在指向选定的颜色的光标之前显示。|  
  
## 备注  
 标准颜色从一个六角调色板中选择，并且，自定义颜色从红色使用\/、\/蓝色表示法或颜色\/satuaration\/种表示法，指定颜色的亮度栏中选择。  
  
 下图演示几 `CMFCColorPickerCtrl` 对象。  
  
 ![CMFCColorPickerCtrl 对话框](../../mfc/reference/media/colorpicker.png "ColorPicker")  
  
 `CMFCColorPickerCtrl` 支持两对样式。  十六进制和HEX\_GREYSCALE样式为标准颜色选择合适。  选择器和亮度样式为自定义颜色选择合适。  
  
 执行以下步骤将 `CMFCColorPickerCtrl` 控件添加到对话框中:  
  
1.  如果使用 **类向导**，插入一个新按钮控件添加到对话框模板中\(因为 `CMFCColorPickerCtrl` 选件类从 `CButton` 选件类继承的）。  
  
2.  插入与新按钮控件添加到对话框选件类的成员变量。  然后从 `CButton` 请更改变量的类型。`CMFCColorPickerCtrl`。  
  
3.  插入对话框选件类的 `WM_INITDIALOG` 消息处理程序。  在处理程序中，设置类型、调色板和首字母 `CMFCColorPickerCtrl` 控件的选定的颜色。  
  
## 示例  
 通过在 `CMFCColorPickerCtrl` 选件类，中的各种方法下面的示例演示如何配置 `CMFCColorPickerCtrl` 对象。  示例演示如何设置选择器控件的类型以及如何设置其颜色、颜色、状态和饱和。  此示例是 [新的控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/CPP/cmfccolorpickerctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/CPP/cmfccolorpickerctrl-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)  
  
## 要求  
 **标头:** afxcolorpickerctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md)