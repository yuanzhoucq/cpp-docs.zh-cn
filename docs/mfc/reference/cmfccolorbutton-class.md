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
ms.openlocfilehash: cf24c162d0eda272f73c69c434589ae6ef3332a4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752559"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton 类

和`CMFCColorButton` [CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)一起使用以实现颜色选取器控件。

## <a name="syntax"></a>语法

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC颜色按钮：CMFC颜色按钮](#cmfccolorbutton)|构造新的 `CMFCColorButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC颜色按钮：：启用自动按钮](#enableautomaticbutton)|启用并禁用位于常规颜色按钮上方的"自动"按钮。 （标准系统自动按钮标记为**自动**.）|
|[CMFC颜色按钮：启用其他按钮](#enableotherbutton)|启用并禁用位于常规颜色按钮下方的"其他"按钮。 （标准系统"其他"按钮标记为**更多颜色**。|
|[CMFC颜色按钮：获取自动颜色](#getautomaticcolor)|检索当前自动颜色。|
|[CMFC颜色按钮：获取颜色](#getcolor)|检索按钮的颜色。|
|[CMFC颜色按钮：：设置颜色](#setcolor)|设置按钮的颜色。|
|[CMFC颜色按钮：：设置颜色名称](#setcolorname)|设置颜色名称。|
|[CMFC颜色按钮：：设置列数](#setcolumnsnumber)|设置颜色选取器对话框上的列数。|
|[CMFC颜色按钮：：设置文档颜色](#setdocumentcolors)|指定颜色选取器对话框中显示的特定于文档的颜色的列表。|
|[CMFC颜色按钮：：设置调色板](#setpalette)|指定标准显示颜色的调色板。|
|[CMFC颜色按钮：：大小到内容](#sizetocontent)|更改按钮控件的大小，具体取决于其文本和图像大小。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC颜色按钮：：是DrawXP主题](#isdrawxptheme)|指示当前颜色按钮是否以 Windows XP 的可视样式显示。|
|[CMFC颜色按钮：在画上](#ondraw)|由框架调用以显示按钮的图像。|
|[CMFC颜色按钮：：在绘制边框](#ondrawborder)|框架调用以显示按钮的边框。|
|[CMFC颜色按钮：：在DrawFocusrect上](#ondrawfocusrect)|当按钮具有焦点时，框架调用以显示焦点矩形。|
|[CMFC颜色按钮：：在显示颜色弹出](#onshowcolorpopup)|当颜色选取器对话框即将显示时，由框架调用。|
|[CMFC颜色按钮：：重建调色板](#rebuildpalette)|将`m_pPalette`受保护的数据成员初始化到指定的调色板或默认系统调色板。|
|[CMFCColorButton::UpdateColor](#updatecolor)|当用户从颜色选取器对话框的调色板中选择颜色时，由框架调用。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|`m_bAltColorDlg`|布尔值。 如果为 TRUE，则当单击*另一个*按钮或"FALSE"系统颜色对话框时，框架将显示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)颜色对话框。 默认值为 TRUE。 有关详细信息，请参阅[CMFCColorButton：：启用其他按钮](#enableotherbutton)。|
|`m_bAutoSetFocus`|布尔值。 如果为 TRUE，则框架在显示菜单时将焦点设置在颜色菜单上，或者如果 FALSE 不会更改焦点。 默认值为 TRUE。|
|[CMFC颜色按钮：：m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|指示颜色按钮是否已启用自定义模式。|
|`m_Color`|[颜色值](/windows/win32/gdi/colorref)。 包含当前选择的颜色。|
|`m_ColorAutomatic`|[颜色值](/windows/win32/gdi/colorref)。 包含当前选定的默认颜色。|
|`m_Colors`|[COLORREF](/windows/win32/gdi/colorref)值的[CArray。](../../mfc/reference/carray-class.md) 包含当前可用的颜色。|
|`m_lstDocColors`|[COLORREF](/windows/win32/gdi/colorref)值的[CList。](../../mfc/reference/clist-class.md) 包含当前文档颜色。|
|`m_nColumns`|一个整数。 包含要在颜色选择菜单中的颜色网格中显示的列数。|
|`m_pPalette`|指向[CPalette](../../mfc/reference/cpalette-class.md)的指针。 包含当前颜色选择菜单中可用的颜色。|
|`m_pPopup`|指向[CMFCColorPopupMenu 类](../../mfc/reference/cmfccolorpopupmenu-class.md)对象的指针。 单击颜色按钮时显示的颜色选择菜单。|
|`m_strAutoColorText`|一个字符串。 颜色选择菜单中"自动"按钮的标签。|
|`m_strDocColorsText`|一个字符串。 显示文档颜色的颜色选择菜单中按钮的标签。|
|`m_strOtherText`|一个字符串。 颜色选择菜单中"其他"按钮的标签。|

## <a name="remarks"></a>备注

默认情况下，`CMFCColorButton`类充当按钮，打开颜色选取器对话框。 颜色选取器对话框包含一系列小颜色按钮和显示自定义颜色选取器的"其他"按钮。 （标准系统"其他"按钮标记为**更多颜色**。当用户选择新颜色时，`CMFCColorButton`对象将反映更改并显示所选颜色。

直接在代码中创建颜色按钮控件，或者使用**ClassWizard**工具和对话框模板。 如果直接创建颜色按钮控件，请向应用程序添加`CMFCColorButton`变量，然后调用`Create``CMFCColorButton`对象的构造函数和方法。 如果使用**ClassWizard，** 请向应用程序添加`CButton`变量，然后将变量的类型从`CButton`更改为 。 `CMFCColorButton`

颜色选取器对话框 （ [CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)） 由[CMFCColorButton：：在](#onshowcolorpopup)框架调用`OnLButtonDown`事件处理程序时显示ColorPopup 方法显示。 [CMFCColorButton：可以重写显示颜色弹出](#onshowcolorpopup)方法以支持自定义颜色选择。

对象`CMFCColorButton`通过向其发送WM_COMMAND来通知其父对象颜色正在更改 |BN_CLICKED通知。 父级使用[CMFCColorButton：getColor](#getcolor)方法检索当前颜色。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCColorButton`类中的各种方法配置颜色按钮。 这些方法设置颜色按钮的颜色及其列数，并启用自动按钮和其他按钮。 此示例是[状态栏演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>要求

**标题：** afxcolor 按钮.h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a>CMFC颜色按钮：CMFC颜色按钮

构造新的 `CMFCColorButton` 对象。

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFC颜色按钮：：启用自动按钮

启用或禁用颜色选取器控件的"自动"按钮，并设置自动（默认）颜色。

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]指定自动按钮的文本。

*颜色 自动*<br/>
[在]指定自动按钮默认颜色的 RGB 值。

*b 启用*<br/>
[在]指定自动按钮是启用还是禁用。

### <a name="remarks"></a>备注

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFC颜色按钮：启用其他按钮

启用或禁用"其他"按钮，该按钮显示在常规颜色按钮下方。

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]指定按钮的文本。

*巴尔特·博拉尔德格*<br/>
[在]指定在用户单击该按钮时是否打开[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框或系统颜色对话框。

*b 启用*<br/>
[在]指定"其他"按钮是启用还是禁用。

### <a name="remarks"></a>备注

单击"其他"按钮可显示颜色对话框。 如果*bAltColorDlg*参数为 TRUE，则显示 CMFCColorDialog 类;如果 bAltColorDlg 参数为 TRUE，则显示[CMFCColorDialog 类](../../mfc/reference/cmfccolordialog-class.md);否则，将显示系统颜色对话框。

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFC颜色按钮：获取自动颜色

检索当前自动（默认）颜色。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>返回值

表示当前自动颜色的 RGB 值。

### <a name="remarks"></a>备注

当前自动颜色由[CMFCColorButton 设置：启用自动按钮](#enableautomaticbutton)方法。

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a>CMFC颜色按钮：获取颜色

检索当前选择的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

RGB 值。

### <a name="remarks"></a>备注

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a>CMFC颜色按钮：：是DrawXP主题

指示当前颜色按钮是否以 Windows XP 的可视样式显示。

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>返回值

如果支持视觉样式，并且当前颜色按钮以 Windows XP 的视觉样式显示，则为 TRUE;否则，FALSE。

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a>CMFC颜色按钮：：m_bEnabledInCustomizeMode

将颜色按钮设置为自定义模式。

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>备注

如果需要向自定义对话框的页面添加颜色按钮（或允许用户在自定义期间进行其他颜色选择），请通过将`m_bEnabledInCustomizeMode`成员设置为 TRUE 来启用该按钮。 默认情况下，此成员设置为 FALSE。

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a>CMFC颜色按钮：在画上

由框架调用以呈现按钮的图像。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向用于渲染按钮图像的设备上下文。

*矩形*<br/>
[在]绑定按钮的矩形。

*uiState*<br/>
[在]指定按钮的可视状态。

### <a name="remarks"></a>备注

重写此方法以自定义呈现过程。

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a>CMFC颜色按钮：：在绘制边框

框架调用以显示按钮的边框。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向用于绘制边框的设备上下文。

*rectClient*<br/>
[在]由*pDC*参数指定的设备上下文中的矩形，用于定义要绘制的按钮的边界。

*uiState*<br/>
[在]指定按钮的可视状态。

### <a name="remarks"></a>备注

重写此函数以自定义颜色按钮的边框外观。

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFC颜色按钮：：在DrawFocusrect上

当按钮具有焦点时，框架调用以显示焦点矩形。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向用于绘制焦点矩形的设备上下文。

*rectClient*<br/>
[在]由*pDC*参数指定的设备上下文中的矩形，用于定义按钮的边界。

### <a name="remarks"></a>备注

重写此方法以自定义焦点矩形的外观。

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a>CMFC颜色按钮：：在显示颜色弹出

在显示弹出颜色栏之前调用。

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>备注

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a>CMFC颜色按钮：：重建调色板

将`m_pPalette`受保护的数据成员初始化到指定的调色板或默认系统调色板。

```cpp
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pPal*|[在]指向逻辑调色板或 NULL 的指针。 如果为 NULL，则使用默认系统调色板。|

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a>CMFC颜色按钮：：设置颜色

指定按钮的颜色。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]RGB 值。

### <a name="remarks"></a>备注

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFC颜色按钮：：设置颜色名称

指定颜色的名称。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]颜色的 RGB 值。

*strName*<br/>
[在]颜色的名称。

### <a name="remarks"></a>备注

颜色名称列表是每个应用程序的全局名称。 因此，此方法将其参数传输到[CMFCColorBar：：setColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)。

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFC颜色按钮：：设置列数

定义在用户颜色选择过程中向用户显示的颜色表中显示的列数。

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>参数

*nColumns*<br/>
[在]指定列数。

### <a name="remarks"></a>备注

用户可以从显示预定义颜色表的弹出颜色栏中选择颜色。 使用此方法定义表中的列数。

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFC颜色按钮：：设置文档颜色

指定一组颜色和集的名称。 使用[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象显示颜色集。

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]指定要使用文档颜色集显示的标签。

*lstColors*<br/>
[在]对 RGB 值列表的引用。

### <a name="remarks"></a>备注

对象`CMFCColorButton`维护传输到[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)对象的 RGB 值的列表。 显示颜色栏时，这些颜色将显示在由*lpszLabel*参数指定的标签的特殊部分中。

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a>CMFC颜色按钮：：设置调色板

指定要在弹出颜色栏上显示的标准颜色。

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>参数

*pPalette*<br/>
[在]指向调色板的指针。

### <a name="remarks"></a>备注

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFC颜色按钮：：大小到内容

调整按钮控件的大小以适合其文本和图像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>参数

*bCalcOnly*<br/>
[在]如果为非零，则计算按钮控件的新大小，但不会更改实际大小。

### <a name="return-value"></a>返回值

指定`CSize`新按钮控件大小的对象。

### <a name="remarks"></a>备注

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFC颜色按钮：：更新颜色

当用户从用户单击颜色按钮时显示的颜色栏中选择颜色时，由框架调用。

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]用户选择的颜色。

### <a name="remarks"></a>备注

该`UpdateColor`函数更改当前选定的按钮的颜色，并通过发送带有BN_CLICKED标准通知的WM_COMMAND消息通知其父按钮。 使用[CMFCColorButton：getColor](#getcolor)方法检索所选颜色。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFC颜色按钮：：在显示颜色弹出](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette 类](../../mfc/reference/cpalette-class.md)<br/>
[CArray 类](../../mfc/reference/carray-class.md)<br/>
[CList 类](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
