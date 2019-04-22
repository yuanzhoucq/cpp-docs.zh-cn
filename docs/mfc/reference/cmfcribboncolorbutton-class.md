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
ms.openlocfilehash: ceb686a9aca4ac126c4d61dd45975c65a9376ce9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769961"
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton 类

`CMFCRibbonColorButton` 类用于实现可添加到功能区栏的颜色按钮。 功能区颜色按钮显示包含一个或多个调色板的下拉菜单。

## <a name="syntax"></a>语法

```
class CMFCRibbonColorButton : public CMFCRibbonGallery
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|将一组颜色添加到常规颜色区域。|
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|指定是否启用  “自动”按钮。|
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|启用“其他”  按钮。|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFCRibbonColorButton::GetColor](#getcolor)|返回当前选定的颜色。|
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|返回在颜色栏上显示的颜色元素的大小。|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|返回调色板弹出窗口上当前选定的元素的颜色。|
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|删除常规颜色区域中所有颜色组。|
|[CMFCRibbonColorButton::SetColor](#setcolor)|选择常规颜色区域中的某种颜色。|
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|设置在颜色条上显示的所有颜色元素的大小。|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|指定要在文档颜色区域中显示的 RGB 值列表。|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>备注

功能区颜色按钮显示用户按下它时的颜色条。 默认情况下，此颜色条包含称为常规颜色区域的颜色选择调色板。 （可选）颜色条包含一个  “自动”按钮，该按钮允许用户选择默认颜色，以及包含一个“其他”  按钮，该按钮用于显示包含其他颜色的调色板弹出窗口。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCRibbonColorButton` 类中的各种方法。 该示例演示了如何构造 `CMFCRibbonColorButton` 对象、设置大图像、启用  “自动”按钮、启用  “其他”按钮、设置列数、设置颜色条上显示的所有颜色元素的大小、将一组颜色添加到常规彩色区域中以及指定要在文档颜色区域中显示的 RGB 值列表。 此代码片段属于 [Draw Client 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>要求

**标头:** afxribboncolorbutton.h

##  <a name="addcolorsgroup"></a>  CMFCRibbonColorButton::AddColorsGroup

将一组颜色添加到常规颜色区域。

```
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
[in]组名称。

*lstColors*<br/>
[in]颜色的列表。

*bContiguousColumns*<br/>
[in]控制颜色项组中的显示方式。 如果为 TRUE，而无需垂直间距绘制颜色项。 如果为 FALSE，颜色项绘制垂直间距。

### <a name="remarks"></a>备注

使用此函数会使颜色弹出窗口显示多个组的颜色。 您可以控制颜色组中的显示方式。

##  <a name="cmfcribboncolorbutton"></a>  CMFCRibbonColorButton::CMFCRibbonColorButton

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
[in]指定要在用户单击按钮时执行的命令的命令 ID。

*lpszText*<br/>
[in]指定要在按钮上显示的文本。

*nSmallImageIndex*<br/>
[in]要在按钮上显示的小图像的从零开始的索引。

*color*<br/>
[in]按钮 （默认为黑色） 颜色。

*bSimpleButtonLook*<br/>
[in]如果为 TRUE，该按钮被绘制为一个简单的矩形。

*nLargeImageIndex*<br/>
[in]要在按钮上显示的大型图像的从零开始的索引。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="enableautomaticbutton"></a>  CMFCRibbonColorButton::EnableAutomaticButton

指定是否启用  “自动”按钮。

```
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
[in]为标签**自动**按钮。

*colorAutomatic*<br/>
[in]RGB 值，该值指定**自动**按钮的默认颜色。

*bEnable*<br/>
[in]则为 TRUE**自动**按钮已启用;如果它处于禁用状态，则为 FALSE。

*lpszToolTip*<br/>
[in]工具提示**自动**按钮。

*bOnTop*<br/>
[in]指定是否**自动**按钮位于顶部之前的调色板。

*bDrawBorder*<br/>
[in]如果应用程序功能区颜色按钮上绘制边框颜色条，则为 TRUE。 颜色栏会显示当前选定的颜色。 如果应用程序不绘制边框，则为 FALSE

##  <a name="enableotherbutton"></a>  CMFCRibbonColorButton::EnableOtherButton

启用“其他”  按钮。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
按钮的标签。

*lpszToolTip*<br/>
工具提示文本**其他**按钮。

### <a name="remarks"></a>备注

**其他**按钮是颜色的组的下方显示的按钮。 当用户单击**其他**按钮，将显示一个颜色对话框。

##  <a name="getautomaticcolor"></a>  CMFCRibbonColorButton::GetAutomaticColor

检索当前的自动按钮颜色。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>返回值

一个表示当前自动按钮颜色的 RGB 颜色值。

### <a name="remarks"></a>备注

通过设置自动按钮颜色`colorAutomatic`参数传递给`CMFCRibbonColorButton::EnableAutomaticButton`方法。

##  <a name="getcolor"></a>  CMFCRibbonColorButton::GetColor

返回当前选定的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

通过单击按钮选择的颜色。

##  <a name="getcolorboxsize"></a>  CMFCRibbonColorButton::GetColorBoxSize

返回在颜色栏上显示的颜色元素的大小。

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>返回值

中的下拉颜色调色板的颜色按钮的大小。

##  <a name="getcolumns"></a>  CMFCRibbonColorButton::GetColumns

获取功能区颜色按钮库显示的某一行中的项数。

```
int GetColumns() const;
```

### <a name="return-value"></a>返回值

返回每个行中的图标数目。

### <a name="remarks"></a>备注

##  <a name="gethighlightedcolor"></a>  CMFCRibbonColorButton::GetHighlightedColor

返回当前所选元素的颜色上弹出的调色板。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>返回值

弹出颜色调色板上的当前所选元素的颜色。

##  <a name="removeallcolorgroups"></a>  CMFCRibbonColorButton::RemoveAllColorGroups

删除常规颜色区域中所有颜色组。

```
void RemoveAllColorGroups();
```

##  <a name="setcolor"></a>  CMFCRibbonColorButton::SetColor

选择常规颜色区域中的某种颜色。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
[in]要设置的颜色。

##  <a name="setcolorboxsize"></a>  CMFCRibbonColorButton::SetColorBoxSize

设置在颜色条上显示的所有颜色元素的大小。

```
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>参数

*sizeBox*<br/>
[in]新颜色调色板中的颜色按钮的大小。

##  <a name="setcolorname"></a>  CMFCRibbonColorButton::SetColorName

设置指定颜色的新名称。

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>参数

*color*<br/>
[in]一种颜色的 RGB 值。

*strName*<br/>
[in]指定颜色的新名称。

### <a name="remarks"></a>备注

因为它调用`CMFCColorBar::SetColorName`，此方法将更改在所有指定的颜色名称`CMFCColorBar`你的应用程序中的对象。

##  <a name="setcolumns"></a>  CMFCRibbonColorButton::SetColumns

设置显示在用户的颜色选择过程中向用户显示的颜色表中的列数。

```
void SetColumns(int nColumns);
```

### <a name="parameters"></a>参数

*nColumns*<br/>
[in]若要在每个行中显示的颜色图标的数。

### <a name="remarks"></a>备注

##  <a name="setdocumentcolors"></a>  CMFCRibbonColorButton::SetDocumentColors

指定要在文档颜色区域中显示的 RGB 值列表。

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[in]要与文档颜色显示的文本。

*lstColors*<br/>
[in]对的 RGB 值列表的引用。

##  <a name="setpalette"></a>  CMFCRibbonColorButton::SetPalette

指定要在颜色按钮显示的颜色表中显示的标准颜色。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>参数

*pPalette*<br/>
[in]指向调色板颜色的指针。

### <a name="remarks"></a>备注

##  <a name="updatecolor"></a>  CMFCRibbonColorButton::UpdateColor

当用户从用户单击颜色按钮时显示的颜色表中选择一种颜色，由框架调用。

```
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
[in]用户选定的颜色。

### <a name="remarks"></a>备注

`CMFCRibbonColorButton::UpdateColor`方法当前所选的按钮的颜色更改，并发送 WM_COMMAND 消息 BN_CLICKED 标准通知来通知其父级。 使用[CMFCRibbonColorButton::GetColor](#getcolor)方法来检索所选的颜色。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery 类](../../mfc/reference/cmfcribbongallery-class.md)
