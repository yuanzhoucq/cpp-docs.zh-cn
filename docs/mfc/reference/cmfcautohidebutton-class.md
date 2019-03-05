---
title: CMFCAutoHideButton 类
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
ms.openlocfilehash: 15b449b4b9f9074966ac269787b1b3ca6f977f48
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264581"
---
# <a name="cmfcautohidebutton-class"></a>CMFCAutoHideButton 类

显示或隐藏配置为隐藏的 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 按钮。

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

## <a name="syntax"></a>语法

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Create](#create)|创建并初始化自动隐藏按钮。|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|检索自动隐藏按钮的对齐方式。|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|返回[CDockablePane](../../mfc/reference/cdockablepane-class.md)与自动隐藏按钮关联的对象。|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|确定自动隐藏按钮的大小。|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|返回自动隐藏按钮的文本标签大小。|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|突出显示自动隐藏按钮。|
|[CMFCAutoHideButton::IsActive](#isactive)|指示自动隐藏按钮是否处于活动状态。|
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|返回自动隐藏按钮的突出显示状态。|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|确定自动隐藏按钮的方向是水平还是垂直。|
|[CMFCAutoHideButton::IsTop](#istop)||
|[CMFCAutoHideButton::IsVisible](#isvisible)|指示按钮是否可见。|
|[CMFCAutoHideButton::Move](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|框架在绘制自动隐藏按钮时调用此方法。|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|框架在绘制自动隐藏按钮的边框时调用此方法。|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|框架在填充自动隐藏按钮的背景时调用此方法。|
|[CMFCAutoHideButton::ReplacePane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|显示或隐藏关联[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。|
|[CMFCAutoHideButton::ShowButton](#showbutton)|显示或隐藏自动隐藏按钮。|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>备注

在创建时，`CMFCAutoHideButton`对象附加到[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。 
  `CDockablePane` 对象随着用户与 `CMFCAutoHideButton` 对象交互而隐藏或显示。

默认情况下，框架在用户打开“自动隐藏”时自动创建 `CMFCAutoHideButton`。 框架可创建自定义 UI 类的元素而不是 `CMFCAutoHideButton` 类。 若要指定框架应使用的自定义 UI 类，请将静态成员变量 `CMFCAutoHideBar::m_pAutoHideButtonRTS` 设置为自定义 UI 类。 默认情况下，此变量设置为 `CMFCAutoHideButton`。

## <a name="example"></a>示例

下面的示例演示如何构造 `CMFCAutoHideButton` 对象和在 `CMFCAutoHideButton` 类中使用各种方法。 该示例演示如何使用 `CMFCAutoHideButton` 对象的 `Create` 方法来初始化该对象，并显示关联的 `CDockablePane` 类和自动隐藏按钮。

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>要求

**标头：** afxautohidebutton.h

##  <a name="bringtotop"></a>  CMFCAutoHideButton::BringToTop

```
void BringToTop();
```

### <a name="remarks"></a>备注

##  <a name="create"></a>  CMFCAutoHideButton::Create

创建并初始化自动隐藏按钮。

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>参数

*pParentBar*<br/>
[in]指向在父级工具栏的指针。

*pAutoHideWnd*<br/>
[in]一个指向[CDockablePane](../../mfc/reference/cdockablepane-class.md)对象。 此自动隐藏按钮隐藏和显示`CDockablePane`。

*dwAlignment*<br/>
[in]一个值，指定与主框架窗口按钮的对齐方式。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

当您创建`CMFCAutoHideButton`对象，必须将自动隐藏按钮关联与特定`CDockablePane`。 用户可以使用自动隐藏按钮隐藏和显示关联`CDockablePane`。

*DwAlignment*参数指示应用程序中的自动隐藏按钮所在的位置。 该参数可为下列任一值：

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

##  <a name="getalignment"></a>  CMFCAutoHideButton::GetAlignment

检索自动隐藏按钮的对齐方式。

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>返回值

一个 DWORD 值，该值包含自动隐藏按钮的当前对齐方式。

### <a name="remarks"></a>备注

自动隐藏按钮的对齐方式指示按钮所在的应用程序上。 它可以是以下值之一：

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

##  <a name="getautohidewindow"></a>  CMFCAutoHideButton::GetAutoHideWindow

返回[CDockablePane](../../mfc/reference/cdockablepane-class.md)与自动隐藏按钮关联的对象。

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>返回值

一个指向关联的`CDockablePane`对象。

### <a name="remarks"></a>备注

若要将与自动隐藏按钮相关联`CDockablePane`，传递`CDockablePane`作为参数[CMFCAutoHideButton::Create](#create)方法。

##  <a name="getparenttoolbar"></a>  CMFCAutoHideButton::GetParentToolBar

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getrect"></a>  CMFCAutoHideButton::GetRect

```
CRect GetRect() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getsize"></a>  CMFCAutoHideButton::GetSize

确定自动隐藏按钮的大小。

```
CSize GetSize() const;
```

### <a name="return-value"></a>返回值

一个`CSize`对象，其中包含该按钮的大小。

### <a name="remarks"></a>备注

计算的大小包括自动隐藏按钮的边框的大小。

##  <a name="gettextsize"></a>  CMFCAutoHideButton::GetTextSize

返回自动隐藏按钮的文本标签大小。

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>返回值

一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，其中包含自动隐藏按钮的文本的大小。

##  <a name="isactive"></a>  CMFCAutoHideButton::IsActive

指示自动隐藏按钮是否处于活动状态。

```
BOOL IsActive() const;
```

### <a name="return-value"></a>返回值

如果自动隐藏按钮处于活动状态; 则为 TRUEFALSE 否则为。

### <a name="remarks"></a>备注

时，自动隐藏按钮处于活动状态相关联[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)窗口所示。

##  <a name="ishorizontal"></a>  CMFCAutoHideButton::IsHorizontal

确定自动隐藏按钮的方向是水平还是垂直。

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>返回值

如果该按钮水平; 非零值否则为 0。

### <a name="remarks"></a>备注

框架将设置的方向[CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)对象时创建它。  你可以通过使用控制方向*dwAlignment*中的参数[CMFCAutoHideButton::Create](#create)方法。

##  <a name="istop"></a>  CMFCAutoHideButton::IsTop

```
BOOL IsTop() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="isvisible"></a>  CMFCAutoHideButton::IsVisible

指示自动隐藏按钮是否可见。

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>返回值

如果该按钮是可见的则为 TRUEFALSE 否则为。

##  <a name="ondraw"></a>  CMFCAutoHideButton::OnDraw

框架在绘制自动隐藏按钮时调用此方法。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

### <a name="remarks"></a>备注

如果你想要自定义应用程序中的自动隐藏按钮的外观，创建一个新类派生自`CMFCAutoHideButton`。 在派生类中，重写此方法。

##  <a name="ondrawborder"></a>  CMFCAutoHideButton::OnDrawBorder

框架在绘制自动隐藏按钮的边框时调用此方法。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

*rectBounds*<br/>
[in]自动隐藏按钮的边框。

*rectBorderSize*<br/>
[in]自动隐藏按钮的每个边边框粗细。

### <a name="remarks"></a>备注

如果你想要自定义应用程序中的每个自动隐藏按钮的边框，创建一个新类派生自`CMFCAutoHideButton`。 在派生类中，重写此方法。

##  <a name="onfillbackground"></a>  CMFCAutoHideButton::OnFillBackground

框架在填充自动隐藏按钮的背景时调用此方法。

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

*rect*<br/>
[in]自动隐藏按钮的边框。

### <a name="remarks"></a>备注

如果你想要自定义应用程序中的自动隐藏按钮的背景，创建一个新类派生自`CMFCAutoHideButton`。 在派生类中，重写此方法。

##  <a name="showattachedwindow"></a>  CMFCAutoHideButton::ShowAttachedWindow

显示或隐藏关联[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。

```
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
[in]一个布尔值，指定此方法显示附加`CDockablePane`。

##  <a name="showbutton"></a>  CMFCAutoHideButton::ShowButton

显示或隐藏自动隐藏按钮。

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
[in]一个布尔值，指定是否显示自动隐藏按钮。

##  <a name="move"></a>  CMFCAutoHideButton::Move

```
void Move(int nOffset);
```

### <a name="parameters"></a>参数

[in] *nOffset*<br/>

### <a name="remarks"></a>备注

##  <a name="replacepane"></a>  CMFCAutoHideButton::ReplacePane

```
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>参数

[in] *pNewBar*<br/>

### <a name="remarks"></a>备注

##  <a name="unsetautohidemode"></a>  CMFCAutoHideButton::UnSetAutoHideMode

禁用自动隐藏模式。

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>参数

*pFirstBarInGroup*<br/>
[in]指向组中的第一栏的指针。

### <a name="remarks"></a>备注

##  <a name="highlightbutton"></a>  CMFCAutoHideButton::HighlightButton

突出显示了自动隐藏按钮。

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>参数

*bHighlight*<br/>
指定新的自动隐藏按钮的状态。 TRUE 表示该按钮将突出显示，FALSE 表示不突出显示按钮。

### <a name="remarks"></a>备注

##  <a name="ishighlighted"></a>  CMFCAutoHideButton::IsHighlighted

返回自动隐藏按钮的突出显示状态。

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>返回值

返回 TRUE，如果自动隐藏按钮将突出显示;否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHideBar 类](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[CAutoHideDockSite 类](../../mfc/reference/cautohidedocksite-class.md)
