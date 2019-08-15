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
ms.openlocfilehash: 25bfe3ef67fcca7708179d1a316af05b3ba49dda
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505434"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar 类

`CMFCColorBar`类表示可选择文档或应用程序中的颜色的停靠控件条。

## <a name="syntax"></a>语法

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|name|描述|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|构造 `CMFCColorBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|计算在颜色栏控件上包含按钮并调整这些按钮的位置所需的垂直和水平边距。|
|[CMFCColorBar::CreateControl](#createcontrol)|创建一个颜色栏控件窗口, 将其附加到`CMFCColorBar`对象, 并调整控件的大小以包含指定的颜色调色板。|
|[CMFCColorBar::Create](#create)|创建一个颜色栏控件窗口, 并将其附加`CMFCColorBar`到对象。|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|显示或隐藏 "自动" 按钮。|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|启用或禁用允许用户选择更多颜色的对话框显示。|
|[CMFCColorBar::GetColor](#getcolor)|检索当前选定的颜色。|
|[CMFCColorBar::GetCommandID](#getcommandid)|检索当前颜色栏控件的命令 ID。|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|检索表示颜色按钮有焦点的颜色;也就是说, 按钮是*热*的。|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|检索水平边距, 即左或右两个颜色单元格与工作区边界之间的间距。|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|检索垂直边距, 即上、下颜色单元格与工作区边界之间的间距。|
|[CMFCColorBar::IsTearOff](#istearoff)|指示当前颜色栏是否可停靠。|
|[CMFCColorBar::SetColor](#setcolor)|设置当前选定的颜色。|
|[CMFCColorBar::SetColorName](#setcolorname)|为指定的颜色设置新名称。|
|[CMFCColorBar::SetCommandID](#setcommandid)|为颜色栏控件设置新的命令 ID。|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|设置在当前文档中使用的颜色的列表。|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|设置水平边距, 这是左或右两个颜色单元格与工作区边界之间的空间。|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|设置垂直边距, 即上、下颜色单元格与工作区边界之间的间距。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|调整颜色栏控件上颜色按钮的位置。|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|指示颜色按钮的文本标签是否可以更改。|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|指示在自定义过程中, 颜色栏控件对象是否可以出现在工具栏列表中。|
|[CMFCColorBar::CalcSize](#calcsize)|由框架作为布局计算过程的一部分进行调用。|
|[CMFCColorBar::CreatePalette](#createpalette)|使用指定颜色数组中的颜色初始化调色板。|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|计算颜色栏控件网格中的行数和列数。|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|计算当前颜色条显示其他用户界面元素 (如**其他**按钮、文档颜色等) 所需的附加高度。|
|[CMFCColorBar::InitColors](#initcolors)|用指定调色板或系统默认调色板中的颜色初始化颜色数组。|
|[CMFCColorBar::OnKey](#onkey)|当用户按下键盘按钮时由框架调用。|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|由框架调用以关闭 popup 控件的层次结构。|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|由框架调用, 以在显示项之前启用或禁用颜色栏控件的用户界面项。|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|打开 "颜色" 对话框。|
|[CMFCColorBar::Rebuild](#rebuild)|完全重绘颜色栏控件。|
|[CMFCColorBar::SelectPalette](#selectpalette)|将指定设备上下文的逻辑调色板设置为当前颜色条控件的父按钮的调色板。|
|[CMFCColorBar::SetPropList](#setproplist)|将受`m_pWndPropList`保护的数据成员设置为指向属性网格控件的指定指针。|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|请求拥有颜色条控件的框架窗口, 以更新状态栏中的消息行。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|`m_bInternal`|确定是否处理鼠标事件的布尔型字段。 通常, 当此字段为 TRUE 且自定义模式为 FALSE 时, 将处理鼠标事件。|
|`m_bIsEnabled`|指示控件是否已启用的布尔值。|
|`m_bIsTearOff`|指示颜色栏控件是否支持停靠的布尔值。|
|`m_BoxSize`|一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象, 该对象指定颜色条网格中的单元格的大小。|
|`m_bShowDocColorsWhenDocked`|指示是否在停靠颜色栏时显示文档颜色的布尔值。 有关详细信息, 请参阅[CMFCColorBar:: SetDocumentColors](#setdocumentcolors)。|
|`m_bStdColorDlg`|一个布尔值, 指示是显示标准系统颜色对话框还是显示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框。 有关详细信息, 请参阅[CMFCColorBar:: EnableOtherButton](#enableotherbutton)。|
|`m_ColorAutomatic`|存储当前自动颜色的[COLORREF](/windows/win32/gdi/colorref) 。 有关详细信息, 请参阅[CMFCColorBar:: EnableOtherButton](#enableotherbutton)。|
|`m_ColorNames`|一个[CMap](../../mfc/reference/cmap-class.md)对象, 它将一组 RGB 颜色与其名称关联。|
|`m_colors`|[COLORREF](/windows/win32/gdi/colorref)值的[CArray](../../mfc/reference/carray-class.md) , 其中包含颜色栏控件中显示的颜色。|
|`m_ColorSelected`|[COLORREF](/windows/win32/gdi/colorref)值, 是用户当前从颜色栏控件中选择的颜色。|
|`m_lstDocColors`|[COLORREF](/windows/win32/gdi/colorref)值的[CList](../../mfc/reference/clist-class.md) , 其中包含文档中当前使用的颜色。|
|`m_nCommandID`|一个无符号整数, 它是颜色按钮的命令 ID。|
|`m_nHorzMargin`|一个整数, 它是颜色网格中颜色按钮之间的水平边距。|
|`m_nHorzOffset`|一个整数, 它是颜色按钮中心的水平偏移量。 如果按钮除颜色之外显示文本或图像, 则此值很重要。|
|`m_nNumColumns`|一个整数, 它是颜色的颜色栏控件网格中的列数。|
|`m_nNumColumnsVert`|一个整数, 它是以垂直方向的颜色网格中的列数。|
|`m_nNumRowsHorz`|一个整数, 它是以水平方向的颜色网格中的列数。|
|`m_nRowHeight`|一个整数, 它是颜色网格中的颜色按钮行的高度。|
|`m_nVertMargin`|一个整数, 它是颜色网格中颜色按钮之间的垂直边距。|
|`m_nVertOffset`|一个整数, 它是颜色按钮中心的垂直偏移量。 如果按钮除颜色之外显示文本或图像, 则此值很重要。|
|`m_Palette`|颜色栏控件中使用的颜色的[CPalette](../../mfc/reference/cpalette-class.md) 。|
|`m_pParentBtn`|指向[CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)对象的指针, 该对象是当前按钮的父对象。 如果 "颜色" 按钮在工具栏控件的层次结构中或在颜色属性网格控件中, 则此值很重要。|
|`m_pParentRibbonBtn`|指向[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)对象的指针, 该对象位于功能区上, 是当前按钮的父按钮。 如果 "颜色" 按钮在工具栏控件的层次结构中或在颜色属性网格控件中, 则此值很重要。|
|`m_pWndPropList`|指向[CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)对象的指针。|
|`m_strAutoColor`|一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) , 它是在 "**自动**" 按钮上显示的文本。 有关详细信息, 请参阅[CMFCColorBar:: EnableAutomaticButton](#enableautomaticbutton)。|
|`m_strDocColors`|一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) , 它是在 "文档颜色" 按钮上显示的文本。 有关详细信息, 请参阅[CMFCColorBar:: SetDocumentColors](#setdocumentcolors)。|
|`m_strOtherColor`|一个[CString](../../atl-mfc-shared/reference/cstringt-class.md) , 它是在*另*一个按钮上显示的文本。 有关详细信息, 请参阅[CMFCColorBar:: EnableOtherButton](#enableotherbutton)。|

## <a name="remarks"></a>备注

通常不会直接创建`CMFCColorBar`对象。 相反, [CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)(用于菜单和工具栏) 或[CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)将创建`CMFCColorBar`对象。

`CMFCColorBar`类提供以下功能:

- 自动调整文档颜色的列表。

- 保存并还原其状态, 以及文档状态。

- 管理 "自动" 按钮。

- 使用[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)控件选择自定义颜色。

- 支持 "拆卸" 状态 (如果是使用[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)创建的)。

将`CMFCColorBar`功能合并到应用程序中:

1. 创建一个常规菜单按钮并为其分配 ID, 例如 ID_CHAR_COLOR。

1. 在框架窗口类中, 重写[CFrameWndEx:: OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)方法, 并将常规菜单按钮替换为[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)对象 (通过调用[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton))。

1. 设置所有样式, 并在创建[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)期间启用或`CMFCColorBar`禁用对象的功能。 在`CMFCColorMenuButton`框架调用方法`CreatePopupMenu`后`CMFCColorBar` , 对象动态创建对象。

用户单击颜色栏控件按钮时, 框架将使用`ON_COMMAND`宏来通知颜色栏控件的父级。 在宏中, 命令 ID 参数是您在步骤1中分配给颜色栏控件按钮的值 (在本示例中为 ID_CHAR_COLOR)。 有关详细信息, 请参阅[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)、 [CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)、 [CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)、 [CFrameWndEx 类](../../mfc/reference/cframewndex-class.md)和[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)。

## <a name="example"></a>示例

下面的示例演示如何使用类中的`CMFCColorBar`各种方法来配置颜色条。 方法设置水平和垂直边距, 启用 "其他" 按钮, 创建颜色栏控件窗口, 并设置当前选定的颜色。 此示例是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

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

**标头:** afxcolorbar

##  <a name="adjustlocations"></a>CMFCColorBar:: AdjustLocations

调整颜色栏控件上颜色按钮的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>备注

在 WM_SIZE 消息处理期间, 框架将调用此方法。

##  <a name="allowchangetextlabels"></a>CMFCColorBar:: AllowChangeTextLabels

指示颜色按钮的文本标签是否可以更改。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>返回值

始终为 FALSE。

### <a name="remarks"></a>备注

默认情况下, 此方法始终返回 FALSE, 这意味着不能修改文本标签。 重写此方法以启用修改文本标签。

##  <a name="allowshowonlist"></a>CMFCColorBar:: AllowShowOnList

指示在自定义过程中, 颜色栏控件对象是否可以出现在工具栏列表中。

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>返回值

始终为 TRUE。

### <a name="remarks"></a>备注

默认情况下, 此方法始终返回 TRUE, 这意味着在自定义过程中, 框架可以显示颜色栏控件。 重写此方法以实现其他行为。

##  <a name="calcsize"></a>CMFCColorBar:: CalcSize

由框架作为布局计算过程的一部分进行调用。

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>参数

*bVertDock*<br/>
中若要指定垂直停靠颜色栏控件, 则为 TRUE;若为 FALSE, 则指定颜色栏控件水平停靠。

### <a name="return-value"></a>返回值

颜色栏控件中颜色按钮的数组大小。

##  <a name="cmfccolorbar"></a>CMFCColorBar:: CMFCColorBar

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

*颜色*<br/>
中框架在颜色栏控件上显示的颜色数组。

*color*<br/>
中初始选择的颜色。

*lpszAutoColor*<br/>
中"*自动*(默认)" 颜色按钮的文本标签, 或为 NULL。

"自动" 按钮的标准标签为 "**自动**"。

*lpszOtherColor*<br/>
中"*其他*" 按钮的文本标签, 可显示更多颜色选项, 或为 NULL。

"其他" 按钮的标准标签为 "其他**颜色 ...** "。

*lpszDocColors*<br/>
中"文档颜色" 按钮的文本标签。 "文档颜色" 调色板列出了文档当前使用的所有颜色。

*lstDocColors*<br/>
中文档当前使用的颜色的列表。

*nColumns*<br/>
中颜色数组具有的列数。

*nRowsDockHorz*<br/>
中颜色栏水平停靠时的行数。

*nColDockVert*<br/>
中颜色栏垂直停靠时所具有的列数。

*colorAutomatic*<br/>
中单击 "自动" 按钮时, 框架应用的默认颜色。

*nCommandID*<br/>
中颜色栏控件命令 ID。

*pParentBtn*<br/>
中指向父按钮的指针。

*src*<br/>
中要复制`CMFCColorBar`到新`CMFCColorBar`对象的现有对象。

*uiCommandID*<br/>
中命令 ID。

##  <a name="contexttosize"></a>CMFCColorBar:: ContextToSize

计算在颜色栏控件上包含按钮所需的垂直和水平边距, 并调整这些按钮的位置。

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*bSquareButtons*|中如果为 TRUE, 则指定颜色条控件上的按钮的形状是正方形;否则为 FALSE。 默认值为 TRUE。|
|*bCenterButtons*|中如果为 TRUE, 则指定颜色条控件按钮表面上的内容居中;否则为 FALSE。 默认值为 TRUE。|

### <a name="remarks"></a>备注

##  <a name="create"></a>CMFCColorBar:: Create

创建一个颜色栏控件窗口, 并将其附加`CMFCColorBar`到对象。

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
中指向父窗口的指针。

*dwStyle*<br/>
中[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的按位组合 (OR)。

*nID*<br/>
中命令 ID。

*pPalette*<br/>
中指向颜色调色板的指针。 默认值为 NULL。

*nColumns*<br/>
中颜色栏控件中的列数。 默认值为 0。

*nRowsDockHorz*<br/>
中在水平停靠时颜色栏控件中的行数。 默认值为 0。

*nColDockVert*<br/>
中在垂直停靠时颜色栏控件中的列数。 默认值为 0。

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

若要构造`CMFCColorBar`对象, 请调用类构造函数, 然后调用此方法。 `Create`方法创建 Windows 控件并初始化颜色列表。

##  <a name="createcontrol"></a>CMFCColorBar:: CreateControl

创建一个颜色栏控件窗口, 将其附加到`CMFCColorBar`对象, 并调整控件窗口的大小以包含指定的颜色调色板。

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
中指向父窗口的指针。 不能为 NULL。

*rect*<br/>
中指定颜色条控件绘制位置的边框。

*nID*<br/>
中控件 ID。

*nColumns*<br/>
中颜色栏控件中的理想列数。 此方法修改该数字以适应颜色的指定调色板。 默认值为-1, 表示未指定此参数。

*pPalette*<br/>
中指向颜色调色板的指针, 或为 NULL。 如果此参数为 NULL, 此方法将计算颜色条控件的大小, 就像指定了20种颜色一样。 默认值为 NULL。

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用*rect*、 *nColumns*和*pPalette*参数计算颜色栏控件中的适当数量或行和列, 然后调用[CMFCColorBar:: Create](#create)方法。

##  <a name="createpalette"></a>CMFCColorBar:: CreatePalette

使用指定颜色数组中的颜色初始化调色板。

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*arColors*|中颜色的数组。|
|*palette*|中颜色的调色板。|

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

##  <a name="enableautomaticbutton"></a>CMFCColorBar:: EnableAutomaticButton

显示或隐藏 "自动" 按钮。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
中"*自动*(默认)" 颜色按钮的文本标签, 或为 NULL。

"自动" 按钮的标准标签为 "**自动**"。

*colorAutomatic*<br/>
中单击 "自动" 按钮时, 框架应用的默认颜色。

*bEnable*<br/>
中若要启用自动按钮, 则为 TRUE;若要禁用自动按钮, 则为 FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

如果*lpszLabel*参数为 NULL 或*BENABLE*参数为 FALSE, 则会删除 "自动" 按钮的文本标签。

##  <a name="enableotherbutton"></a>CMFCColorBar:: EnableOtherButton

启用或禁用允许用户选择更多颜色的对话框显示。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
中"*其他*" 按钮的文本标签, 可显示更多颜色选项, 或为 NULL。

此按钮的标准标签为 "**其他颜色 ...** "。

*bAltColorDlg*<br/>
中如果显示 " [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) " 对话框, 则为 TRUE;若为 FALSE, 则显示 "标准[CColorDialog](../../mfc/reference/ccolordialog-class.md) " 对话框。 默认值为 TRUE。

*bEnable*<br/>
中若要启用此按钮, 则为 TRUE;若要禁用按钮, 则为 FALSE。 默认值为 TRUE。

##  <a name="getcolor"></a>CMFCColorBar:: GetColor

检索当前选定的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

当前选定的颜色。

##  <a name="getcolorgridsize"></a>CMFCColorBar:: GetColorGridSize

计算颜色栏控件网格中的行数和列数。

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*bVertDock*|中若要为垂直停靠的颜色栏控件执行计算, 则为 TRUE;否则, 请为水平停靠的控件执行计算。|

### <a name="return-value"></a>返回值

一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象, `cx`其组件包含列数以及其`cy`组件包含行数。

##  <a name="getcommandid"></a>CMFCColorBar:: GetCommandID

检索当前颜色栏控件的命令 ID。

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>返回值

命令 ID。

### <a name="remarks"></a>备注

当用户选择新的颜色时, 框架会在 WM_COMMAND 消息中发送命令 ID 以通知`CMFCColorBar`对象的父对象。

##  <a name="getextraheight"></a>CMFCColorBar:: GetExtraHeight

计算当前颜色条显示其他用户界面元素 (如**其他**按钮或文档颜色) 所需的附加高度。

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*nNumColumns*|中如果颜色栏控件包含文档颜色, 则为文档颜色网格中显示的列数。 否则, 不使用此值。|

### <a name="return-value"></a>返回值

需要计算的额外高度。

##  <a name="gethighlightedcolor"></a>CMFCColorBar:: GetHighlightedColor

检索表示颜色按钮有焦点的颜色;也就是说, 按钮是*热*的。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>返回值

一个 RGB 值。

### <a name="remarks"></a>备注

##  <a name="gethorzmargin"></a>CMFCColorBar:: GetHorzMargin

检索水平边距, 即左或右两个颜色单元格与工作区边界之间的间距。

```
int GetHorzMargin();
```

### <a name="return-value"></a>返回值

水平边距。

##  <a name="getvertmargin"></a>CMFCColorBar:: GetVertMargin

检索垂直边距, 即上、下颜色单元格与工作区边界之间的间距。

```
int GetVertMargin() const;
```

### <a name="return-value"></a>返回值

垂直边距。

##  <a name="initcolors"></a>CMFCColorBar:: InitColors

用指定调色板中的颜色或系统默认调色板初始化颜色数组。

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pPalette*|中指向调色板对象的指针, 或为 NULL。 如果此参数为 NULL, 此方法将使用操作系统的默认调色板。|
|*arColors*|中颜色的数组。|

### <a name="return-value"></a>返回值

颜色数组中的元素数。

##  <a name="istearoff"></a>CMFCColorBar:: IsTearOff

指示当前颜色栏是否可停靠。

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>返回值

如果当前颜色栏控件可停靠, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果颜色栏控件是可停靠控件, 则可以将其从控件栏中断开并停靠在另一个位置。

##  <a name="onkey"></a>CMFCColorBar:: OnKey

当用户按下键盘按钮时由框架调用。

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>参数

*nChar*<br/>
中用户按下的键的虚拟键代码。

### <a name="return-value"></a>返回值

如果此方法处理指定的键, 则为 TRUE;否则为 FALSE。

##  <a name="onsendcommand"></a>CMFCColorBar:: OnSendCommand

由框架调用以关闭弹出控件的层次结构。

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pButton*|中指向位于工具栏上的控件的指针。|

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

##  <a name="onupdatecmdui"></a>CMFCColorBar:: OnUpdateCmdUI

由框架调用, 以在显示项之前启用或禁用颜色栏控件的用户界面项。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>参数

*pTarget*<br/>
中指向包含要更新的用户界面项的窗口的指针。

*bDisableIfNoHndler*<br/>
中如果消息映射中未定义任何处理程序, 则为 TRUE; 否则为 false。否则为 FALSE。

### <a name="remarks"></a>备注

当应用程序的用户单击用户界面项时, 该项必须知道该用户是否应显示为已启用或已禁用。 命令消息的目标通过实现 ON_UPDATE_COMMAND_UI 命令处理程序来提供此信息。 使用此方法可帮助处理命令。 有关详细信息, 请参阅[CCmdUI 类](../../mfc/reference/ccmdui-class.md)。

##  <a name="opencolordialog"></a>CMFCColorBar:: OpenColorDialog

打开 "颜色" 对话框。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>参数

*colorDefault*<br/>
中当 "颜色" 对话框打开时默认选择的颜色。

*colorRes*<br/>
弄用户选择的颜色。

### <a name="return-value"></a>返回值

如果用户选择了颜色, 则为 TRUE;如果用户取消了 "颜色" 对话框, 则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="rebuild"></a>CMFCColorBar:: Rebuild

完全重绘颜色栏控件。

```
virtual void Rebuild();
```

##  <a name="selectpalette"></a>CMFCColorBar:: SelectPalette

将指定设备上下文的逻辑调色板设置为当前颜色条控件的父按钮的调色板。

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pDC*|中一个指针, 指向当前颜色栏控件的父按钮的设备上下文。|

### <a name="return-value"></a>返回值

指向调色板的指针, 该调色板由当前颜色栏控件的父按钮的调色板替换。

##  <a name="setcolor"></a>CMFCColorBar:: SetColor

设置当前选定的颜色。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

*color*<br/>
中RGB 颜色值。

##  <a name="setcolorname"></a>CMFCColorBar:: SetColorName

为指定的颜色设置新名称。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>参数

*color*<br/>
中颜色的 RGB 值。

*strName*<br/>
中指定颜色的新名称。

### <a name="remarks"></a>备注

此方法在应用程序的所有`CMFCColorBar`对象中更改指定颜色的名称。

##  <a name="setcommandid"></a>CMFCColorBar:: SetCommandID

为颜色栏控件设置新的命令 ID。

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>参数

*nCommandID*<br/>
中命令 ID。

### <a name="remarks"></a>备注

调用此方法可修改颜色栏控件的命令 ID 并通知控件的父窗口, ID 已更改。

##  <a name="setdocumentcolors"></a>CMFCColorBar:: SetDocumentColors

设置在当前文档中使用的颜色的列表。

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>参数

*lpszCaption*<br/>
中颜色栏控件未停靠时显示的标题。

*lstDocColors*<br/>
中替换当前文档颜色的颜色的列表。

*bShowWhenDocked*<br/>
中若要在停靠颜色栏控件时显示文档颜色, 则为 TRUE;否则为 FALSE。 默认值是 FALSE。

### <a name="remarks"></a>备注

*文档颜色*是当前在文档中使用的颜色。 框架自动维护文档颜色列表, 但您可以使用此方法修改列表。

##  <a name="sethorzmargin"></a>CMFCColorBar:: SetHorzMargin

设置水平边距, 这是左或右两个颜色单元格与工作区边界之间的间距。

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>参数

*nHorzMargin*<br/>
中水平边距 (以像素为单位)。

### <a name="remarks"></a>备注

默认情况下, [CMFCColorBar:: CMFCColorBar](#cmfccolorbar)构造函数将水平边距设置为4像素。

##  <a name="setproplist"></a>CMFCColorBar:: SetPropList

将受`m_pWndPropList`保护的数据成员设置为指向属性网格控件的指定指针。

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pWndList*|中指向属性网格控件对象的指针。|

##  <a name="setvertmargin"></a>CMFCColorBar:: SetVertMargin

设置垂直边距, 即上、下颜色单元格与工作区边界之间的间距。

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>参数

*nVertMargin*<br/>
中垂直边距 (以像素为单位)。

### <a name="remarks"></a>备注

默认情况下, [CMFCColorBar:: CMFCColorBar](#cmfccolorbar)构造函数将垂直边距设置为4像素。

##  <a name="showcommandmessagestring"></a>CMFCColorBar:: ShowCommandMessageString

请求拥有颜色条控件的框架窗口, 以更新状态栏中的消息行。

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>参数

*uiCmdId*<br/>
中命令 ID。 (忽略此参数。)

### <a name="remarks"></a>备注

此方法将 WM_SETMESSAGESTRING 消息发送到颜色栏控件的所有者。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
