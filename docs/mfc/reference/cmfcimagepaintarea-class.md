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
ms.openlocfilehash: 4e73bd7bc1a28317dbfc452df1f45541dfcbfd21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374436"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea 类

提供用于修改图像编辑器对话框中图像的图片区域。

## <a name="syntax"></a>语法

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|[CMFC图像绘制区域：CMFC图像绘制区域](#cmfcimagepaintarea)|构造 `CMFCImagePaintArea` 对象。|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFC图像绘制区域：获取模式](#getmode)|检索当前绘图模式。|
|[CMFC图像绘制区域：：设置位图](#setbitmap)|设置图片区域的位图图像。|
|[CMFC图像绘制区域：设置颜色](#setcolor)|设置当前绘图颜色。|
|[CMFC图像绘制区域：设置模式](#setmode)|设置当前绘图模式。|

### <a name="remarks"></a>备注

此类不适于在您的代码中直接使用。

框架使用此类在图像编辑器对话框中显示图片区域。 有关图像编辑器对话框的详细信息，请参阅[CMFCImage 编辑器对话类](../../mfc/reference/cmfcimageeditordialog-class.md)。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCImagePaintArea`类的对象、设置当前绘图颜色、设置当前绘图模式以及设置图片区域的位图图像。

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFC图像绘制区域](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>要求

**标题：** afximagepaint 区域.h

## <a name="cmfcimagepaintareacmfcimagepaintarea"></a><a name="cmfcimagepaintarea"></a>CMFC图像绘制区域：CMFC图像绘制区域

构造 `CMFCImagePaintArea` 对象。

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*p 家长Dlg*|[在]指向作为图像编辑器父级的对话框的指针。|

## <a name="cmfcimagepaintareagetmode"></a><a name="getmode"></a>CMFC图像绘制区域：获取模式

检索当前绘图模式。

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>返回值

指定当前绘图模式[的IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值。

## <a name="cmfcimagepaintareasetbitmap"></a><a name="setbitmap"></a>CMFC图像绘制区域：：设置位图

设置图片区域的位图图像。

```
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pBitmap*|[在]要显示的新位图图像。|

### <a name="remarks"></a>备注

如果*pBitmap*为 NULL，则此方法将可修改的绘制区域的大小设置为零。 否则，它将可修改的绘制区域的大小设置为提供的位图图像的大小。

## <a name="cmfcimagepaintareasetcolor"></a><a name="setcolor"></a>CMFC图像绘制区域：设置颜色

设置当前绘图颜色。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*颜色*|[在]新的绘图颜色。|

### <a name="remarks"></a>备注

当您从图像编辑器调色板栏或颜色选取器中选择颜色时，框架将调用此方法以更新当前绘图颜色。 初始绘图颜色为黑色（COLORREF 值为 0）。

除IMAGE_EDIT_MODE_COLOR外，图像编辑器对话框对所有绘图模式都使用绘图颜色。 有关绘图模式的详细信息，请参阅[CMFCImagePaint 区域：：IMAGE_EDIT_MODE枚举](cmfcimagepaintarea-image-edit-mode-enumeration.md)。

## <a name="cmfcimagepaintareasetmode"></a><a name="setmode"></a>CMFC图像绘制区域：设置模式

设置当前绘图模式。

```
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*模式*|[在]指定当前绘图模式[的IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值。|

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)
