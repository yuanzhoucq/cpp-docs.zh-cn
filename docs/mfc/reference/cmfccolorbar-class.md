---
title: CMFCColorBar 类
ms.date: 11/04/2016
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
ms.openlocfilehash: 4eee24eb93be446f6b4f2631b70736c13a02f45c
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771402"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar 类

`CMFCColorBar`类表示可以在文档或应用程序中选择颜色的停靠控件条。

## <a name="syntax"></a>语法

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|构造 `CMFCColorBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|计算所需包含颜色条控件上的按钮，然后调整这些按钮的位置的水平和垂直边距。|
|[CMFCColorBar::CreateControl](#createcontrol)|创建一个颜色条控制窗口，并将其附加到`CMFCColorBar`对象，并调整其大小控件以包含指定的调色板。|
|[CMFCColorBar::Create](#create)|创建颜色栏控件窗口，并将其附加到`CMFCColorBar`对象。|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|显示或隐藏的自动按钮。|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|启用或禁用显示一个对话框，使用户可以选择更多颜色。|
|[CMFCColorBar::GetColor](#getcolor)|检索当前选定的颜色。|
|[CMFCColorBar::GetCommandID](#getcommandid)|检索当前颜色栏控件的命令 ID。|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|检索表示的颜色按钮具有焦点，则颜色也就是说，该按钮是*热*。|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|检索的水平边距，即左侧或右侧的颜色单元格与客户端区域边界之间的空间。|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|检索是在顶部或底部颜色单元格和客户端区域边界之间的空间的垂直边距。|
|[CMFCColorBar::IsTearOff](#istearoff)|指示是否当前颜色栏可停靠。|
|[CMFCColorBar::SetColor](#setcolor)|设置当前选定的颜色。|
|[CMFCColorBar::SetColorName](#setcolorname)|设置指定颜色的新名称。|
|[CMFCColorBar::SetCommandID](#setcommandid)|设置颜色条控件的新命令 ID。|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|设置当前文档中使用颜色的列表。|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|设置水平边距，即左侧或右侧的颜色单元格与客户端区域边界之间的空间。|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|设置客户端区域边界的顶部或底部的颜色单元格之间空间的垂直边距。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|调整颜色条控件上的颜色按钮的位置。|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|指示是否可以更改颜色按钮的文本标签。|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|指示是否颜色栏控件对象可以出现在工具栏列表自定义过程。|
|[CMFCColorBar::CalcSize](#calcsize)|由框架作为布局计算过程的一部分调用。|
|[CMFCColorBar::CreatePalette](#createpalette)|初始化使用指定的颜色数组中的颜色的调色板。|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|计算行和颜色栏控件的网格中的列的数。|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|计算当前的颜色条显示其他用户界面元素，如所需的其他高度**其他**按钮、 文档颜色等。|
|[CMFCColorBar::InitColors](#initcolors)|初始化具有指定的调色板或系统默认调色板中颜色的颜色的数组。|
|[CMFCColorBar::OnKey](#onkey)|当用户按下键盘按钮时由框架调用。|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|由框架调用以关闭弹出框控件的层次结构。|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|由框架调用以启用或禁用用户界面控件的项的颜色条显示项之前。|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|将打开颜色对话框。|
|[CMFCColorBar::Rebuild](#rebuild)|完全重绘颜色栏控件。|
|[CMFCColorBar::SelectPalette](#selectpalette)|将指定的设备上下文的逻辑调色板设置为当前的颜色条控件的父按钮的调色板。|
|[CMFCColorBar::SetPropList](#setproplist)|集`m_pWndPropList`受保护的数据成员添加到属性网格控件的指定指针。|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|请求拥有要更新状态栏中的消息行的颜色条控件的框架窗口。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|`m_bInternal`|一个布尔字段，可确定是否处理鼠标事件。 通常情况下，此字段为 TRUE 和自定义模式为 FALSE 时，会处理鼠标事件。|
|`m_bIsEnabled`|一个布尔值，该值指示是否已启用控件。|
|`m_bIsTearOff`|一个布尔值，该值指示是否为颜色条控件支持停靠。|
|`m_BoxSize`|一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，它指定颜色条网格中的单元格的大小。|
|`m_bShowDocColorsWhenDocked`|一个布尔值，该值指示是否停靠在颜色栏时显示文档的颜色。 有关详细信息，请参阅[CMFCColorBar::SetDocumentColors](#setdocumentcolors)。|
|`m_bStdColorDlg`|一个布尔值，该值指示是否显示标准系统颜色对话框中或[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框。 有关详细信息，请参阅[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|
|`m_ColorAutomatic`|一个[COLORREF](/windows/desktop/gdi/colorref)用于存储当前的自动颜色。 有关详细信息，请参阅[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md)对象关联一组的 RGB 颜色与它们的名称。|
|`m_colors`|一个[CArray](../../mfc/reference/carray-class.md)的[COLORREF](/windows/desktop/gdi/colorref)包含颜色条在控件中显示的颜色的值。|
|`m_ColorSelected`|一个[COLORREF](/windows/desktop/gdi/colorref)值，它是用户当前已选择从颜色栏控件的颜色。|
|`m_lstDocColors`|一个[CList](../../mfc/reference/clist-class.md)的[COLORREF](/windows/desktop/gdi/colorref)包含当前文档中使用的颜色的值。|
|`m_nCommandID`|无符号的整数的颜色按钮的命令 id。|
|`m_nHorzMargin`|一个整数，表示在网格中的颜色的颜色按钮之间的水平间距。|
|`m_nHorzOffset`|一个整数，表示为中心的颜色按钮的水平偏移量。 此值非常重要，如果该按钮显示的文本或图像除了一种颜色。|
|`m_nNumColumns`|一个整数，表示颜色的颜色条控制网格中的列数。|
|`m_nNumColumnsVert`|为垂直方向的颜色的网格中的列数的整数。|
|`m_nNumRowsHorz`|一个整数，表示水平方向的颜色的网格中的列数。|
|`m_nRowHeight`|一个整数，表示在网格中的颜色的颜色按钮的行的高度。|
|`m_nVertMargin`|一个整数，表示在网格中的颜色的颜色按钮之间的垂直边距。|
|`m_nVertOffset`|一个整数，表示为中心的颜色按钮的垂直偏移量。 此值非常重要，如果该按钮显示的文本或图像除了一种颜色。|
|`m_Palette`|一个[CPalette](../../mfc/reference/cpalette-class.md)颜色栏控件中使用的颜色。|
|`m_pParentBtn`|一个指向[CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)是当前的按钮的父对象。 如果颜色按钮的工具栏上的控件层次结构中或在颜色属性网格控件中，此值是重要的。|
|`m_pParentRibbonBtn`|一个指向[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)对象，功能区上并为当前按钮的父按钮。 如果颜色按钮的工具栏上的控件层次结构中或在颜色属性网格控件中，此值是重要的。|
|`m_pWndPropList`|一个指向[CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)对象。|
|`m_strAutoColor`|一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示显示的文本**自动**按钮。 有关详细信息，请参阅[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)。|
|`m_strDocColors`|一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示文档的颜色按钮显示的文本。 有关详细信息，请参阅[CMFCColorBar::SetDocumentColors](#setdocumentcolors)。|
|`m_strOtherColor`|一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示显示的文本*其他*按钮。 有关详细信息，请参阅[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|

## <a name="remarks"></a>备注

通常情况下，未创建`CMFCColorBar`直接对象。 相反， [CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)（在菜单和工具栏中使用） 或[CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)创建`CMFCColorBar`对象。

`CMFCColorBar`类提供了以下功能：

- 自动调整文档颜色的列表。

- 保存并还原其状态，以及文档状态。

- 管理"自动"按钮。

- 使用[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)控件以选择自定义颜色。

- 支持"分离"状态 (如果使用创建[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md))。

若要将合并`CMFCColorBar`功能集成到你的应用程序：

1. 创建一个常规菜单按钮，并将其分配一个 ID，例如 ID_CHAR_COLOR。

1. 在框架窗口类中，重写[CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)方法将替换为常规菜单与按钮[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)对象 (通过调用[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton))。

1. 设置的所有样式以及启用或禁用的功能`CMFCColorBar`对象在过程[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)创建。 `CMFCColorMenuButton`对象动态创建`CMFCColorBar`framework 调用后的对象`CreatePopupMenu`方法。

当用户单击颜色栏控件按钮时，则框架将使用`ON_COMMAND`宏，以通知颜色栏控件的父级。 在宏，命令 ID 参数是分配给在步骤 1 (在此示例中 ID_CHAR_COLOR) 中的颜色条控制按钮的值。 有关详细信息，请参阅[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)， [CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)， [CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)， [CFrameWndEx 类](../../mfc/reference/cframewndex-class.md)，并[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)类。

## <a name="example"></a>示例

下面的示例演示如何使用各种方法中的配置颜色条`CMFCColorBar`类。 方法设置水平和垂直边距，启用其他按钮、 创建颜色栏控件窗口中，并设置当前选定的颜色。 此示例摘自[新的控件示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>要求

**标头：** afxcolorbar.h

##  <a name="adjustlocations"></a>  CMFCColorBar::AdjustLocations

调整颜色条控件上的颜色按钮的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>备注

WM_SIZE 消息处理过程由框架调用此方法。

##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels

指示是否可以更改颜色按钮的文本标签。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>返回值

始终为 FALSE。

### <a name="remarks"></a>备注

默认情况下，此方法始终返回 FALSE，这意味着不能修改文本标签。 重写此方法以允许修改文本标签。

##  <a name="allowshowonlist"></a>  CMFCColorBar::AllowShowOnList

指示是否颜色栏控件对象可以出现在工具栏列表自定义过程。

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>返回值

始终为 TRUE。

### <a name="remarks"></a>备注

默认情况下，此方法始终返回 TRUE，这意味着该框架可以在自定义过程中显示的颜色条控件。 重写此方法来实现不同的行为。

##  <a name="calcsize"></a>  CMFCColorBar::CalcSize

由框架作为布局计算过程的一部分调用。

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>参数

*bVertDock*<br/>
[in]若要指定颜色栏控件垂直; 停靠，则返回 TRUE如果为 FALSE，以指定颜色栏控件时水平停靠。

### <a name="return-value"></a>返回值

在颜色栏控件中的颜色按钮的数组的大小。

##  <a name="cmfccolorbar"></a>  CMFCColorBar::CMFCColorBar

构造 `CMFCColorBar` 对象。

```
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    int nRowsDockHorz,
    int nColDockVert,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCColorButton* pParentBtn);

CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCRibbonColorButton* pParentRibbonBtn);

CMFCColorBar(
    CMFCColorBar& src,
    UINT uiCommandID);
```

### <a name="parameters"></a>参数

*colors*<br/>
[in]框架在颜色栏控件显示的颜色的数组。

*color*<br/>
[in]最初选定的颜色。

*lpszAutoColor*<br/>
[in]文本标签*自动*（默认值） 颜色按钮，则为 NULL。

标准标签为自动按钮**自动**。

*lpszOtherColor*<br/>
[in]文本标签*其他*按钮，其中显示更多颜色选项，则为 NULL。

其他按钮的标准标签**更多颜色...**.

*lpszDocColors*<br/>
[in]文档颜色按钮的文本标签。 文档颜色调色板，列出所有的文档当前使用的颜色。

*lstDocColors*<br/>
[in]文档当前使用的颜色的列表。

*nColumns*<br/>
[in]颜色数组具有的列数。

*nRowsDockHorz*<br/>
[in]颜色栏中的水平停靠时的行数。

*nColDockVert*<br/>
[in]颜色栏中的垂直停靠时的列数。

*colorAutomatic*<br/>
[in]在框架应用单击自动按钮时的默认颜色。

*nCommandID*<br/>
[in]颜色条控制命令 id。

*pParentBtn*<br/>
[in]指向父按钮的指针。

*src*<br/>
[in]将现有`CMFCColorBar`对象复制到新`CMFCColorBar`对象。

*uiCommandID*<br/>
[in]命令 id。

##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize

计算的垂直和水平边距的所需包含在颜色栏控件上的按钮和调整这些按钮的位置。

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*bSquareButtons*|[in]以指定颜色条控件上按钮的形状的正方形;，则返回 TRUE否则为 FALSE。 默认值为 TRUE。|
|*bCenterButtons*|[in]为 TRUE，则指定的颜色条控件按钮的表面上的内容居中;否则为 FALSE。 默认值为 TRUE。|

### <a name="remarks"></a>备注

##  <a name="create"></a>  CMFCColorBar::Create

创建颜色栏控件窗口，并将其附加到`CMFCColorBar`对象。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID,
    CPalette* pPalette=NULL,
    int nColumns=0,
    int nRowsDockHorz=0,
    int nColDockVert=0);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
[in]向父窗口的指针。

*dwStyle*<br/>
[in]按位组合 (OR) 的[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*nID*<br/>
[in]命令 id。

*pPalette*<br/>
[in]指向颜色的调色板。 默认值为 NULL。

*nColumns*<br/>
[in]在颜色栏控件中的列数。 默认值为 0。

*nRowsDockHorz*<br/>
[in]颜色栏控件时水平停靠中的行数。 默认值为 0。

*nColDockVert*<br/>
[in]垂直停靠时在颜色栏控件中的列数。 默认值为 0。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

若要构造`CMFCColorBar`对象，请调用类构造函数，则此方法。 `Create`方法创建 Windows 控件，并初始化颜色的列表。

##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl

创建一个颜色条控制窗口，并将其附加到`CMFCColorBar`对象，并调整控件窗口以包含指定的调色板。

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
[in]向父窗口的指针。 不能为 NULL。

*rect*<br/>
[in]指定位置绘制颜色栏控件边界矩形。

*nID*<br/>
[in]控件 id。

*nColumns*<br/>
[in]理想的颜色条控件中的列数。 此方法修改该数字以适应指定的调色板的颜色。 默认值为-1，表示未指定此参数。

*pPalette*<br/>
[in]指向调色板的颜色，则为 NULL 指针。 如果此参数为 NULL，此方法将如同 20 颜色指定计算颜色栏控件的大小。 默认值为 NULL。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用*rect*， *nColumns*，并*pPalette*参数来计算相应的行数和颜色栏控件，然后调用中的列[CMFCColorBar::Create](#create)方法。

##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette

初始化使用指定的颜色数组中的颜色的调色板。

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*arColors*|[in]一个颜色数组。|
|*palette*|[in]颜色的调色板。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

##  <a name="enableautomaticbutton"></a>  CMFCColorBar::EnableAutomaticButton

显示或隐藏的自动按钮。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[in]文本标签*自动*（默认值） 颜色按钮，则为 NULL。

标准标签为自动按钮**自动**。

*colorAutomatic*<br/>
[in]在框架应用单击自动按钮时的默认颜色。

*bEnable*<br/>
[in]为 TRUE，则启用自动按钮;如果为 FALSE 来禁用自动按钮。 默认值为 TRUE。

### <a name="remarks"></a>备注

如果删除的自动按钮的文本标签*lpszLabel*参数为 NULL 或*bEnable*参数为 FALSE。

##  <a name="enableotherbutton"></a>  CMFCColorBar::EnableOtherButton

启用或禁用显示一个对话框，使用户可以选择更多颜色。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[in]文本标签*其他*按钮，其中显示更多颜色选项，则为 NULL。

此按钮的标准标签**更多颜色...**.

*bAltColorDlg*<br/>
[in]为 true，则显示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框;如果为 FALSE，显示标准[CColorDialog](../../mfc/reference/ccolordialog-class.md)对话框。 默认值为 TRUE。

*bEnable*<br/>
[in]为 TRUE，则启用该按钮;如果为 FALSE 禁用该按钮。 默认值为 TRUE。

##  <a name="getcolor"></a>  CMFCColorBar::GetColor

检索当前选定的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

当前选定的颜色。

##  <a name="getcolorgridsize"></a>  CMFCColorBar::GetColorGridSize

计算行和颜色栏控件的网格中的列的数。

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*bVertDock*|[in]为 TRUE，则为垂直停靠的颜色栏控件，则执行计算否则，为水平停靠控件执行计算。|

### <a name="return-value"></a>返回值

一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，其`cx`组件包含的列和它的数`cy`组件包含的行数。

##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID

检索当前颜色栏控件的命令 ID。

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>返回值

命令 id。

### <a name="remarks"></a>备注

当用户选择一种新颜色时，framework 发送 WM_COMMAND 消息来通知父级的命令 ID`CMFCColorBar`对象。

##  <a name="getextraheight"></a>  CMFCColorBar::GetExtraHeight

计算当前的颜色条显示其他用户界面元素，如所需的其他高度**其他**按钮或文档的颜色。

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*nNumColumns*|[in]如果颜色栏控件包含文档颜色，要在文档颜色的网格中显示的列数。 否则，不使用此值。|

### <a name="return-value"></a>返回值

需要计算额外高度。

##  <a name="gethighlightedcolor"></a>  CMFCColorBar::GetHighlightedColor

检索表示的颜色按钮具有焦点，则颜色也就是说，该按钮是*热*。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>返回值

RGB 值。

### <a name="remarks"></a>备注

##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin

检索的水平边距，即左侧或右侧的颜色单元格与客户端区域边界之间的空间。

```
int GetHorzMargin();
```

### <a name="return-value"></a>返回值

水平边距。

##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin

检索是在顶部或底部颜色单元格和客户端区域边界之间的空间的垂直边距。

```
int GetVertMargin() const;
```

### <a name="return-value"></a>返回值

垂直边距。

##  <a name="initcolors"></a>  CMFCColorBar::InitColors

初始化一个使用中的指定调色板的颜色或使用系统默认调色板颜色数组。

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pPalette*|[in]调色板对象，或为 NULL 指针。 如果此参数为 NULL，则此方法使用的操作系统默认调色板。|
|*arColors*|[in]一个颜色数组。|

### <a name="return-value"></a>返回值

颜色数组中的元素数。

##  <a name="istearoff"></a>  CMFCColorBar::IsTearOff

指示是否当前颜色栏可停靠。

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>返回值

如果当前颜色栏控件是可停靠; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果颜色栏控件是可停靠，它可以拉出的控件条和停靠在另一个位置。

##  <a name="onkey"></a>  CMFCColorBar::OnKey

当用户按下键盘按钮时由框架调用。

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>参数

*nChar*<br/>
[in]用户按下键的虚拟键代码。

### <a name="return-value"></a>返回值

如果此方法处理指定的键; 则为 TRUE否则为 FALSE。

##  <a name="onsendcommand"></a>  CMFCColorBar::OnSendCommand

由框架调用以关闭弹出窗口控件的层次结构。

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pButton*|[in]指向驻留在工具栏的控件。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

##  <a name="onupdatecmdui"></a>  CMFCColorBar::OnUpdateCmdUI

由框架调用以启用或禁用用户界面控件的项的颜色条显示项之前。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>参数

*pTarget*<br/>
[in]指向一个窗口，其中包含要更新的用户界面项的指针。

*bDisableIfNoHndler*<br/>
[in]若要禁用的用户界面项，如果在消息映射; 中不定义任何处理程序，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

当应用程序的用户单击用户界面项时，该项必须知道是否应显示为已启用或禁用。 命令消息的目标来实现 ON_UPDATE_COMMAND_UI 命令处理程序提供此信息。 使用此方法以帮助处理命令。 有关详细信息，请参阅[CCmdUI 类](../../mfc/reference/ccmdui-class.md)。

##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog

将打开颜色对话框。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>参数

*colorDefault*<br/>
[in]颜色对话框打开时，默认情况下选择颜色。

*colorRes*<br/>
[out]用户选择了颜色。

### <a name="return-value"></a>返回值

如果用户选择某种颜色，则为 TRUE如果用户取消了颜色对话框中，则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="rebuild"></a>  CMFCColorBar::Rebuild

完全重绘颜色栏控件。

```
virtual void Rebuild();
```

##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette

将指定的设备上下文的逻辑调色板设置为当前的颜色条控件的父按钮的调色板。

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pDC*|[in]指向当前颜色栏控件的父按钮的设备上下文指针。|

### <a name="return-value"></a>返回值

指向将替换为当前的颜色条控件的父按钮的调色板的调色板。

##  <a name="setcolor"></a>  CMFCColorBar::SetColor

设置当前选定的颜色。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
[in]RGB 颜色值。

##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName

设置指定颜色的新名称。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>参数

*color*<br/>
[in]一种颜色的 RGB 值。

*strName*<br/>
[in]指定颜色的新名称。

### <a name="remarks"></a>备注

此方法将更改在所有指定的颜色名称`CMFCColorBar`你的应用程序中的对象。

##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID

设置颜色条控件的新命令 ID。

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>参数

*nCommandID*<br/>
[in]命令 id。

### <a name="remarks"></a>备注

调用此方法来修改颜色栏控件的命令 ID 以及通知的 ID 已更改的控件的父窗口。

##  <a name="setdocumentcolors"></a>  CMFCColorBar::SetDocumentColors

设置当前文档中使用颜色的列表。

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>参数

*lpszCaption*<br/>
[in]颜色栏控件未停靠时，将显示标题。

*lstDocColors*<br/>
[in]将替换当前文档颜色的颜色列表。

*bShowWhenDocked*<br/>
[in]若要显示文档的颜色，颜色栏控件停靠; 时，则返回 TRUE否则为 FALSE。 默认值是 FALSE。

### <a name="remarks"></a>备注

*文档颜色*是当前文档中使用的颜色。 框架会自动维护文档颜色的列表，但可以使用此方法可以修改的列表。

##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin

设置水平边距，即左侧或右侧的颜色单元格与客户端区域的边界之间的空间。

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>参数

*nHorzMargin*<br/>
[in]水平边距，以像素为单位。

### <a name="remarks"></a>备注

默认情况下[CMFCColorBar::CMFCColorBar](#cmfccolorbar)构造函数设置的水平边距为 4 个像素。

##  <a name="setproplist"></a>  CMFCColorBar::SetPropList

集`m_pWndPropList`受保护的数据成员添加到属性网格控件的指定指针。

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pWndList*|[in]为属性网格控件对象的指针。|

##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin

设置客户端区域边界的顶部或底部的颜色单元格之间空间的垂直边距。

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>参数

*nVertMargin*<br/>
[in]垂直边距，以像素为单位。

### <a name="remarks"></a>备注

默认情况下[CMFCColorBar::CMFCColorBar](#cmfccolorbar)构造函数设置的垂直边距为 4 个像素。

##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString

请求拥有要更新状态栏中的消息行的颜色条控件的框架窗口。

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>参数

*uiCmdId*<br/>
[in]命令 id。 （忽略此参数。）

### <a name="remarks"></a>备注

此方法将 WM_SETMESSAGESTRING 消息发送到颜色栏控件的所有者。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
