---
title: CMFCImagePaintArea 类
ms.date: 11/04/2016
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
ms.openlocfilehash: af1d485d6d6281e909e33176ee1ae2b736c76600
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641384"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea 类

提供用于修改图像编辑器对话框中的图像的图片区域。

## <a name="syntax"></a>语法

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|构造 `CMFCImagePaintArea` 对象。|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCImagePaintArea::GetMode](#getmode)|检索当前的绘制模式。|
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|设置图片区域的位图图像。|
|[CMFCImagePaintArea::SetColor](#setcolor)|设置当前绘图的颜色。|
|[CMFCImagePaintArea::SetMode](#setmode)|设置当前的绘制模式。|

### <a name="remarks"></a>备注

此类不适于在代码中直接使用。

该框架使用此类以在图像编辑器对话框中显示图片区域。 有关图像编辑器对话框的详细信息，请参阅[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)。

## <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCImagePaintArea`类中，设置当前绘图时的颜色，设置当前的绘制模式，并设置图片区域的位图图像。

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>要求

**标头：** afximagepaintarea.h

##  <a name="cmfcimagepaintarea"></a>  CMFCImagePaintArea::CMFCImagePaintArea

构造 `CMFCImagePaintArea` 对象。

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pParentDlg*|[in]指向是父级的图像编辑器对话框中的指针。|

##  <a name="getmode"></a>  CMFCImagePaintArea::GetMode

检索当前的绘制模式。

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>返回值

[IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值，该值指定当前的绘制模式。

##  <a name="setbitmap"></a>  CMFCImagePaintArea::SetBitmap

设置图片区域的位图图像。

```
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*pBitmap*|[in]要显示的新位图图像。|

### <a name="remarks"></a>备注

如果*pBitmap*为 NULL，此方法可修改绘制区域的大小设置为零。 否则，它将可修改绘制区域的大小设置为提供的位图图像的大小。

##  <a name="setcolor"></a>  CMFCImagePaintArea::SetColor

设置当前绘图的颜色。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*颜色*|[in]新的绘图颜色。|

### <a name="remarks"></a>备注

当从图像编辑器调色板栏中选择一种颜色或颜色选取器中，框架调用此方法来更新当前绘图的颜色。 初始绘图的颜色为黑色 （0 COLORREF 值）。

图像编辑器对话框中的所有绘图模式下，除了 IMAGE_EDIT_MODE_COLOR 使用绘图的颜色。 有关绘制模式的详细信息，请参阅[cmfcimagepaintarea:: Image_edit_mode 枚举](cmfcimagepaintarea-image-edit-mode-enumeration.md)。

##  <a name="setmode"></a>  CMFCImagePaintArea::SetMode

设置当前的绘制模式。

```
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*模式*|[in][IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值，该值指定当前的绘制模式。|

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)
