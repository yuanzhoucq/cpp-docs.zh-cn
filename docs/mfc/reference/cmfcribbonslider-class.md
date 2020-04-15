---
title: CMFC 剪杆级
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
ms.openlocfilehash: f2a05ca1433ca3a44b0459360e3f09fe7a274c68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368837"
---
# <a name="cmfcribbonslider-class"></a>CMFC 剪杆级

类`CMFCRibbonSlider`实现一个滑块控件，您可以将该控件添加到功能区栏或功能区状态栏中。 功能区滑块控件类似于显示在 Office 2007 应用程序中的缩放滑块。

## <a name="syntax"></a>语法

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC剪彩滑块：CMFC剪彩滑块](#cmfcribbonslider)|构造和初始化功能区滑块控件。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC剪杆：GetPos](#getpos)|返回滑块控件的当前位置。|
|[CMFC剪彩滑块：获取山脉最大值](#getrangemax)|返回滑块的最大值。|
|[CMFC剪彩者：获取兰格明](#getrangemin)|返回滑块的最小值。|
|[CMFC 功能滑块：获取常规大小](#getregularsize)|返回功能区元素的常规大小。 （覆盖[CMFC 功能基础元素：获取常规大小](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).）|
|[CMFC 功能滑块：：获取放大增量](#getzoomincrement)|返回滑块控件的缩放增量大小。|
|[CMFC 功能滑块：：有缩放按钮](#haszoombuttons)|指定滑块是否具有缩放按钮。|
|[CMFC剪彩器：在画上](#ondraw)|由框架调用以绘制功能区元素。 （覆盖[CMFC 功能基础元素：onDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).）|
|[CMFC 剪杆：：设置Pos](#setpos)|设置滑块控件的当前位置。|
|[CMFC 剪杆滑块：：设置范围](#setrange)|通过设置最小值和最大值来指定滑块控件的范围。|
|[CMFC 功能滑块：：设置缩放按钮](#setzoombuttons)|显示或隐藏缩放按钮。|
|[CMFC 功能滑块：：设置放大增量](#setzoomincrement)|设置滑块控件的缩放增量大小。|

## <a name="remarks"></a>备注

可以使用 方法`SetRange`配置滑块的缩放增量范围。 您可以使用`SetPos`方法设置滑块的当前位置。

您可以使用`SetZoomButtons`方法在滑块控件的左侧和右侧显示圆形缩放按钮。 默认情况下，滑块是水平的，左侧缩放按钮显示减号，右侧缩放按钮显示加号。

该方法`SetZoomIncrement`定义在用户单击缩放按钮时要添加到或从当前位置减去的增量。

## <a name="example"></a>示例

下面的示例演示如何在`CMFCRibbonSlider`类中使用各种方法来设置滑块的属性。 该示例演示如何构造`CMFCRibbonSlider`对象、显示缩放按钮、设置滑块控件的当前位置以及设置滑块控件的值范围。

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>要求

**标题：** afxribbon 滑块.h

## <a name="cmfcribbonslidercmfcribbonslider"></a><a name="cmfcribbonslider"></a>CMFC剪彩滑块：CMFC剪彩滑块

构造功能区滑块。

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]滑块 ID。

[在]。 *n 宽度*滑块宽度（以像素为单位）。

### <a name="remarks"></a>备注

构造在添加滑块的面板类别中为*nWidth*像素宽的功能区滑块。 默认情况下，滑块是水平的。

## <a name="cmfcribbonslidergetpos"></a><a name="getpos"></a>CMFC剪杆：GetPos

返回滑块控件的当前位置。

```
int GetPos() const;
```

### <a name="return-value"></a>返回值

滑块控件的当前位置，该位置相对于滑块的开头。

## <a name="cmfcribbonslidergetrangemax"></a><a name="getrangemax"></a>CMFC剪彩滑块：获取山脉最大值

获取滑块可以在滑块控件上移动的最大增量。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>返回值

滑块可以在滑块控件上移动的滑块的最大增量。

## <a name="cmfcribbonslidergetrangemin"></a><a name="getrangemin"></a>CMFC剪彩者：获取兰格明

返回滑块在滑块控件上可以移动的最小增量。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>返回值

滑块在滑块控件上可以移动的最小增量。

## <a name="cmfcribbonslidergetregularsize"></a><a name="getregularsize"></a>CMFC 功能滑块：获取常规大小

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonslidergetzoomincrement"></a><a name="getzoomincrement"></a>CMFC 功能滑块：：获取放大增量

获取滑块控件的缩放增量。

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>返回值

滑块控件的缩放增量。

## <a name="cmfcribbonsliderhaszoombuttons"></a><a name="haszoombuttons"></a>CMFC 功能滑块：：有缩放按钮

指定滑块是否具有缩放按钮。

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>返回值

如果滑块具有缩放按钮，则为 TRUE;否则。

## <a name="cmfcribbonsliderondraw"></a><a name="ondraw"></a>CMFC剪彩器：在画上

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcribbonslidersetpos"></a><a name="setpos"></a>CMFC 剪杆：：设置Pos

设置滑块控件的当前位置。

```
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>参数

*nPos*<br/>
[在]指定要为滑块设置的位置。 该位置相对于滑块的开头。

*bredraw*<br/>
[在]如果为 TRUE，则滑块将重新绘制。

## <a name="cmfcribbonslidersetrange"></a><a name="setrange"></a>CMFC 剪杆滑块：：设置范围

设置滑块控件的值范围。

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>参数

*nMin*<br/>
[在]指定滑块控件的最小值。

*nMax*<br/>
[在]指定滑块控件的最大值。

### <a name="remarks"></a>备注

通过设置最小值和最大值来指定滑块控件的值范围。

## <a name="cmfcribbonslidersetzoombuttons"></a><a name="setzoombuttons"></a>CMFC 功能滑块：：设置缩放按钮

显示或隐藏缩放按钮。

```
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>参数

[在]。 *bSet*TRUE 以显示缩放按钮;假隐藏它们。

## <a name="cmfcribbonslidersetzoomincrement"></a><a name="setzoomincrement"></a>CMFC 功能滑块：：设置放大增量

设置滑块控件的缩放增量。

```
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>参数

*nZoom 增量*<br/>
[在]指定滑块控件的缩放增量。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)
