---
title: CMFCCaption按钮类
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
ms.openlocfilehash: fb47e4373bf53e66dd4af17c89fe2f761858fbfd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367757"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaption按钮类

类`CMFCCaptionButton`实现一个按钮，该按钮显示在停靠窗格或微型框架窗口的标题栏上。 通常，框架会自动创建标题按钮。

## <a name="syntax"></a>语法

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|名称|说明|
|----------|-----------------|
|[CMFCCaption按钮：CMFCCaption按钮](#cmfccaptionbutton)|构造 CMFCCaptionButton 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCCaption按钮：获取Hit](#gethit)|返回由按钮表示的命令。|
|[CMFCCaption按钮：：GetIconID](#geticonid)|返回与按钮关联的图像 ID。|
|[CMFCCaption按钮：：获取 Rect](#getrect)|返回按钮占用的矩形。|
|[CMFCCaption按钮：获取大小](#getsize)|返回按钮的宽度和高度。|
|[CMFC标题按钮：：IsMini框架按钮](#isminiframebutton)|指示标题栏高度是否设置为迷你大小。|
|[CMFCCaption按钮：移动](#move)|设置按钮绘制位置和窗口显示状态。|
|[CMFCCaption按钮：在画上](#ondraw)|绘制标题按钮。|
|[CMFCCaption按钮：：设置迷你框架按钮](#setminiframebutton)|设置标题栏的迷你大小。|

## <a name="remarks"></a>备注

可以从[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)派生类，并使用受保护的方法`AddButton`，向迷你框架窗口添加字幕按钮。

CPaneFrameWnd.h 为两种类型的字幕按钮定义命令 ID：

- AFX_CAPTION_BTN_PIN，当停靠窗格支持自动隐藏模式时，将显示一个引脚按钮。

- AFX_CAPTION_BTN_CLOSE，当窗格可以关闭或隐藏时，将显示"**关闭**"按钮。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCCaptionButton`对象并设置标题栏的迷你大小。

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>要求

**标题：** afxcaption按钮.h

## <a name="cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a>CMFCCaption按钮：CMFCCaption按钮

构造 `CMFCCaptionButton` 对象。

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>参数

*nHit*<br/>
[在]与按钮关联的命令。

*b 左对齐*<br/>
[在]指定按钮是否向左对齐。

下表列出了*nHit*参数的可能值。

|“值”|Command|
|-----------|-------------|
|AFX_HTCLOSE|关闭按钮。|
|HTMINBUTTON|最小化按钮。|
|HTMAX按钮|最大化按钮。|
|AFX_HTLEFTBUTTON|左箭头按钮。|
|AFX_HTRIGHTBUTTON|右箭头按钮。|
|AFX_HTMENU|向下箭头菜单按钮。|
|HTNOWHERE|默认值;不表示任何命令。|

### <a name="remarks"></a>备注

默认情况下，标题按钮不与命令关联。

标题按钮在右侧或左侧对齐。

## <a name="cmfccaptionbuttongethit"></a><a name="gethit"></a>CMFCCaption按钮：获取Hit

返回由按钮表示的命令。

```
UINT GetHit() const;
```

### <a name="return-value"></a>返回值

按钮表示的命令。

下表列出了可能的返回值。

|“值”|Command|
|-----------|-------------|
|AFX_HTCLOSE|关闭按钮。|
|HTMINBUTTON|最小化按钮。|
|HTMAX按钮|最大化按钮。|
|AFX_HTLEFTBUTTON|左箭头按钮。|
|AFX_HTRIGHTBUTTON|右箭头按钮。|
|AFX_HTMENU|向下箭头菜单按钮。|
|HTNOWHERE|默认值;不表示任何命令。|

## <a name="cmfccaptionbuttongeticonid"></a><a name="geticonid"></a>CMFCCaption按钮：：GetIconID

返回与按钮关联的图像 ID。

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>参数

*布霍兹*<br/>
[在]左或右箭头图像指示为 TRUE;对于左侧或右侧箭头图像指示，用于向上或向下箭头图像指示。

*b 最大化*<br/>
[在]为最大化图像 ID 而实现 TRUE;用于最小化图像 ID 的 FALSE。

### <a name="return-value"></a>返回值

图像 ID。

### <a name="remarks"></a>备注

参数指定图像指示，以尽量减少或最大化字幕按钮。

## <a name="cmfccaptionbuttongetrect"></a><a name="getrect"></a>CMFCCaption按钮：：获取 Rect

返回按钮占用的矩形。

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>返回值

表示按钮位置的矩形。

### <a name="remarks"></a>备注

如果看不到该按钮，则返回的大小为 0。

## <a name="cmfccaptionbuttongetsize"></a><a name="getsize"></a>CMFCCaption按钮：获取大小

返回按钮的宽度和高度。

```
static CSize GetSize();
```

### <a name="return-value"></a>返回值

按钮的外部尺寸。

### <a name="remarks"></a>备注

返回的大小包括按钮边距和边框。

## <a name="cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a>CMFC标题按钮：：IsMini框架按钮

指示标题栏高度是否设置为迷你大小。

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>返回值

如果标题设置为最小大小，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfccaptionbuttonmove"></a><a name="move"></a>CMFCCaption按钮：移动

设置按钮绘制位置和窗口显示状态。

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>参数

*ptto*<br/>
[在]新位置。

*bHide*<br/>
[在]是否显示该按钮。

## <a name="cmfccaptionbuttonondraw"></a><a name="ondraw"></a>CMFCCaption按钮：在画上

绘制标题按钮。

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向按钮的设备上下文。

*b 活动*<br/>
[在]是否绘制活动按钮图像。

*布霍兹*<br/>
[在]保留用于派生类。

*b 最大化*<br/>
[在]是否绘制最大化按钮图像。

*b 残疾*<br/>
[在]是否绘制启用的按钮图像。

### <a name="remarks"></a>备注

当按钮为最大化或最小化按钮时，将使用*b 最大化*参数。

## <a name="cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a>CMFCCaption按钮：：设置迷你框架按钮

设置标题栏的迷你大小。

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>参数

*bSet*<br/>
[在]TRUE，适用于迷你标题栏高度;默认标题栏高度的 FALSE。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFramewnd 类](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
