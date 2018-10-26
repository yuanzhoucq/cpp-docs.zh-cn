---
title: CMFCCaptionButton 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d6b1363dd77d4fd052a530a60b2e462e15a2291
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074431"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton 类

`CMFCCaptionButton`类实现的停靠窗格或微型框架窗口的标题栏显示的按钮。 通常，框架会自动创建标题按钮。

## <a name="syntax"></a>语法

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|name|描述|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|构造一个 CMFCCaptionButton 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|返回按钮表示的命令。|
|[CMFCCaptionButton::GetIconID](#geticonid)|返回与按钮关联的图像 ID。|
|[CMFCCaptionButton::GetRect](#getrect)|返回由按钮所占用的矩形。|
|[CMFCCaptionButton::GetSize](#getsize)|返回的宽度和按钮的高度。|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|指示是否将标题栏高度设置为最小大小。|
|[CMFCCaptionButton::Move](#move)|设置按钮绘制位置和窗口显示状态。|
|[CMFCCaptionButton::OnDraw](#ondraw)|绘制标题按钮。|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|设置标题栏的最小大小。|

## <a name="remarks"></a>备注

您可以从派生类[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)，并使用受保护的方法， `AddButton`，以添加到微型框架窗口的标题按钮。

CPaneFrameWnd.h 定义两种类型的标题按钮的命令 Id:

- AFX_CAPTION_BTN_PIN 停靠窗格支持自动隐藏模式时显示图钉按钮。

- AFX_CAPTION_BTN_CLOSE，后者将显示**关闭**按钮时可以关闭或隐藏窗格。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCCaptionButton`对象，并将标题栏的最小大小。

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>要求

**标头：** afxcaptionbutton.h

##  <a name="cmfccaptionbutton"></a>  CMFCCaptionButton::CMFCCaptionButton

构造 `CMFCCaptionButton` 对象。

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>参数

*nHit*<br/>
[in]与按钮关联的命令。

*bLeftAlign*<br/>
[in]指定是否向左对齐按钮。

下表列出了可能值*nHit*参数。

|“值”|命令|
|-----------|-------------|
|AFX_HTCLOSE|关闭按钮。|
|HTMINBUTTON|最小化按钮。|
|HTMAXBUTTON|最大化按钮。|
|AFX_HTLEFTBUTTON|向左的箭头按钮。|
|AFX_HTRIGHTBUTTON|向右箭头按钮。|
|AFX_HTMENU|向下箭头菜单按钮。|
|HTNOWHERE|默认值;不表示任何命令。|

### <a name="remarks"></a>备注

默认情况下，标题按钮将无法与命令相关联。

标题按钮上的右侧或左侧对齐。

##  <a name="gethit"></a>  CMFCCaptionButton::GetHit

返回按钮表示的命令。

```
UINT GetHit() const;
```

### <a name="return-value"></a>返回值

按钮表示该命令。

下表列出了可能的返回值。

|“值”|命令|
|-----------|-------------|
|AFX_HTCLOSE|关闭按钮。|
|HTMINBUTTON|最小化按钮。|
|HTMAXBUTTON|最大化按钮。|
|AFX_HTLEFTBUTTON|向左的箭头按钮。|
|AFX_HTRIGHTBUTTON|向右箭头按钮。|
|AFX_HTMENU|向下箭头菜单按钮。|
|HTNOWHERE|默认值;不表示任何命令。|

##  <a name="geticonid"></a>  CMFCCaptionButton::GetIconID

返回与按钮关联的图像 ID。

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>参数

*bHorz*<br/>
[in]左或向右箭头图像 Id;，则返回 TRUE如果为 FALSE 的向上或向下箭头的映像 Id。

*bMaximized*<br/>
[in]最大化图像 id;，则返回 TRUEFALSE 为最小化映像 id。

### <a name="return-value"></a>返回值

映像 id。

### <a name="remarks"></a>备注

参数指定的最小化映像 Id 或最大化标题按钮。

##  <a name="getrect"></a>  CMFCCaptionButton::GetRect

返回由按钮所占用的矩形。

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>返回值

表示按钮的位置的矩形。

### <a name="remarks"></a>备注

如果您不能看到的按钮，返回的大小为 0。

##  <a name="getsize"></a>  CMFCCaptionButton::GetSize

返回的宽度和按钮的高度。

```
static CSize GetSize();
```

### <a name="return-value"></a>返回值

外部按钮的尺寸。

### <a name="remarks"></a>备注

返回的大小包括按钮边距和边框。

##  <a name="isminiframebutton"></a>  CMFCCaptionButton::IsMiniFrameButton

指示是否将标题栏高度设置为最小大小。

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>返回值

如果标题设置为最小大小，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="move"></a>  CMFCCaptionButton::Move

设置按钮绘制位置和窗口显示状态。

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>参数

*ptTo*<br/>
[in]新的位置。

*bHide*<br/>
[in]是否显示该按钮。

##  <a name="ondraw"></a>  CMFCCaptionButton::OnDraw

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
[in]为按钮的设备上下文的指针。

*bActive*<br/>
[in]是否要绘制活动按钮图像。

*bHorz*<br/>
[in]保留供派生类中使用。

*bMaximized*<br/>
[in]是否要绘制最大化的按钮图像。

*bDisabled*<br/>
[in]是否要绘制启用的按钮图像。

### <a name="remarks"></a>备注

*BMaximized*参数使用时该按钮是最大化或最小化按钮。

##  <a name="setminiframebutton"></a>  CMFCCaptionButton::SetMiniFrameButton

设置标题栏的最小大小。

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>参数

*bSet*<br/>
[in]适用于最小的标题栏的高度;对于默认标题栏高度为 FALSE。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)
