---
title: CMFCRibbonProgressBar 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
ms.openlocfilehash: b7cbddbd4fca8379562b762fadbb3d2bda44f166
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753531"
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar 类

实现用于直观指示较长操作进度的控件。

## <a name="syntax"></a>语法

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC 剪彩进度栏：CMFC 剪彩进度栏](#cmfcribbonprogressbar)|构造并初始化一个 `CMFCRibbonProgressBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC功能放大缩小字体功能 放大缩小字体功能](#getpos)|返回当前进度。|
|[CMFC功能进度栏：获取山脉最大值](#getrangemax)|返回当前范围的最大值。|
|[CMFC功能进展栏：获取兰格明](#getrangemin)|返回当前范围的最小值。|
|[CMFC 功能进度栏：获取常规大小](#getregularsize)|返回功能区元素的常规大小。 （覆盖[CMFC 功能基础元素：获取常规大小](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).）|
|[CMFC功能收集进度栏：：无限模式](#isinfinitemode)|指定进度条是否以无限模式工作。|
|[CMFC剪彩进度栏：在画上](#ondraw)|由框架调用以绘制功能区元素。 （覆盖[CMFC 功能基础元素：onDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).）|
|[CMFC 功能进度栏：：设置无限模式](#setinfinitemode)|将进度条设置在无限模式下工作。|
|[CMFC 功能进度栏：：设置Pos](#setpos)|设置当前进度。|
|[CMFC 功能进度栏：：设置范围](#setrange)|设置最小值和最大值。|

## <a name="remarks"></a>备注

A`CMFCRibbonProgressBar`可以在两种模式下运行：常规模式和无限模式。 在常规模式下，进度条从左到右填充，并在达到最大值时停止。 在无限模式下，进度条从最小值重复填充到最大值。 您可以使用无限模式来指示操作正在进行，但完成时间未知。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCRibbonProgressBar` 类中的各种方法。 该示例演示如何将进度条设置为以无限模式工作（操作的完成时间未知），设置进度条的最小值和最大值，并设置进度条的当前位置。 此代码段是 MS [Office 2007 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>要求

**标题：** afxRibbonProgressBar.h

## <a name="cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a>CMFC 剪彩进度栏：CMFC 剪彩进度栏

构造并初始化[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)对象。

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]指定功能区进度栏的命令 ID。

*n 宽度*<br/>
[在]指定功能区进度条的宽度（以像素为单位）。

*nHeight*<br/>
[在]指定功能区进度条的高度（以像素为单位）。

## <a name="cmfcribbonprogressbargetpos"></a><a name="getpos"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

返回进度条的当前位置。

```
int GetPos () const;
```

### <a name="return-value"></a>返回值

表示进度条的当前位置的值。

### <a name="remarks"></a>备注

正在设置的范围必须在[CMFCRibbonProgressBar 指定的范围内：：setRange](#setrange)方法。

## <a name="cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a>CMFC功能进度栏：获取山脉最大值

返回进度条的当前最大值。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>返回值

当前范围的最大值。

### <a name="remarks"></a>备注

## <a name="cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a>CMFC功能进展栏：获取兰格明

返回进度条的当前最小范围值。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>返回值

当前范围的最小值。

## <a name="cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a>CMFC 功能进度栏：获取常规大小

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a>CMFC功能收集进度栏：：无限模式

指定进度条是否以无限模式工作。

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>返回值

如果进度条处于无限模式，则为 TRUE;如果进度条处于无限模式。否则，FALSE。

### <a name="remarks"></a>备注

在无限模式下，进度条从最小值重复填充到最大值。 您可以使用无限模式来指示操作正在进行，但完成时间未知。

## <a name="cmfcribbonprogressbarondraw"></a><a name="ondraw"></a>CMFC剪彩进度栏：在画上

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a>CMFC 功能进度栏：：设置无限模式

将进度条设置在无限模式下工作。

```cpp
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>参数

*bSet*<br/>
[在]TRUE 指定进度条处于无限模式;否则，FALSE。

### <a name="remarks"></a>备注

通常，如果进度条处于无限模式，则告诉用户操作正在进行，但完成时间未知。 因此，进度条从最小值重复填充到最大值。

## <a name="cmfcribbonprogressbarsetpos"></a><a name="setpos"></a>CMFC 功能进度栏：：设置Pos

设置进度条的当前位置。

```cpp
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*nPos*<br/>
[在]指定将进度条设置为的位置。

*bredraw*<br/>
[在]指定是否应重绘进度条。

### <a name="remarks"></a>备注

正在设置的范围必须在[CMFCRibbonProgressBar 指定的范围内：：setRange](#setrange)方法。

## <a name="cmfcribbonprogressbarsetrange"></a><a name="setrange"></a>CMFC 功能进度栏：：设置范围

设置进度条的最小值和最大值。

```cpp
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>参数

*nMin*<br/>
[在]指定范围的最小值。

*nMax*<br/>
[在]指定范围的最大值。

### <a name="remarks"></a>备注

使用此方法通过设置最小值和最大值来定义进度条的范围。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFC剪条类](../../mfc/reference/cmfcribbonbar-class.md)
