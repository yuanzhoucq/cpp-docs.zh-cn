---
title: CMFCRibbonColorButton 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
ms.openlocfilehash: 528b883d75889589c7021f462324dd9dcb71be25
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754844"
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton 类

`CMFCRibbonColorButton` 类用于实现可添加到功能区栏的颜色按钮。 功能区颜色按钮显示包含一个或多个调色板的下拉菜单。

## <a name="syntax"></a>语法

```
class CMFCRibbonColorButton : public CMFCRibbonGallery
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC彩带颜色按钮：：添加颜色组](#addcolorsgroup)|将一组颜色添加到常规颜色区域。|
|[CMFC功能彩带按钮：：启用自动按钮](#enableautomaticbutton)|指定是否启用 **** “自动”按钮。|
|[CMFC功能彩带按钮：：启用其他按钮](#enableotherbutton)|启用“其他” **** 按钮。|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFC彩带颜色按钮：获取颜色](#getcolor)|返回当前选定的颜色。|
|[CMFC功能彩带按钮：获取ColorBox大小](#getcolorboxsize)|返回在颜色栏上显示的颜色元素的大小。|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFC彩带颜色按钮：：获取突出显示的颜色](#gethighlightedcolor)|返回调色板弹出窗口上当前选定的元素的颜色。|
|[CMFC彩带颜色按钮：：删除所有颜色组](#removeallcolorgroups)|删除常规颜色区域中所有颜色组。|
|[CMFC彩带颜色按钮：：设置颜色](#setcolor)|选择常规颜色区域中的某种颜色。|
|[CMFC功能彩带颜色按钮：：设置彩色框大小](#setcolorboxsize)|设置在颜色条上显示的所有颜色元素的大小。|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFC功能彩带颜色按钮：：设置文档颜色](#setdocumentcolors)|指定要在文档颜色区域中显示的 RGB 值列表。|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>备注

功能区颜色按钮显示用户按下它时的颜色条。 默认情况下，此颜色条包含称为常规颜色区域的颜色选择调色板。 （可选）颜色条包含一个 **** “自动”按钮，该按钮允许用户选择默认颜色，以及包含一个“其他” **** 按钮，该按钮用于显示包含其他颜色的调色板弹出窗口。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCRibbonColorButton` 类中的各种方法。 该示例演示了如何构造 `CMFCRibbonColorButton` 对象、设置大图像、启用 **** “自动”按钮、启用 **** “其他”按钮、设置列数、设置颜色条上显示的所有颜色元素的大小、将一组颜色添加到常规彩色区域中以及指定要在文档颜色区域中显示的 RGB 值列表。 此代码片段属于 [Draw Client 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>要求

**标头:** afxribboncolorbutton.h

## <a name="cmfcribboncolorbuttonaddcolorsgroup"></a><a name="addcolorsgroup"></a>CMFC彩带颜色按钮：：添加颜色组

将一组颜色添加到常规颜色区域。

```cpp
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
[在]组名称。

*lstColors*<br/>
[在]颜色列表。

*b 连续列*<br/>
[在]控制颜色项在组中的显示方式。 如果为 TRUE，则绘制颜色项目时没有垂直间距。 如果 FALSE，则使用垂直间距绘制颜色项。

### <a name="remarks"></a>备注

使用此函数可以使颜色弹出窗口显示多组颜色。 您可以控制颜色在组中的显示方式。

## <a name="cmfcribboncolorbuttoncmfcribboncolorbutton"></a><a name="cmfcribboncolorbutton"></a>CMFC彩带颜色按钮：：CMFC彩带颜色按钮

构造 `CMFCRibbonColorButton` 对象。

```
CMFCRibbonColorButton();

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex,
    COLORREF color = RGB(0, 0, 0));

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    BOOL bSimpleButtonLook,
    int nSmallImageIndex,
    int nLargeImageIndex,
    COLORREF color = RGB(0, 0, 0));
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]指定在用户单击按钮时要执行的命令 ID。

*lpszText*<br/>
[在]指定要显示在按钮上的文本。

*n 小图像索引*<br/>
[在]要显示在按钮上的小图像的零基索引。

*颜色*<br/>
[在]按钮的颜色（默认为黑色）。

*b 简单按钮外观*<br/>
[在]如果为 TRUE，则该按钮将作为一个简单的矩形绘制。

*nLargeImageIndex*<br/>
[在]要显示在按钮上的大图像的零基索引。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribboncolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFC功能彩带按钮：：启用自动按钮

指定是否启用 **** “自动”按钮。

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]**"自动"** 按钮的标签。

*颜色 自动*<br/>
[在]指定 **"自动**"按钮默认颜色的 RGB 值。

*b 启用*<br/>
[在]如果启用了"自动"按钮，则为 TRUE;如果启用了 **"自动"** 按钮，则为 TRUE。如果禁用，则 FALSE。

*lpszToolTip*<br/>
[在]**"自动"** 按钮的工具提示。

