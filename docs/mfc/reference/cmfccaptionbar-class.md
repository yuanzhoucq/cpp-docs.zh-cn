---
title: CMFCCaptionBar 类
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: 1a18e235c9f5875a977f740c26b917a3567a678d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264984"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar 类

一个`CMFCCaptionBar`对象是可以显示三个元素的控件条： 按钮、 文本标签和位图。 它一次只能显示一种类型的一个元素。 你可以将每个元素与控件进行左对齐、右对齐或居中对齐。 你还可将平面或 3D 样式应用于标题栏的顶部和底部边界。

## <a name="syntax"></a>语法

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCCaptionBar::Create](#create)|创建标题栏控件，并将其附加到`CMFCCaptionBar`对象。|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|指示另一个窗格是否可以动态地插入的标题栏和其父框架之间。 (重写[cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|
|[CMFCCaptionBar::EnableButton](#enablebutton)|启用或禁用的标题栏上的按钮。|
|[CMFCCaptionBar::GetAlignment](#getalignment)|返回指定元素的对齐方式。|
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|返回的标题栏的边框大小。|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|检索标题栏上的按钮的边框。|
|[CMFCCaptionBar::GetMargin](#getmargin)|返回的标题栏元素边缘的标题栏控件的边缘之间的距离。|
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|指定的标题栏是否在消息栏模式下。|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|从标题栏中删除位图图像。|
|[CMFCCaptionBar::RemoveButton](#removebutton)|从标题栏中删除该按钮。|
|[CMFCCaptionBar::RemoveIcon](#removeicon)|从标题栏中删除图标。|
|[CMFCCaptionBar::RemoveText](#removetext)|从标题栏中删除的文本标签。|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|设置的标题栏的位图图像。|
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|设置的标题栏的边框大小。|
|[CMFCCaptionBar::SetButton](#setbutton)|设置的标题栏的按钮。|
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|指定是否保持已按下按钮。|
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|设置按钮的工具提示。|
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|设置的标题栏的边框样式。|
|[CMFCCaptionBar::SetIcon](#seticon)|设置标题栏的图标。|
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|设置图像的标题栏的工具提示。|
|[CMFCCaptionBar::SetMargin](#setmargin)|设置的标题栏元素边缘的标题栏控件的边缘之间的距离。|
|[CMFCCaptionBar::SetText](#settext)|设置的标题栏的文本标签。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|由框架调用以填充在标题栏的背景。|
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|由框架调用以绘制边框的标题栏。|
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|由框架调用以绘制标题栏按钮。|
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|由框架调用以绘制标题栏图像。|
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|由框架调用以绘制的标题栏文本。|

### <a name="data-members"></a>数据成员

|name|描述|
|----------|-----------------|
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|标题栏背景色。|
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|在标题栏的边框的颜色。|
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|标题栏文本的颜色。|

## <a name="remarks"></a>备注

若要创建标题栏，请执行以下步骤：

1. 构造 `CMFCCaptionBar` 对象。 通常情况下，会将标题栏添加到框架窗口类。

1. 调用[CMFCCaptionBar::Create](#create)方法以创建标题栏控件并将其附加到`CMFCCaptionBar`对象。

1. 调用[CMFCCaptionBar::SetButton](#setbutton)， [CMFCCaptionBar::SetText](#settext)， [CMFCCaptionBar::SetIcon](#seticon)，和[CMFCCaptionBar::SetBitmap](#setbitmap)若要设置的标题栏元素。

当设置按钮元素时，必须为该按钮来指定命令 ID。 用户单击按钮时，标题栏将路由到父框架窗口具有此 ID 的 WM_COMMAND 消息。

标题栏还可以在消息栏模式下，它可以模拟在 Microsoft Office 2007 应用程序中显示的消息栏。 在消息栏模式下，标题栏会显示位图、 消息和一个按钮 （这通常会打开一个对话框。）可以将工具提示分配给位图。

若要启用消息栏模式下，调用[CMFCCaptionBar::Create](#create)和第四个参数 (bIsMessageBarMode) 设置为 TRUE。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCCaptionBar` 类中的各种方法。 该示例演示如何创建标题栏控件、 设置的标题栏的三维边框，设置以像素为单位的标题栏元素边缘的标题栏控件的边缘之间的距离，、 设置的标题栏按钮设置按钮的工具提示、 设置的标题栏的文本标签，设置的标题栏，位图图像，以及设置图像的工具提示的标题栏中。 此代码片段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>要求

**标头：** afxcaptionbar.h

##  <a name="create"></a>  CMFCCaptionBar::Create

创建标题栏控件，并将其附加到`CMFCCaptionBar`对象。

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
逻辑或组合的标题栏样式。

*pParentWnd*<br/>
标题栏控件的父窗口。

*uID*<br/>
标题栏控件的 ID。

*nHeight*<br/>
以像素为单位的标题栏控件的高度。 如果它为-1，是根据图标、 文本和标题栏控件显示的按钮的高度计算高度。

*bIsMessageBarMode*<br/>
标题栏中的消息条模式; 如果为 TRUEFALSE 否则为。

### <a name="return-value"></a>返回值

如果成功，则创建标题栏控件，则返回 TRUEFALSE 否则为。

### <a name="remarks"></a>备注

构造`CMFCCaptionBar`两个步骤中的对象。 首先调用构造函数中，，然后调用`Create`方法，用于创建 Windows 控件并将其附加到`CMFCCaptionBar`对象。

##  <a name="doesallowdyninsertbefore"></a>  CMFCCaptionBar::DoesAllowDynInsertBefore

指示另一个窗格是否可以动态地插入的标题栏和其父框架之间。

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>返回值

除非重写，否则返回 FALSE。

### <a name="remarks"></a>备注

##  <a name="enablebutton"></a>  CMFCCaptionBar::EnableButton

启用或禁用的标题栏上的按钮。

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]若要启用该按钮，则返回 FALSE 以禁用此按钮，则为 TRUE。

##  <a name="getalignment"></a>  CMFCCaptionBar::GetAlignment

返回指定元素的对齐方式。

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>参数

*elem*<br/>
[in]要为其检索对齐一个标题栏元素。

### <a name="return-value"></a>返回值

元素，如按钮、 位图、 文本或图标的对齐方式。

### <a name="remarks"></a>备注

元素的对齐方式可以是下列值之一：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="getbordersize"></a>  CMFCCaptionBar::GetBorderSize

返回的标题栏的边框大小。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>返回值

以像素为单位，边框的大小。

##  <a name="getbuttonrect"></a>  CMFCCaptionBar::GetButtonRect

检索标题栏上的按钮的边框。

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>返回值

一个`CRect`对象，其中包含标题栏上的按钮的边框的坐标。

##  <a name="getmargin"></a>  CMFCCaptionBar::GetMargin

返回的标题栏元素边缘的标题栏控件的边缘之间的距离。

```
int GetMargin() const;
```

### <a name="return-value"></a>返回值

以像素为单位的标题栏元素边缘的标题栏控件的边缘之间的距离。

##  <a name="ismessagebarmode"></a>  CMFCCaptionBar::IsMessageBarMode

指定的标题栏是否在消息栏模式下。

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>返回值

标题栏中的消息条模式; 如果为 TRUEFALSE 否则为。

### <a name="remarks"></a>备注

在消息栏模式下，标题栏会显示带工具提示、 消息文本和一个按钮的图像。

##  <a name="m_clrbarbackground"></a>  CMFCCaptionBar::m_clrBarBackground

标题栏背景色。

```
COLORREF m_clrBarBackground
```

##  <a name="m_clrbarborder"></a>  CMFCCaptionBar::m_clrBarBorder

在标题栏的边框的颜色。

```
COLORREF m_clrBarBorder
```

##  <a name="m_clrbartext"></a>  CMFCCaptionBar::m_clrBarText

标题栏文本的颜色。

```
COLORREF m_clrBarText
```

##  <a name="ondrawbackground"></a>  CMFCCaptionBar::OnDrawBackground

由框架调用以填充在标题栏的背景。

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的标题栏的指针。

*rect*<br/>
[in]要填充的边界矩形。

### <a name="remarks"></a>备注

`OnDrawBackground`要填充的标题栏的背景时调用方法。 默认实现使用填充的背景[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)颜色。

重写此方法在`CMFCCaptionBar`派生类，以自定义标题栏的外观。

##  <a name="ondrawborder"></a>  CMFCCaptionBar::OnDrawBorder

由框架调用以绘制边框的标题栏。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]一个设备上下文，用于显示边框。

*rect*<br/>
[in]边界矩形。

### <a name="remarks"></a>备注

默认情况下，边框具有平面的样式。

重写此方法在`CMFCCaptionBar`派生类，以自定义标题栏边框的外观。

##  <a name="ondrawbutton"></a>  CMFCCaptionBar::OnDrawButton

由框架调用以绘制标题栏按钮。

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向用来显示该按钮的设备上下文的指针。

*rect*<br/>
[in]按钮的边框。

*strButton*<br/>
[in]按钮的文本标签。

*bEnabled*<br/>
[in]如果启用该按钮; 则为 TRUEFALSE 否则为。

### <a name="remarks"></a>备注

重写此方法在`CMFCCaptionBar`派生类，以自定义标题栏按钮的外观。

##  <a name="ondrawimage"></a>  CMFCCaptionBar::OnDrawImage

由框架调用以绘制标题栏图像。

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向用于显示图像的设备上下文的指针。

*rect*<br/>
[in]指定图像的边框。

### <a name="remarks"></a>备注

重写此方法在`CMFCCaptionBar`派生类，以自定义图像外观。

##  <a name="ondrawtext"></a>  CMFCCaptionBar::OnDrawText

由框架调用以绘制的标题栏文本。

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向用来显示该按钮的设备上下文的指针。

*rect*<br/>
[in]文本的边框。

*strText*<br/>
[in]要显示的文本字符串。

### <a name="remarks"></a>备注

默认实现通过使用显示的文本`CDC::DrawText`并[CMFCCaptionBar::m_clrBarText](#m_clrbartext)颜色。

重写此方法在`CMFCCaptionBar`派生类，以自定义标题栏文本的外观。

##  <a name="removebitmap"></a>  CMFCCaptionBar::RemoveBitmap

从标题栏中删除位图图像。

```
void RemoveBitmap();
```

##  <a name="removebutton"></a>  CMFCCaptionBar::RemoveButton

从标题栏中删除该按钮。

```
void RemoveButton();
```

### <a name="remarks"></a>备注

自动调整的标题栏元素的布局。

##  <a name="removeicon"></a>  CMFCCaptionBar::RemoveIcon

从标题栏中删除图标。

```
void RemoveIcon();
```

##  <a name="removetext"></a>  CMFCCaptionBar::RemoveText

从标题栏中删除的文本标签。

```
void RemoveText();
```

##  <a name="setbitmap"></a>  CMFCCaptionBar::SetBitmap

设置的标题栏的位图图像。

```
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
[in]要设置的位图句柄。

*clrTransparent*<br/>
[in]一个指定位图的透明颜色的 RGB 值。

*bStretch*<br/>
[in]如果为 TRUE，如果不适合边界矩形的图像的拉伸位图。 否则不拉伸的位图。

*bmpAlignment*<br/>
[in]位图的对齐方式。

### <a name="remarks"></a>备注

使用此方法在标题栏上设置位图。

上一个位图被自动销毁。 如果标题栏将显示一个图标，因为你调用了[CMFCCaptionBar::SetIcon](#seticon)方法，除非通过调用删除该图标，将不会显示位图[CMFCCaptionBar::RemoveIcon](#removeicon)。

对齐位图所指定的*bmpAlignment*参数。  此参数可能是以下 `BarElementAlignment` 值之一：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setbordersize"></a>  CMFCCaptionBar::SetBorderSize

设置的标题栏的边框大小。

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>参数

*nSize*<br/>
[in]新的大小，以像素为单位的标题栏边框。

##  <a name="setbutton"></a>  CMFCCaptionBar::SetButton

设置的标题栏的按钮。

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
命令的按钮的标签。

*uiCmdUI*<br/>
按钮的命令 id。

*btnAlignmnet*<br/>
按钮的对齐方式。

*bHasDropDownArrow*<br/>
如果该按钮显示的下拉箭头，则返回 FALSE 否则，则为 TRUE。

##  <a name="setbuttonpressed"></a>  CMFCCaptionBar::SetButtonPressed

指定是否保持已按下按钮。

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>参数

*bPresed*<br/>
如果按钮使其按下的状态，FALSE，否则，则为 TRUE。

##  <a name="setbuttontooltip"></a>  CMFCCaptionBar::SetButtonToolTip

设置按钮的工具提示。

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>参数

*lpszToolTip*<br/>
[in]工具提示标题。

*lpszDescription*<br/>
[in]工具提示说明。

##  <a name="setflatborder"></a>  CMFCCaptionBar::SetFlatBorder

设置的标题栏的边框样式。

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>参数

*bFlat*<br/>
[in]如果标题栏的边框是平面的则为 TRUE。 如果此边框是 3D，则为 FALSE。

##  <a name="seticon"></a>  CMFCCaptionBar::SetIcon

设置标题栏的图标。

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>参数

*hIcon*<br/>
[in]若要设置图标的句柄。

*iconAlignment*<br/>
[in]图标的对齐方式。

### <a name="remarks"></a>备注

标题栏可以显示的图标或位图。 请参阅[CMFCCaptionBar::SetBitmap](#setbitmap)若要了解如何显示位图。 如果将设置一个图标或位图时，将始终显示图标。 调用[CMFCCaptionBar::RemoveIcon](#removeicon)从标题栏中删除图标。

根据对齐图标*iconAlignment*参数。 它可以是以下之一`BarElementAlignment`值：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setimagetooltip"></a>  CMFCCaptionBar::SetImageToolTip

设置图像的工具提示的标题栏中。

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>参数

*lpszToolTip*<br/>
[in]在工具提示的文本。

*lpszDescription*<br/>
[in]工具提示说明。

##  <a name="setmargin"></a>  CMFCCaptionBar::SetMargin

设置的标题栏元素边缘的标题栏控件的边缘之间的距离。

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>参数

*nMargin*<br/>
[in]以像素为单位的标题栏元素边缘的标题栏控件的边缘之间的距离。

##  <a name="settext"></a>  CMFCCaptionBar::SetText

设置的标题栏的文本标签。

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>参数

*strText*<br/>
[in]要设置的文本字符串。

*textAlignment*<br/>
[in]文本对齐方式。

### <a name="remarks"></a>备注

对齐的文本标签所指定的*文本斜体文本*参数。 它可以是以下之一`BarElementAlignment`值：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
