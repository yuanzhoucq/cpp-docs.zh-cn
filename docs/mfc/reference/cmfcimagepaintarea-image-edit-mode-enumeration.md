---
title: CMFCImagePaintArea::IMAGE_EDIT_MODE 枚举
ms.date: 11/04/2016
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
ms.openlocfilehash: 372a1df6500f4d7219c89d8f82425246c2236514
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272134"
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE 枚举

指定用于修改图像编辑器对话框中的图像的绘制模式。

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
|IMAGE_EDIT_MODE_PEN|用于绘制单个像素。|
|IMAGE_EDIT_MODE_FILL|用于填充所有包含当前光标位置处的颜色的相邻区域。|
|IMAGE_EDIT_MODE_LINE|用于绘制线条。|
|IMAGE_EDIT_MODE_RECT|用于绘制矩形。|
|IMAGE_EDIT_MODE_ELLIPSE|用于绘制一个椭圆。|
|IMAGE_EDIT_MODE_COLOR|用于当前光标位置处的颜色设置的当前颜色。|

### <a name="remarks"></a>备注

`CMFCImagePaintArea`和`CMFCImageEditorDialog`类使用此枚举来设置当前的绘制模式。 绘制模式和当前颜色用于修改图像编辑器对话框中的图片区域。 有关详细信息`CMFCImagePaintArea`并`CMFCImageEditorDialog`，请参阅[CMFCImagePaintArea 类](../../mfc/reference/cmfcimagepaintarea-class.md)并[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)。

当使用 IMAGE_EDIT_MODE_COLOR 绘制模式从映像选择一种颜色时，框架将当前绘图模式设置为 IMAGE_EDIT_MODE_PEN。

## <a name="requirements"></a>要求

**标头：** afximagepaintarea.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImagePaintArea 类](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)
