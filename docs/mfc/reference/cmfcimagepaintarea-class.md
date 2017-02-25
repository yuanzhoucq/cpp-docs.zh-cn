---
title: "CMFCImagePaintArea Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCImagePaintArea"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCImagePaintArea class"
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CMFCImagePaintArea Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供可用于修改在图像编辑器对话框中的图像的图像区域。  
  
## 语法  
  
```  
class CMFCImagePaintArea : public CButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCImagePaintArea::CMFCImagePaintArea](../Topic/CMFCImagePaintArea::CMFCImagePaintArea.md)|构造 `CMFCImagePaintArea` 对象。|  
|`CMFCImagePaintArea::~CMFCImagePaintArea`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCImagePaintArea::GetMode](../Topic/CMFCImagePaintArea::GetMode.md)|检索当前绘图模式。|  
|[CMFCImagePaintArea::SetBitmap](../Topic/CMFCImagePaintArea::SetBitmap.md)|设置图像区域的位图图像。|  
|[CMFCImagePaintArea::SetColor](../Topic/CMFCImagePaintArea::SetColor.md)|设置当前绘制颜色。|  
|[CMFCImagePaintArea::SetMode](../Topic/CMFCImagePaintArea::SetMode.md)|设置当前绘图模式。|  
  
### 备注  
 此类不适于在您的代码中直接使用。  
  
 框架使用此选件类显示在图像编辑器对话框的图像区域。  有关图像编辑器对话框的更多信息，请参见 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)。  
  
## 示例  
 下面的示例演示如何构造对象 `CMFCImagePaintArea` 选件类，将当前绘制颜色，将当前绘图模式，并设置图像区域的位图图像。  
  
 [!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/CPP/cmfcimagepaintarea-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)  
  
## 要求  
 **标头:** afximagepaintarea.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)