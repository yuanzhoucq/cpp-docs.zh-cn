---
title: "Cmfcimagepaintarea:: Image_edit_mode 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IMAGE_EDIT_MODE Enumeration
dev_langs: C++
helpviewer_keywords: IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22e3b00bed830052c2abbc988152f4a14f1267ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE 枚举
指定用于修改图像编辑器对话框中的图像绘制模式。  
  
## <a name="syntax"></a>语法  
  
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
  
## <a name="members"></a>成员  
  
|||  
|-|-|  
|名称|描述|  
|`IMAGE_EDIT_MODE_PEN`|用于绘制单个像素。|  
|`IMAGE_EDIT_MODE_FILL`|用于填充所有的相邻区域包含当前光标位置处的颜色。|  
|`IMAGE_EDIT_MODE_LINE`|用于绘制线条。|  
|`IMAGE_EDIT_MODE_RECT`|用于绘制矩形。|  
|`IMAGE_EDIT_MODE_ELLIPSE`|用于绘制椭圆形。|  
|`IMAGE_EDIT_MODE_COLOR`|用于当前光标位置处的当前颜色设置为的颜色。|  
  
### <a name="remarks"></a>备注  
 `CMFCImagePaintArea`和`CMFCImageEditorDialog`类使用此枚举来设置的当前绘图模式。 绘制模式和当前颜色用于修改图像编辑器对话框中的图片区域。 有关详细信息`CMFCImagePaintArea`和`CMFCImageEditorDialog`，请参阅[CMFCImagePaintArea 类](../../mfc/reference/cmfcimagepaintarea-class.md)和[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)。  
  
 当你选择一种颜色从映像使用`IMAGE_EDIT_MODE_COLOR`绘图模式下，框架将当前绘图模式设置为`IMAGE_EDIT_MODE_PEN`。  
  
## <a name="requirements"></a>惠?  
 **标头：** afximagepaintarea.h  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCImagePaintArea 类](../../mfc/reference/cmfcimagepaintarea-class.md)   
 [CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)
