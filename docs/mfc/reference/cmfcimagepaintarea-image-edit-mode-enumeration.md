---
title: "CMFCImagePaintArea::IMAGE_EDIT_MODE 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IMAGE_EDIT_MODE Enumeration"
  - "CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration"
  - "CMFCImagePaintArea.IMAGE_EDIT_MODE Enumeration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IMAGE_EDIT_MODE 枚举方法"
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCImagePaintArea::IMAGE_EDIT_MODE 枚举
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定用于修改在图像编辑器"对话框中的图像绘制的模式。  
  
## 语法  
  
```  
enum IMAGE_EDIT_MODE  
{  
   IMAGE_EDIT_MODE_PEN = 0,  
   IMAGE_EDIT_MODE_FILL,  
   IMAGE_EDIT_MODE_LINE,  
   IMAGE_EDIT_MODE_RECT,  
   IMAGE_EDIT_MODE_ELLIPSE,  
   IMAGE_EDIT_MODE_COLOR  
};  
```  
  
## 成员  
  
|||  
|-|-|  
|Name|说明|  
|`IMAGE_EDIT_MODE_PEN`|用于绘制的各个像素。|  
|`IMAGE_EDIT_MODE_FILL`|用于填充在当前的光标位置将包含所有连续区域的颜色。|  
|`IMAGE_EDIT_MODE_LINE`|用于绘制线条。|  
|`IMAGE_EDIT_MODE_RECT`|用于绘制矩形。|  
|`IMAGE_EDIT_MODE_ELLIPSE`|用于绘制椭圆。|  
|`IMAGE_EDIT_MODE_COLOR`|用于将当前颜色到颜色在当前的光标位置。|  
  
### 备注  
 `CMFCImagePaintArea` 和 `CMFCImageEditorDialog` 类使用该枚举设置当前绘图模式。  绘图模式和当前颜色用于修改对话框编辑器在图像的图形区域。  有关 `CMFCImagePaintArea` 和 `CMFCImageEditorDialog` 的详细信息，请参阅 [CMFCImagePaintArea Class](../../mfc/reference/cmfcimagepaintarea-class.md) 和 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)。  
  
 如果选择从图像的颜色使用模式绘制 `IMAGE_EDIT_MODE_COLOR` 时，框架将当前绘图模式设置为 `IMAGE_EDIT_MODE_PEN`。  
  
## 要求  
 **页眉：** afximagepaintarea.h  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCImagePaintArea Class](../../mfc/reference/cmfcimagepaintarea-class.md)   
 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)