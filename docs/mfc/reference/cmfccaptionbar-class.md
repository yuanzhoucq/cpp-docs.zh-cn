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
ms.openlocfilehash: 3a1e8890176fe686b54fe4756dfd578869cbcdfb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367797"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar 类

对象`CMFCCaptionBar`是一个控件栏，可以显示三个元素：按钮、文本标签和位图。 它一次只能显示一种类型的一个元素。 你可以将每个元素与控件进行左对齐、右对齐或居中对齐。 你还可将平面或 3D 样式应用于标题栏的顶部和底部边界。

## <a name="syntax"></a>语法

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCCaption栏：创建](#create)|创建标题栏控件并将其附加到`CMFCCaptionBar`对象。|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|指示是否可以在标题栏及其父框架之间动态插入另一个窗格。 （覆盖[CBasePane：:DoesAllowDynInsert 之前](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).）|
|[CMFCCaption栏：启用按钮](#enablebutton)|启用或禁用标题栏上的按钮。|
|[CMFCCaption栏：获取对齐](#getalignment)|返回指定元素的对齐方式。|
|[CMFCCaptionbar：获取边界大小](#getbordersize)|返回标题栏的边框大小。|
|[CMFCCaptionbar：获取按钮](#getbuttonrect)|检索标题栏上按钮的边界矩形。|
|[CMFCCaptionbar：获取保证金](#getmargin)|返回标题条元素边缘与标题条控件边缘之间的距离。|
|[CMFCCaptionbar：：是消息栏模式](#ismessagebarmode)|指定字幕栏是否处于消息栏模式。|
|[CMFCCaption栏：删除位图](#removebitmap)|从标题栏中删除位图图像。|
|[CMFCCaption栏：删除按钮](#removebutton)|从标题栏中删除按钮。|
|[CMFCCaption栏：删除图标](#removeicon)|从标题栏中删除图标。|
|[CMFCCaption栏：删除文本](#removetext)|从标题栏中删除文本标签。|
|[CMFCCaption 栏：设置位图](#setbitmap)|设置标题栏的位图图像。|
|[CMFCCaption栏：设置边框大小](#setbordersize)|设置标题栏的边框大小。|
|[CMFCCaption栏：设置按钮](#setbutton)|设置标题栏的按钮。|
|[CMFCCaption 栏：设置按钮按下](#setbuttonpressed)|指定按钮是否保持按下状态。|
|[CMFCCaption栏：设置按钮工具提示](#setbuttontooltip)|设置按钮的工具提示。|
|[CMFCCaption 栏：设置平面边框](#setflatborder)|设置标题栏的边框样式。|
|[CMFCCaption栏：SetIcon](#seticon)|设置标题栏的图标。|
|[CMFC标题栏：：设置图像工具提示](#setimagetooltip)|设置标题栏的图像工具提示。|
|[CMFCCaption栏：设置边缘](#setmargin)|设置标题条元素边缘与标题条控件边缘之间的距离。|
|[CMFCCaption栏：设置文本](#settext)|设置标题栏的文本标签。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFCCaptionbar：在绘制背景](#ondrawbackground)|由框架调用以填充标题栏的背景。|
|[CMFCCaptionbar：OnDraw边框](#ondrawborder)|由框架调用以绘制标题栏的边框。|
|[CMFCCaptionbar：在绘制按钮](#ondrawbutton)|由框架调用以绘制标题栏按钮。|
|[CMFCCaptionbar：在图像上](#ondrawimage)|由框架调用以绘制标题栏图像。|
|[CMFCCaptionbar：onDrawtext](#ondrawtext)|由框架调用以绘制标题栏文本。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFCCaptionbar：m_clrBarBackground](#m_clrbarbackground)|标题栏的背景颜色。|
|[CMFCCaptionbar：m_clrBarBorder](#m_clrbarborder)|标题栏边框的颜色。|
|[CMFCCaptionbar：m_clrBarText](#m_clrbartext)|标题栏文本的颜色。|

## <a name="remarks"></a>备注

要创建标题栏，请按照以下步骤操作：

1. 构造 `CMFCCaptionBar` 对象。 通常，您将字幕栏添加到框架窗口类。

1. 调用[CMFCCaptionBar：：创建](#create)方法来创建字幕栏控件并将其附加到`CMFCCaptionBar`对象。

1. 调用[CMFCCaption 栏：设置按钮](#setbutton)[，CMFCCaption 栏：设置文本](#settext)[，CMFCCaption 栏：：SetIcon，](#seticon)和[CMFCCaption 栏：：SetBitmap](#setbitmap)设置标题栏元素。

设置按钮元素时，必须为按钮分配命令 ID。 当用户单击该按钮时，标题栏会将具有此 ID 的WM_COMMAND消息路由到父框架窗口。

标题栏也可以在消息栏模式下工作，该模式模拟 Microsoft Office 2007 应用程序中出现的消息栏。 在消息栏模式下，标题栏显示位图、消息和按钮（通常打开对话框）。您可以为位图分配工具提示。

要启用消息栏模式，请致电[CMFCCaptionBar：：创建](#create)并将第四个参数（bIsMessageBarMode）设置为 TRUE。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCCaptionBar` 类中的各种方法。 该示例演示如何创建标题栏控件、设置字幕栏的 3D 边框、设置字幕栏元素边缘和标题栏控件边缘之间的距离（以像素为单位）、设置标题栏的按钮、设置按钮的工具提示、设置字幕栏的文本标签、设置标题栏的位图图像并在标题栏中设置图像的工具提示。 此代码段是 MS [Office 2007 演示示例](../../overview/visual-cpp-samples.md)的一部分。

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

**标题：** afxcaptionbar.h

## <a name="cmfccaptionbarcreate"></a><a name="create"></a>CMFCCaption栏：创建

创建标题栏控件并将其附加到`CMFCCaptionBar`对象。

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
标题栏样式的逻辑 OR 组合。

*pparentwnd*<br/>
标题栏控件的父窗口。

*Uid*<br/>
标题栏控件的 ID。

*nHeight*<br/>
标题栏控件的高度（以像素为单位）。 如果为 -1，则根据图标的高度、文本和标题栏控件显示的按钮计算高度。

*bIsMessageBar模式*<br/>
如果标题栏处于消息栏模式，则为 TRUE;如果标题栏处于消息栏模式。"否则。

### <a name="return-value"></a>返回值

如果字幕栏控件已成功创建，则为 TRUE;如果字幕栏控件已成功创建，则为 TRUE。否则。

### <a name="remarks"></a>备注

分两步`CMFCCaptionBar`构造对象。 首先调用构造函数，然后调用`Create`方法，该方法创建 Windows 控件并将其附加到`CMFCCaptionBar`对象。

## <a name="cmfccaptionbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCCaption栏：:DoesAllowDynInsert之前

指示是否可以在标题栏及其父框架之间动态插入另一个窗格。

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>返回值

返回 FALSE，除非重写。

### <a name="remarks"></a>备注

## <a name="cmfccaptionbarenablebutton"></a><a name="enablebutton"></a>CMFCCaption栏：启用按钮

启用或禁用标题栏上的按钮。

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 启用按钮，FALSE 禁用该按钮。

## <a name="cmfccaptionbargetalignment"></a><a name="getalignment"></a>CMFCCaption栏：获取对齐

返回指定元素的对齐方式。

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>参数

*埃莱姆*<br/>
[在]要为其检索对齐的标题栏元素。

### <a name="return-value"></a>返回值

元素（如按钮、位图、文本或图标）的对齐方式。

### <a name="remarks"></a>备注

元素的对齐可以是以下值之一：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbargetbordersize"></a><a name="getbordersize"></a>CMFCCaptionbar：获取边界大小

返回标题栏的边框大小。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>返回值

边框的大小（以像素为单位）。

## <a name="cmfccaptionbargetbuttonrect"></a><a name="getbuttonrect"></a>CMFCCaptionbar：获取按钮

检索标题栏上按钮的边界矩形。

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>返回值

包含`CRect`标题栏上按钮边界矩形的坐标的对象。

## <a name="cmfccaptionbargetmargin"></a><a name="getmargin"></a>CMFCCaptionbar：获取保证金

返回标题条元素边缘与标题条控件边缘之间的距离。

```
int GetMargin() const;
```

### <a name="return-value"></a>返回值

标题条元素边缘与标题条控件边缘之间的距离（以像素为单位）。

## <a name="cmfccaptionbarismessagebarmode"></a><a name="ismessagebarmode"></a>CMFCCaptionbar：：是消息栏模式

指定字幕栏是否处于消息栏模式。

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>返回值

如果标题栏处于消息栏模式，则为 TRUE;如果标题栏处于消息栏模式。"否则。

### <a name="remarks"></a>备注

在消息栏模式下，标题栏显示带有工具提示、消息文本和按钮的图像。

## <a name="cmfccaptionbarm_clrbarbackground"></a><a name="m_clrbarbackground"></a>CMFCCaptionbar：m_clrBarBackground

标题栏的背景颜色。

```
COLORREF m_clrBarBackground
```

## <a name="cmfccaptionbarm_clrbarborder"></a><a name="m_clrbarborder"></a>CMFCCaptionbar：m_clrBarBorder

标题栏边框的颜色。

```
COLORREF m_clrBarBorder
```

## <a name="cmfccaptionbarm_clrbartext"></a><a name="m_clrbartext"></a>CMFCCaptionbar：m_clrBarText

标题栏文本的颜色。

```
COLORREF m_clrBarText
```

## <a name="cmfccaptionbarondrawbackground"></a><a name="ondrawbackground"></a>CMFCCaptionbar：在绘制背景

由框架调用以填充标题栏的背景。

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向字幕栏的设备上下文的指针。

*矩形*<br/>
[在]要填充的边界矩形。

### <a name="remarks"></a>备注

当`OnDrawBackground`标题栏的背景即将填充时，将调用该方法。 默认实现使用[CMFCCaptionBar：：：m_clrBarBackground](#m_clrbarbackground)颜色填充背景。

在`CMFCCaptionBar`派生类中重写此方法以自定义标题栏的外观。

## <a name="cmfccaptionbarondrawborder"></a><a name="ondrawborder"></a>CMFCCaptionbar：OnDraw边框

由框架调用以绘制标题栏的边框。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]用于显示边框的设备上下文。

*矩形*<br/>
[在]边界矩形。

### <a name="remarks"></a>备注

默认情况下，边框具有平面样式。

在`CMFCCaptionBar`派生类中重写此方法以自定义字幕栏边框的外观。

## <a name="cmfccaptionbarondrawbutton"></a><a name="ondrawbutton"></a>CMFCCaptionbar：在绘制按钮

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
[在]指向用于显示按钮的设备上下文的指针。

*矩形*<br/>
[在]按钮的边界矩形。

*斯特按钮*<br/>
[在]按钮的文本标签。

*b 启用*<br/>
[在]如果启用了按钮，则为 TRUE;否则。

### <a name="remarks"></a>备注

在`CMFCCaptionBar`派生类中重写此方法以自定义字幕栏按钮的外观。

## <a name="cmfccaptionbarondrawimage"></a><a name="ondrawimage"></a>CMFCCaptionbar：在图像上

由框架调用以绘制标题栏图像。

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向用于显示图像的设备上下文的指针。

*矩形*<br/>
[在]指定图像的边界矩形。

### <a name="remarks"></a>备注

在`CMFCCaptionBar`派生类中重写此方法以自定义图像外观。

## <a name="cmfccaptionbarondrawtext"></a><a name="ondrawtext"></a>CMFCCaptionbar：onDrawtext

由框架调用以绘制标题栏文本。

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向用于显示按钮的设备上下文的指针。

*矩形*<br/>
[在]文本的边界矩形。

*斯特文本*<br/>
[在]要显示的文本字符串。

### <a name="remarks"></a>备注

默认实现通过使用`CDC::DrawText`和[CMFCCaptionBar：：m_clrBarText](#m_clrbartext)颜色来显示文本。

在`CMFCCaptionBar`派生类中重写此方法以自定义字幕栏文本的外观。

## <a name="cmfccaptionbarremovebitmap"></a><a name="removebitmap"></a>CMFCCaption栏：删除位图

从标题栏中删除位图图像。

```
void RemoveBitmap();
```

## <a name="cmfccaptionbarremovebutton"></a><a name="removebutton"></a>CMFCCaption栏：删除按钮

从标题栏中删除按钮。

```
void RemoveButton();
```

### <a name="remarks"></a>备注

字幕条元素的布局会自动调整。

## <a name="cmfccaptionbarremoveicon"></a><a name="removeicon"></a>CMFCCaption栏：删除图标

从标题栏中删除图标。

```
void RemoveIcon();
```

## <a name="cmfccaptionbarremovetext"></a><a name="removetext"></a>CMFCCaption栏：删除文本

从标题栏中删除文本标签。

```
void RemoveText();
```

## <a name="cmfccaptionbarsetbitmap"></a><a name="setbitmap"></a>CMFCCaption 栏：设置位图

设置标题栏的位图图像。

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
[在]要设置的位图的句柄。

*clr透明*<br/>
[在]指定位图的透明颜色的 RGB 值。

*b 拉伸*<br/>
[在]如果为 TRUE，则如果位图不适合图像边界矩形，则位图将拉伸。 否则，位图不会拉伸。

*bmp对齐*<br/>
[在]位图的对齐方式。

### <a name="remarks"></a>备注

使用此方法在标题栏上设置位图。

以前的位图将自动销毁。 如果标题栏显示图标，因为您调用了[CMFCCaptionBar：：setIcon](#seticon)方法，则除非通过调用[CMFCCaptionBar：：：：删除图标](#removeicon)来删除该图标，否则将不会显示位图。

位图按*bmpAlignment 参数*指定对齐。  此参数可能是以下 `BarElementAlignment` 值之一：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetbordersize"></a><a name="setbordersize"></a>CMFCCaption栏：设置边框大小

设置标题栏的边框大小。

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>参数

*nSize*<br/>
[在]标题栏边框的新大小（以像素为单位）。

## <a name="cmfccaptionbarsetbutton"></a><a name="setbutton"></a>CMFCCaption栏：设置按钮

设置标题栏的按钮。

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
按钮的命令标签。

*乌伊CmdUI*<br/>
按钮的命令 ID。

*btnalignmnet*<br/>
按钮的对齐方式。

*b哈斯下拉箭头*<br/>
如果按钮显示下拉箭头，则为 TRUE，否则为 FALSE。

## <a name="cmfccaptionbarsetbuttonpressed"></a><a name="setbuttonpressed"></a>CMFCCaption 栏：设置按钮按下

指定按钮是否保持按下状态。

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>参数

*bPresed*<br/>
如果按钮保持其按下状态，则为 TRUE，否则为 FALSE。

## <a name="cmfccaptionbarsetbuttontooltip"></a><a name="setbuttontooltip"></a>CMFCCaption栏：设置按钮工具提示

设置按钮的工具提示。

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>参数

*lpszToolTip*<br/>
[在]工具提示标题。

*lpsz描述*<br/>
[在]工具提示说明。

## <a name="cmfccaptionbarsetflatborder"></a><a name="setflatborder"></a>CMFCCaption 栏：设置平面边框

设置标题栏的边框样式。

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>参数

*bFlat*<br/>
[在]如果标题栏的边框是平面的，则为 TRUE。 如果边框为 3D，则 FALSE。

## <a name="cmfccaptionbarseticon"></a><a name="seticon"></a>CMFCCaption栏：SetIcon

设置标题栏的图标。

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>参数

*hIcon*<br/>
[在]要设置的图标的句柄。

*图标对齐*<br/>
[在]图标的对齐方式。

### <a name="remarks"></a>备注

标题栏可以显示图标或位图。 请参阅[CMFCCaption 栏：SetBitmap](#setbitmap)以了解如何显示位图。 如果同时设置图标和位图，则始终显示该图标。 调用[CMFCCaption 栏：删除图标](#removeicon)以从字幕栏中删除图标。

图标根据*图标对齐参数对齐*。 它可以是以下`BarElementAlignment`值之一：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetimagetooltip"></a><a name="setimagetooltip"></a>CMFC标题栏：：设置图像工具提示

在标题栏中设置图像的工具提示。

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>参数

*lpszToolTip*<br/>
[在]工具提示的文本。

*lpsz描述*<br/>
[在]工具提示说明。

## <a name="cmfccaptionbarsetmargin"></a><a name="setmargin"></a>CMFCCaption栏：设置边缘

设置标题条元素边缘与标题条控件边缘之间的距离。

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>参数

*nMargin*<br/>
[在]标题条元素边缘与标题条控件边缘之间的距离（以像素为单位）。

## <a name="cmfccaptionbarsettext"></a><a name="settext"></a>CMFCCaption栏：设置文本

设置标题栏的文本标签。

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>参数

*斯特文本*<br/>
[在]要设置的文本字符串。

*文本对齐*<br/>
[在]文本对齐。

### <a name="remarks"></a>备注

文本标签按*文本对齐*参数指定对齐。 它可以是以下`BarElementAlignment`值之一：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
