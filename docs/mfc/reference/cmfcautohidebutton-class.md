---
title: CMFC自动隐藏按钮类
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
ms.openlocfilehash: 3ea6ce13b8cca7e0130fe14459a832b476391b0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751673"
---
# <a name="cmfcautohidebutton-class"></a>CMFC自动隐藏按钮类

显示或隐藏配置为隐藏的 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 按钮。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Create](#create)|创建并初始化自动隐藏按钮。|
|[CMFC自动隐藏按钮：：获取对齐](#getalignment)|检索自动隐藏按钮的对齐方式。|
|[CMFC自动隐藏按钮：：获取自动隐藏窗口](#getautohidewindow)|返回与自动隐藏按钮关联的[CDockablePane](../../mfc/reference/cdockablepane-class.md)对象。|
|[CMFC自动隐藏按钮：：获取父项工具栏](#getparenttoolbar)||
|[CMFC自动隐藏按钮：：获取 Rect](#getrect)||
|[CMFC自动隐藏按钮：获取大小](#getsize)|确定自动隐藏按钮的大小。|
|[CMFC自动隐藏按钮：：获取文本大小](#gettextsize)|返回自动隐藏按钮的文本标签大小。|
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
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|显示或隐藏关联的[可装窗格类](../../mfc/reference/cdockablepane-class.md)。|
|[CMFCAutoHideButton::ShowButton](#showbutton)|显示或隐藏自动隐藏按钮。|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>备注

在创建时，`CMFCAutoHideButton`对象附加到[可装板类](../../mfc/reference/cdockablepane-class.md)。 `CDockablePane` 对象随着用户与 `CMFCAutoHideButton` 对象交互而隐藏或显示。

默认情况下，框架在用户打开“自动隐藏”时自动创建 `CMFCAutoHideButton`。 框架可创建自定义 UI 类的元素而不是 `CMFCAutoHideButton` 类。 若要指定框架应使用的自定义 UI 类，请将静态成员变量 `CMFCAutoHideBar::m_pAutoHideButtonRTS` 设置为自定义 UI 类。 默认情况下，此变量设置为 `CMFCAutoHideButton`。

## <a name="example"></a>示例

下面的示例演示如何构造 `CMFCAutoHideButton` 对象和在 `CMFCAutoHideButton` 类中使用各种方法。 该示例演示如何使用 `CMFCAutoHideButton` 对象的 `Create` 方法来初始化该对象，并显示关联的 `CDockablePane` 类和自动隐藏按钮。

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>要求

**标头：** afxautohidebutton.h

## <a name="cmfcautohidebuttonbringtotop"></a><a name="bringtotop"></a>CMFC自动隐藏按钮：：带上顶部

```cpp
void BringToTop();
```

### <a name="remarks"></a>备注

## <a name="cmfcautohidebuttoncreate"></a><a name="create"></a>CMFC自动隐藏按钮：：创建

创建并初始化自动隐藏按钮。

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>参数

*p 父栏*<br/>
[在]指向父工具栏的指针。

*pAutoHidewnd*<br/>
[在]指向[可多克窗格对象的指针](../../mfc/reference/cdockablepane-class.md)。 此自动隐藏按钮隐藏并显示 。 `CDockablePane`

*dwalignment*<br/>
[在]指定按钮与主框架窗口对齐的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

创建`CMFCAutoHideButton`对象时，必须将自动隐藏按钮与特定的`CDockablePane`。 用户可以使用自动隐藏按钮隐藏和显示关联的`CDockablePane`。

*dwAlignment*参数指示自动隐藏按钮驻留在应用程序中的位置。 该参数可为下列任一值：

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetalignment"></a><a name="getalignment"></a>CMFC自动隐藏按钮：：获取对齐

检索自动隐藏按钮的对齐方式。

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>返回值

包含自动隐藏按钮的当前对齐方式的 DWORD 值。

### <a name="remarks"></a>备注

自动隐藏按钮的对齐方式指示按钮驻留在应用程序上的位置。 它可以是以下任一值：

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetautohidewindow"></a><a name="getautohidewindow"></a>CMFC自动隐藏按钮：：获取自动隐藏窗口

返回与自动隐藏按钮关联的[CDockablePane](../../mfc/reference/cdockablepane-class.md)对象。

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>返回值

指向关联`CDockablePane`对象的指针。

### <a name="remarks"></a>备注

要将自动隐藏按钮与 相关联`CDockablePane`，请`CDockablePane`将 作为参数传递给[CMFCAutoHideButton：：create](#create)方法。

## <a name="cmfcautohidebuttongetparenttoolbar"></a><a name="getparenttoolbar"></a>CMFC自动隐藏按钮：：获取父项工具栏

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebuttongetrect"></a><a name="getrect"></a>CMFC自动隐藏按钮：：获取 Rect

```
CRect GetRect() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebuttongetsize"></a><a name="getsize"></a>CMFC自动隐藏按钮：获取大小

确定自动隐藏按钮的大小。

```
CSize GetSize() const;
```

### <a name="return-value"></a>返回值

包含`CSize`按钮大小的对象。

### <a name="remarks"></a>备注

计算的大小包括自动隐藏按钮的边框大小。

## <a name="cmfcautohidebuttongettextsize"></a><a name="gettextsize"></a>CMFC自动隐藏按钮：：获取文本大小

返回自动隐藏按钮的文本标签大小。

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>返回值

包含自动隐藏按钮的文本大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

## <a name="cmfcautohidebuttonisactive"></a><a name="isactive"></a>CMFC自动隐藏按钮：：活动

指示自动隐藏按钮是否处于活动状态。

```
BOOL IsActive() const;
```

### <a name="return-value"></a>返回值

如果自动隐藏按钮处于活动状态，则为 TRUE;否则。

### <a name="remarks"></a>备注

显示关联的[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)窗口时，自动隐藏按钮处于活动状态。

## <a name="cmfcautohidebuttonishorizontal"></a><a name="ishorizontal"></a>CMFC自动隐藏按钮：：是水平的

确定自动隐藏按钮的方向是水平还是垂直。

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>返回值

如果按钮是水平的，则非零;0 否则。

### <a name="remarks"></a>备注

框架在创建[CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)对象时设置其方向。  您可以使用[CMFCAutoHideButton：：create](#create)方法中的*dwAlignment*参数来控制方向。

## <a name="cmfcautohidebuttonistop"></a><a name="istop"></a>CMFC自动隐藏按钮：：是顶部

```
BOOL IsTop() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcautohidebuttonisvisible"></a><a name="isvisible"></a>CMFC自动隐藏按钮：：可见

指示自动隐藏按钮是否可见。

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>返回值

如果按钮可见，则为 TRUE;否则。

## <a name="cmfcautohidebuttonondraw"></a><a name="ondraw"></a>CMFC自动隐藏按钮：：开机

框架在绘制自动隐藏按钮时调用此方法。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

### <a name="remarks"></a>备注

如果要自定义应用程序中自动隐藏按钮的外观，请创建派生自`CMFCAutoHideButton`的新类。 在派生类中，重写此方法。

## <a name="cmfcautohidebuttonondrawborder"></a><a name="ondrawborder"></a>CMFC自动隐藏按钮：：在绘制边框

框架在绘制自动隐藏按钮的边框时调用此方法。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*rectBunds*<br/>
[在]自动隐藏按钮的边界矩形。

*整边界大小*<br/>
[在]自动隐藏按钮每侧的边框厚度。

### <a name="remarks"></a>备注

如果要自定义应用程序中每个自动隐藏按钮的边框，请创建派生自 的新类`CMFCAutoHideButton`。 在派生类中，重写此方法。

## <a name="cmfcautohidebuttononfillbackground"></a><a name="onfillbackground"></a>CMFC自动隐藏按钮：：在填充背景

框架在填充自动隐藏按钮的背景时调用此方法。

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]自动隐藏按钮的边界矩形。

### <a name="remarks"></a>备注

如果要自定义应用程序中自动隐藏按钮的背景，请创建派生自 的新类`CMFCAutoHideButton`。 在派生类中，重写此方法。

## <a name="cmfcautohidebuttonshowattachedwindow"></a><a name="showattachedwindow"></a>CMFC自动隐藏按钮：：显示附加窗口

显示或隐藏关联的[可装窗格类](../../mfc/reference/cdockablepane-class.md)。

```cpp
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
[在]指定此方法是否显示附加`CDockablePane`的 布尔。

## <a name="cmfcautohidebuttonshowbutton"></a><a name="showbutton"></a>CMFC自动隐藏按钮：：显示按钮

显示或隐藏自动隐藏按钮。

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
[在]指定是否显示自动隐藏按钮的布尔。

## <a name="cmfcautohidebuttonmove"></a><a name="move"></a>CMFC自动隐藏按钮：：移动

```cpp
void Move(int nOffset);
```

### <a name="parameters"></a>参数

[在]*n偏移*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcautohidebuttonreplacepane"></a><a name="replacepane"></a>CMFC自动隐藏按钮：：替换窗格

```cpp
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>参数

[在]*pNewBar*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcautohidebuttonunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFC自动隐藏按钮：：取消设置自动隐藏模式

禁用自动隐藏模式。

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>参数

*普第一巴林集团*<br/>
[在]指向组中的第一个条形的指针。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebuttonhighlightbutton"></a><a name="highlightbutton"></a>CMFC自动隐藏按钮：：高光按钮

突出显示自动隐藏按钮。

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>参数

*b 高光*<br/>
指定新的自动隐藏按钮状态。 TRUE 表示按钮高亮显示，FALSE 表示按钮未突出显示。

### <a name="remarks"></a>备注

## <a name="cmfcautohidebuttonishighlighted"></a><a name="ishighlighted"></a>CMFC自动隐藏按钮：：已突出显示

返回自动隐藏按钮的高光状态。

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>返回值

如果自动隐藏按钮突出显示，则返回 TRUE;如果自动隐藏按钮突出显示，则返回 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHidebar 类](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[CAutoHideDockSite 类](../../mfc/reference/cautohidedocksite-class.md)
