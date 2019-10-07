---
title: CMFCColorButton 类
ms.date: 11/04/2016
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
ms.openlocfilehash: ac49957f075f8798607535286d6c4518c0eeeeae
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505364"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton 类

`CMFCColorButton`和 [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) 类类一起用于实现颜色选取器控件。

## <a name="syntax"></a>语法

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|构造一个新`CMFCColorButton`的对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|启用和禁用定位在常规颜色按钮之上的 "自动" 按钮。 （标准系统自动按钮标记为 "**自动**"。）|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|启用和禁用 "其他" 按钮，该按钮位于常规颜色按钮的下方。 （标准系统 "其他" 按钮标记为 "**更多颜色**"。）|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|检索当前自动颜色。|
|[CMFCColorButton::GetColor](#getcolor)|检索按钮的颜色。|
|[CMFCColorButton::SetColor](#setcolor)|设置按钮的颜色。|
|[CMFCColorButton::SetColorName](#setcolorname)|设置颜色名称。|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|设置 "颜色选取器" 对话框中的列数。|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|指定在 "颜色选取器" 对话框中显示的文档特定颜色的列表。|
|[CMFCColorButton::SetPalette](#setpalette)|指定标准显示颜色的调色板。|
|[CMFCColorButton::SizeToContent](#sizetocontent)|更改按钮控件的大小，具体取决于其文本和图像大小。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|指示当前颜色按钮是否以 Windows XP 视觉样式显示。|
|[CMFCColorButton::OnDraw](#ondraw)|由框架调用以显示按钮的图像。|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|由框架调用以显示按钮的边框。|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|当按钮有焦点时，由框架调用以显示焦点矩形。|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|当要显示颜色选取器对话框时由框架调用。|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|将受`m_pPalette`保护的数据成员初始化为指定的调色板或默认系统调色板。|
|[CMFCColorButton::UpdateColor](#updatecolor)|当用户从颜色选取器对话框的调色板中选择颜色时，由框架调用。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|`m_bAltColorDlg`|布尔值。 如果为 TRUE，则在单击*其他*按钮时，框架会显示 " [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)颜色" 对话框，如果为 "FALSE"，则显示 "系统颜色" 对话框。 默认值为 TRUE。 有关详细信息，请参阅[CMFCColorButton：： EnableOtherButton](#enableotherbutton)。|
|`m_bAutoSetFocus`|布尔值。 如果为 TRUE，则在显示菜单时，框架会在颜色菜单上设置焦点; 如果为 FALSE，则不更改焦点。 默认值为 TRUE。|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|指示是否为颜色按钮启用了自定义模式。|
|`m_Color`|[COLORREF](/windows/win32/gdi/colorref)值。 包含当前选定的颜色。|
|`m_ColorAutomatic`|[COLORREF](/windows/win32/gdi/colorref)值。 包含当前选定的默认颜色。|
|`m_Colors`|[CArray](../../mfc/reference/carray-class.md)的[COLORREF](/windows/win32/gdi/colorref)值。 包含当前可用的颜色。|
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md)的[COLORREF](/windows/win32/gdi/colorref)值。 包含当前文档颜色。|
|`m_nColumns`|一个整数。 包含要在颜色选择菜单中的颜色网格中显示的列数。|
|`m_pPalette`|指向[CPalette](../../mfc/reference/cpalette-class.md)的指针。 包含 "当前颜色选择" 菜单中可用的颜色。|
|`m_pPopup`|指向[CMFCColorPopupMenu 类](../../mfc/reference/cmfccolorpopupmenu-class.md)对象的指针。 单击 "颜色" 按钮时显示的颜色选择菜单。|
|`m_strAutoColorText`|一个字符串。 颜色选择菜单中的 "自动" 按钮的标签。|
|`m_strDocColorsText`|一个字符串。 显示文档颜色的颜色选择菜单中的按钮的标签。|
|`m_strOtherText`|一个字符串。 颜色选择菜单中的 "其他" 按钮的标签。|

## <a name="remarks"></a>备注

默认情况下， `CMFCColorButton`类的行为方式为打开颜色选取器对话框的 "推送" 按钮。 "颜色选取器" 对话框包含一个小颜色按钮的数组和一个显示自定义颜色选取器的 "其他" 按钮。 （标准系统 "其他" 按钮标记为 "**更多颜色**"。）当用户选择新颜色时， `CMFCColorButton`对象将反映更改并显示所选颜色。

直接在代码中或通过使用**ClassWizard**工具和对话框模板创建颜色按钮控件。 如果直接创建颜色按钮控件，请向应用程序`CMFCColorButton`中添加一个变量，然后调用该`CMFCColorButton`对象的构造`Create`函数和方法。 如果使用**ClassWizard**，请在应用程序`CButton`中添加一个变量，然后将该变量的类型从`CButton`更改为`CMFCColorButton`。

当`OnLButtonDown`框架调用事件处理程序时，"颜色选取器" 对话框（ [CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)）由[CMFCColorButton：： OnShowColorPopup](#onshowcolorpopup)方法显示。 可以重写[CMFCColorButton：： OnShowColorPopup](#onshowcolorpopup)方法以支持自定义颜色选择。

`CMFCColorButton`对象通过向其发送 WM_COMMAND 通知其父项颜色正在更改 |BN_CLICKED 通知。 父代使用[CMFCColorButton：： GetColor](#getcolor)方法检索当前颜色。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCColorButton`类中的各种方法来配置颜色按钮。 方法设置颜色按钮及其列数的颜色，并启用 "自动" 和其他按钮。 此示例是[状态栏演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>要求

**标头：** afxcolorbutton

##  <a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton

构造一个新`CMFCColorButton`的对象。

```
CMFCColorButton();
```

##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton

启用或禁用颜色选取器控件的 "自动" 按钮，并设置自动（默认）颜色。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
中指定 "自动" 按钮的文本。

*colorAutomatic*<br/>
中指定自动按钮默认颜色的 RGB 值。

*bEnable*<br/>
中指定是否启用或禁用 "自动" 按钮。

### <a name="remarks"></a>备注

##  <a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton

启用或禁用 "其他" 按钮，该按钮显示在常规颜色按钮的下方。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
中指定按钮的文本。

*bAltColorDlg*<br/>
中指定当用户单击按钮时，是否打开 " [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) " 对话框或 "系统颜色" 对话框。

*bEnable*<br/>
中指定是否启用或禁用 "其他" 按钮。

### <a name="remarks"></a>备注

单击 "其他" 按钮以显示 "颜色" 对话框。 如果*bAltColorDlg*参数为 TRUE，则显示[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md);否则，会显示 "系统颜色" 对话框。

##  <a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor

检索当前自动（默认）颜色。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>返回值

表示当前自动颜色的 RGB 值。

### <a name="remarks"></a>备注

使用[CMFCColorButton：： EnableAutomaticButton](#enableautomaticbutton)方法设置当前自动颜色。

##  <a name="getcolor"></a>CMFCColorButton：： GetColor

检索当前选定的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

一个 RGB 值。

### <a name="remarks"></a>备注

##  <a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme

指示当前颜色按钮是否以 Windows XP 视觉样式显示。

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>返回值

如果支持视觉样式，并且当前颜色按钮以 Windows XP 的视觉样式显示，则为 TRUE;否则为 FALSE。

##  <a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode

将颜色按钮设置为自定义模式。

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>备注

如果需要将颜色按钮添加到自定义对话框页面（或者允许用户在自定义过程中进行其他颜色选择），请将该`m_bEnabledInCustomizeMode`成员设置为 TRUE 以启用该按钮。 默认情况下，此成员设置为 FALSE。

##  <a name="ondraw"></a>CMFCColorButton：： OnDraw

由框架调用，用于呈现按钮的图像。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向用于呈现按钮图像的设备上下文。

*rect*<br/>
中限定按钮的矩形。

*uiState*<br/>
中指定按钮的可视状态。

### <a name="remarks"></a>备注

重写此方法以自定义呈现过程。

##  <a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder

由框架调用以显示按钮的边框。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向用于绘制边框的设备上下文。

*rectClient*<br/>
中由*pDC*参数指定的设备上下文中的一个矩形，该参数定义要绘制的按钮的边界。

*uiState*<br/>
中指定按钮的可视状态。

### <a name="remarks"></a>备注

重写此函数以自定义颜色按钮的边框外观。

##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect

当按钮有焦点时，由框架调用以显示焦点矩形。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向用于绘制聚焦框的设备上下文。

*rectClient*<br/>
中由定义按钮边界的*pDC*参数指定的设备上下文中的矩形。

### <a name="remarks"></a>备注

重写此方法以自定义聚焦框的外观。

##  <a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup

在显示弹出项颜色栏之前调用。

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>备注

##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette

将受`m_pPalette`保护的数据成员初始化为指定的调色板或默认系统调色板。

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pPal*|中指向逻辑调色板或 NULL 的指针。 如果为 NULL，则使用默认系统调色板。|

##  <a name="setcolor"></a>CMFCColorButton::SetColor

指定按钮的颜色。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
中一个 RGB 值。

### <a name="remarks"></a>备注

##  <a name="setcolorname"></a>CMFCColorButton::SetColorName

指定颜色的名称。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>参数

*color*<br/>
中颜色的 RGB 值。

*strName*<br/>
中颜色的名称。

### <a name="remarks"></a>备注

颜色名称的列表是每个应用程序的全局名称。 因此，此方法会将其参数传输到[CMFCColorBar：： SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)。

##  <a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber

定义在用户颜色选择过程中向用户显示的颜色表中显示的列数。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>参数

*nColumns*<br/>
中指定列数。

### <a name="remarks"></a>备注

用户可从显示预定义颜色表的弹出颜色栏中选择一种颜色。 使用此方法定义表中的列数。

##  <a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors

指定一组颜色和集的名称。 使用[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象显示颜色集。

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
中指定要与文档颜色集一起显示的标签。

*lstColors*<br/>
中对 RGB 值的列表的引用。

### <a name="remarks"></a>备注

对象维护传输到[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象的 RGB 值的列表。 `CMFCColorButton` 当显示颜色栏时，这些颜色显示在特殊部分，其标签由*lpszLabel*参数指定。

##  <a name="setpalette"></a>CMFCColorButton::SetPalette

指定要在弹出项颜色栏上显示的标准颜色。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>参数

*pPalette*<br/>
中指向调色板的指针。

### <a name="remarks"></a>备注

##  <a name="sizetocontent"></a>CMFCColorButton：： System.windows.window.sizetocontent

调整按钮控件的大小以适合其文本和图像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>参数

*bCalcOnly*<br/>
中如果为非零值，则会计算按钮控件的新大小，但不会更改实际大小。

### <a name="return-value"></a>返回值

指定新按钮控件大小的对象。`CSize`

### <a name="remarks"></a>备注

##  <a name="updatecolor"></a>CMFCColorButton::UpdateColor

当用户在用户单击颜色按钮时显示的颜色栏中选择颜色时，由框架调用。

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
中用户选择的颜色。

### <a name="remarks"></a>备注

`UpdateColor`函数会更改当前选定的按钮颜色，并通过使用 BN_CLICKED 标准通知发送 WM_COMMAND 消息来通知其父项。 使用[CMFCColorButton：： GetColor](#getcolor)方法检索选定的颜色。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette 类](../../mfc/reference/cpalette-class.md)<br/>
[CArray 类](../../mfc/reference/carray-class.md)<br/>
[CList 类](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