*蓬托普*<br/>
[在]指定 **"自动"** 按钮是否位于调色板之前的顶部。

*bDraw边框*<br/>
[在]如果应用程序在色带颜色按钮的颜色栏周围绘制边框，则为 TRUE。 颜色栏显示当前选择的颜色。 如果应用程序未绘制边框，则 FALSE

## <a name="cmfcribboncolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFC功能彩带按钮：：启用其他按钮

启用“其他” **** 按钮。

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
按钮的标签。

*lpszToolTip*<br/>
**"其他**"按钮的工具提示文本。

### <a name="remarks"></a>备注

"**其他**"按钮是显示在颜色组下方的按钮。 当用户单击 **"其他**"按钮时，将显示颜色对话框。

## <a name="cmfcribboncolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFC彩带颜色按钮：获取自动颜色

检索当前自动按钮颜色。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>返回值

表示当前自动按钮颜色的 RGB 颜色值。

### <a name="remarks"></a>备注

自动按钮颜色由传递给方法的`colorAutomatic``CMFCRibbonColorButton::EnableAutomaticButton`参数设置。

## <a name="cmfcribboncolorbuttongetcolor"></a><a name="getcolor"></a>CMFC彩带颜色按钮：获取颜色

返回当前选定的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

单击按钮选择的颜色。

## <a name="cmfcribboncolorbuttongetcolorboxsize"></a><a name="getcolorboxsize"></a>CMFC功能彩带按钮：获取ColorBox大小

返回在颜色栏上显示的颜色元素的大小。

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>返回值

下拉调色板中颜色按钮的大小。

## <a name="cmfcribboncolorbuttongetcolumns"></a><a name="getcolumns"></a>CMFC功能彩带按钮：：获取列

获取功能区颜色按钮的库显示的行中的项目数。

```
int GetColumns() const;
```

### <a name="return-value"></a>返回值

返回每行中的图标数。

### <a name="remarks"></a>备注

## <a name="cmfcribboncolorbuttongethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFC彩带颜色按钮：：获取突出显示的颜色

返回弹出式调色板上当前选定元素的颜色。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>返回值

弹出式调色板上当前选定元素的颜色。

## <a name="cmfcribboncolorbuttonremoveallcolorgroups"></a><a name="removeallcolorgroups"></a>CMFC彩带颜色按钮：：删除所有颜色组

删除常规颜色区域中所有颜色组。

```cpp
void RemoveAllColorGroups();
```

## <a name="cmfcribboncolorbuttonsetcolor"></a><a name="setcolor"></a>CMFC彩带颜色按钮：：设置颜色

选择常规颜色区域中的某种颜色。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]要设置的颜色。

## <a name="cmfcribboncolorbuttonsetcolorboxsize"></a><a name="setcolorboxsize"></a>CMFC功能彩带颜色按钮：：设置彩色框大小

设置在颜色条上显示的所有颜色元素的大小。

```cpp
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>参数

*大小盒*<br/>
[在]调色板中颜色按钮的新大小。

## <a name="cmfcribboncolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFC彩带颜色按钮：：设置颜色名称

为指定颜色设置新名称。

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]颜色的 RGB 值。

*strName*<br/>
[在]指定颜色的新名称。

### <a name="remarks"></a>备注

因为它调用`CMFCColorBar::SetColorName`，此方法更改应用程序中所有`CMFCColorBar`对象中指定颜色的名称。

## <a name="cmfcribboncolorbuttonsetcolumns"></a><a name="setcolumns"></a>CMFC 功能色按钮：：设置列

设置在用户颜色选择过程中向用户显示的颜色表中显示的列数。

```cpp
void SetColumns(int nColumns);
```

### <a name="parameters"></a>参数

*nColumns*<br/>
[在]每行中显示的颜色图标数。

### <a name="remarks"></a>备注

## <a name="cmfcribboncolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFC功能彩带颜色按钮：：设置文档颜色

指定要在文档颜色区域中显示的 RGB 值列表。

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]要与文档颜色一起显示的文本。

*lstColors*<br/>
[在]对 RGB 值列表的引用。

## <a name="cmfcribboncolorbuttonsetpalette"></a><a name="setpalette"></a>CMFC功能彩带按钮：：设置调色板

指定要在颜色按钮显示的颜色表中显示的标准颜色。

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>参数

*pPalette*<br/>
[在]指向调色板的指针。

### <a name="remarks"></a>备注

## <a name="cmfcribboncolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFC彩带颜色按钮：：更新颜色

当用户从用户单击颜色按钮时显示的颜色表中选择颜色时，由框架调用。

```cpp
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]用户选择的颜色。

### <a name="remarks"></a>备注

该方法`CMFCRibbonColorButton::UpdateColor`更改当前所选按钮的颜色，并通过发送带有BN_CLICKED标准通知的WM_COMMAND消息通知其父按钮。 使用[CMFC 功能色按钮：获取颜色](#getcolor)方法检索所选颜色。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery 类](../../mfc/reference/cmfcribbongallery-class.md)
