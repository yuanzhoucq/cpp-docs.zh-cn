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
ms.openlocfilehash: 58fddeef9cb0afe930af84b05e6a87871f729da4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752570"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar 类

类`CMFCColorBar`表示可选择文档或应用程序中的颜色的停靠控制栏。

## <a name="syntax"></a>语法

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CMFCColorBar：CMFCColorBar](#cmfccolorbar)|构造 `CMFCColorBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCColorbar：上下文大小](#contexttosize)|计算包含颜色条控件上的按钮所需的垂直和水平边距，然后调整这些按钮的位置。|
|[CMFCColorBar：创建控制](#createcontrol)|创建颜色栏控件窗口，将其附加到`CMFCColorBar`对象，并调整控件的大小以包含指定的调色板。|
|[CMFCColorBar：创建](#create)|创建颜色条控件窗口并将其附加到`CMFCColorBar`对象。|
|[CMFCColorBar：启用自动按钮](#enableautomaticbutton)|显示或隐藏自动按钮。|
|[CMFCColorBar：启用其他按钮](#enableotherbutton)|启用或禁用允许用户选择更多颜色的对话框的显示。|
|[CMFCColorBar：获取颜色](#getcolor)|检索当前选择的颜色。|
|[CMFCColorBar：获取命令ID](#getcommandid)|检索当前颜色栏控件的命令 ID。|
|[CMFCColorBar：获取突出显示的颜色](#gethighlightedcolor)|检索表示颜色按钮具有焦点的颜色;也就是说，按钮是*热*的。|
|[CMFCColorBar：获取霍兹边缘](#gethorzmargin)|检索水平边距，即左或右颜色单元格和工作区边界之间的空间。|
|[CMFCColorBar：获取 VertMargin](#getvertmargin)|检索垂直边距，即顶部或底部颜色单元格和工作区边界之间的空间。|
|[CMFCColorBar：IsTearoff](#istearoff)|指示当前颜色条是否可停靠。|
|[CMFCColor 栏：设置颜色](#setcolor)|设置当前选择的颜色。|
|[CMFC颜色栏：设置颜色名称](#setcolorname)|为指定颜色设置新名称。|
|[CMFCColorBar：setCommandID](#setcommandid)|为颜色条控件设置新的命令 ID。|
|[CMFCColor 栏：设置文档颜色](#setdocumentcolors)|设置当前文档中使用的颜色列表。|
|[CMFCColorBar：SetHorz边缘](#sethorzmargin)|设置水平边距，即左侧或右侧颜色单元格和工作区边界之间的空间。|
|[CMFC颜色栏：设置Vert边缘](#setvertmargin)|设置垂直边距，即顶部或底部颜色单元格和工作区边界之间的空间。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFCColorBar：调整位置](#adjustlocations)|调整颜色条控件上颜色按钮的位置。|
|[CMFCColor 栏：允许更改文本标签](#allowchangetextlabels)|指示颜色按钮的文本标签是否可以更改。|
|[CMFCColorbar：允许显示列表](#allowshowonlist)|指示在自定义过程中，颜色条控件对象是否可以显示在工具栏列表中。|
|[CMFCColorBar：钙化](#calcsize)|框架在布局计算过程中调用。|
|[CMFCColorBar：创建调色板](#createpalette)|使用指定颜色数组中的颜色初始化调色板。|
|[CMFCColorBar：获取颜色网格大小](#getcolorgridsize)|计算颜色条控件网格中的行数和列数。|
|[CMFCColorBar：获取额外高度](#getextraheight)|计算当前颜色栏显示其他用户界面元素（如 **"其他**"按钮、文档颜色等）所需的额外高度。|
|[CMFCColorbar：：以颜色](#initcolors)|使用指定调色板中的颜色或系统默认调色板中的颜色初始化颜色数组。|
|[CMFCColorbar：：打开钥匙](#onkey)|当用户按下键盘按钮时，框架调用。|
|[CMFCColorbar：打开发送命令](#onsendcommand)|由框架调用以关闭弹出控件的层次结构。|
|[CMFCColorBar：关于更新CmdUI](#onupdatecmdui)|框架调用以在显示项目之前启用或禁用颜色条控件的用户界面项。|
|[CMFCColorBar：：打开颜色对话](#opencolordialog)|打开颜色对话框。|
|[CMFCColorBar：重建](#rebuild)|完全重绘色条控件。|
|[CMFCColor 栏：选择调色板](#selectpalette)|将指定设备上下文的逻辑调色板设置为当前颜色栏控件的父按钮的调色板。|
|[CMFCColor 栏：设置Proplist](#setproplist)|将`m_pWndPropList`受保护的数据成员设置到指向属性网格控件的指定指针。|
|[CMFCColorBar：：显示命令消息字符串](#showcommandmessagestring)|请求拥有颜色栏控件的帧窗口更新状态栏中的消息行。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|`m_bInternal`|确定是否处理鼠标事件的布尔字段。 通常，当此字段为 TRUE 且自定义模式为 FALSE 时，将处理鼠标事件。|
|`m_bIsEnabled`|指示控件是否已启用的布尔。|
|`m_bIsTearOff`|指示颜色条控件是否支持停靠的布尔。|
|`m_BoxSize`|指定颜色栏网格中单元格大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。|
|`m_bShowDocColorsWhenDocked`|一个布尔，指示在颜色条停靠时是否显示文档颜色。 有关详细信息，请参阅[CMFCColor 栏：设置文档颜色](#setdocumentcolors)。|
|`m_bStdColorDlg`|指示是显示标准系统颜色对话框还是[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)对话框的布尔。 有关详细信息，请参阅[CMFCColorBar：启用其他按钮](#enableotherbutton)。|
|`m_ColorAutomatic`|存储当前自动颜色的[COLORREF。](/windows/win32/gdi/colorref) 有关详细信息，请参阅[CMFCColorBar：启用其他按钮](#enableotherbutton)。|
|`m_ColorNames`|将一组 RGB 颜色与其名称关联到的[CMap](../../mfc/reference/cmap-class.md)对象。|
|`m_colors`|包含颜色栏控件中显示的颜色的[COLORREF](/windows/win32/gdi/colorref)值的[CArray。](../../mfc/reference/carray-class.md)|
|`m_ColorSelected`|[COLORREF](/windows/win32/gdi/colorref)值，是用户当前从色条控件中选择的颜色。|
|`m_lstDocColors`|包含文档中当前使用的颜色的[COLORREF](/windows/win32/gdi/colorref)值的[CList。](../../mfc/reference/clist-class.md)|
|`m_nCommandID`|一个未签名的整数，它是颜色按钮的命令 ID。|
|`m_nHorzMargin`|一个整数，它是颜色网格中颜色按钮之间的水平边距。|
|`m_nHorzOffset`|一个整数，它是颜色按钮中心的水平偏移。 如果按钮除了显示颜色外，还显示文本或图像，则此值很重要。|
|`m_nNumColumns`|一个整数，它是颜色栏中控制颜色网格中的列数。|
|`m_nNumColumnsVert`|一个整数，它是垂直方向的颜色网格中的列数。|
|`m_nNumRowsHorz`|一个整数，它是水平方向颜色网格中的列数。|
|`m_nRowHeight`|一个整数，它是颜色网格中一行颜色按钮的高度。|
|`m_nVertMargin`|一个整数，它是颜色网格中颜色按钮之间的垂直边距。|
|`m_nVertOffset`|一个整数，它是颜色按钮中心的垂直偏移。 如果按钮除了显示颜色外，还显示文本或图像，则此值很重要。|
|`m_Palette`|颜色栏控件中使用的颜色的[CPalette。](../../mfc/reference/cpalette-class.md)|
|`m_pParentBtn`|指向当前按钮的父级[的 CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)对象的指针。 如果颜色按钮位于工具栏控件的层次结构中或位于颜色属性网格控件中，则此值非常重要。|
|`m_pParentRibbonBtn`|指向功能区上的[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)对象的指针，该对象是当前按钮的父按钮。 如果颜色按钮位于工具栏控件的层次结构中或位于颜色属性网格控件中，则此值非常重要。|
|`m_pWndPropList`|指向[CMFC 属性网格Ctrl](../../mfc/reference/cmfcpropertygridctrl-class.md)对象的指针。|
|`m_strAutoColor`|["CString"，](../../atl-mfc-shared/reference/cstringt-class.md)是 **"自动"** 按钮上显示的文本。 有关详细信息，请参阅[CMFCColorBar：启用自动按钮](#enableautomaticbutton)。|
|`m_strDocColors`|[CString，](../../atl-mfc-shared/reference/cstringt-class.md)是显示在文档颜色按钮上的文本。 有关详细信息，请参阅[CMFCColor 栏：设置文档颜色](#setdocumentcolors)。|
|`m_strOtherColor`|[CString，](../../atl-mfc-shared/reference/cstringt-class.md)是*显示在另一个*按钮上的文本。 有关详细信息，请参阅[CMFCColorBar：启用其他按钮](#enableotherbutton)。|

## <a name="remarks"></a>备注

通常，您不会直接创建`CMFCColorBar`对象。 相反[，CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)（用于菜单和工具栏）或[CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)将创建`CMFCColorBar`该对象。

该`CMFCColorBar`类提供以下功能：

- 自动调整文档颜色的列表。

- 保存和恢复其状态以及文档状态。

- 管理"自动"按钮。

- 使用[CMFCColorPickerCtrl 类](../../mfc/reference/cmfccolorpickerctrl-class.md)控件选择自定义颜色。

- 支持"撕掉"状态（如果使用[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)创建）。

要将`CMFCColorBar`功能合并到应用程序中，

1. 创建常规菜单按钮并为其分配 ID，例如ID_CHAR_COLOR。

1. 在框架窗口类中，重写[CFrameWndEx：：onShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)方法，并将常规菜单按钮替换为[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)对象（通过调用[CMFCToolBar：：替换按钮](../../mfc/reference/cmfctoolbar-class.md#replacebutton)）。

1. 在[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)创建期间设置`CMFCColorBar`所有样式并启用或禁用对象的功能。 对象`CMFCColorMenuButton`在框架调用`CMFCColorBar``CreatePopupMenu`方法后动态创建对象。

当用户单击颜色条控件按钮时，框架将使用`ON_COMMAND`宏通知颜色条控件的父级。 在宏中，命令 ID 参数是分配给步骤 1 中 color 栏控制按钮的值（ID_CHAR_COLOR在此示例中）。 有关详细信息，请参阅[CMFCColorMenuButton 类](../../mfc/reference/cmfccolormenubutton-class.md)[、CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)[、CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)类[、CFrameWndEx 类](../../mfc/reference/cframewndex-class.md)和[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCColorBar`类中的各种方法配置颜色条。 这些方法设置水平和垂直边距，启用另一个按钮，创建颜色条控制窗口，并设置当前选择的颜色。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具栏](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>要求

**标题：** afxcolorbar.h

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a>CMFCColorBar：调整位置

调整颜色条控件上颜色按钮的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>备注

在消息处理期间，框架会调用此方法WM_SIZE消息处理。

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCColor 栏：允许更改文本标签

指示颜色按钮的文本标签是否可以更改。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>返回值

始终为 FALSE。

### <a name="remarks"></a>备注

默认情况下，此方法始终返回 FALSE，这意味着无法修改文本标签。 重写此方法以启用修改文本标签。

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCColorbar：允许显示列表

指示在自定义过程中，颜色条控件对象是否可以显示在工具栏列表中。

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>返回值

始终为 TRUE。

### <a name="remarks"></a>备注

默认情况下，此方法始终返回 TRUE，这意味着框架可以在自定义过程中显示色条控件。 重写此方法以实现其他行为。

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a>CMFCColorBar：钙化

框架在布局计算过程中调用。

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>参数

*bVertDock*<br/>
[在]TRUE 指定颜色条控件垂直停靠;FALSE 以指定颜色条控件水平停靠。

### <a name="return-value"></a>返回值

颜色栏控件中颜色按钮数组的大小。

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a>CMFCColorBar：CMFCColorBar

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
[在]框架显示在颜色栏控件上的颜色数组。

*颜色*<br/>
[在]最初选择的颜色。

*lpsz自动颜色*<br/>
[在]*自动*（默认）颜色按钮或 NULL 的文本标签。

自动按钮的标准标签是 **"自动**"。

*lpszOther颜色*<br/>
[在]*另*一个按钮的文本标签，显示更多颜色选项，或 NULL。

另一个按钮的标准标签是 **"更多颜色..."**

*lpszDocColors*<br/>
[在]文档颜色按钮的文本标签。 文档颜色调色板列出文档当前使用的所有颜色。

*lstDocColors*<br/>
[在]文档当前使用的颜色列表。

*nColumns*<br/>
[在]颜色数组的列数。

*n 罗索多克霍尔兹*<br/>
[在]颜色栏水平停靠时的行数。

*n科尔多克弗特*<br/>
[在]颜色栏垂直停靠时的列数。

*颜色 自动*<br/>
[在]单击自动按钮时框架适用的默认颜色。

*nCommandID*<br/>
[在]颜色条控制命令 ID。

*p 家长Btn*<br/>
[在]指向父按钮的指针。

*src*<br/>
[在]要复制到`CMFCColorBar`新`CMFCColorBar`对象的现有对象。

*uiCommandID*<br/>
[在]命令 ID。

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a>CMFCColorbar：上下文大小

计算包含颜色条控件上的按钮所需的垂直和水平边距，并调整这些按钮的位置。

```cpp
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*b方形按钮*|[在]TRUE 指定颜色条控件上的按钮形状为正方形;否则，FALSE。 默认值为 TRUE。|
|*b中心按钮*|[在]TRUE 指定颜色条控制按钮正面上的内容居中;否则，FALSE。 默认值为 TRUE。|

### <a name="remarks"></a>备注

## <a name="cmfccolorbarcreate"></a><a name="create"></a>CMFCColorBar：创建

创建颜色条控件窗口并将其附加到`CMFCColorBar`对象。

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

*pparentwnd*<br/>
[在]指向父窗口的指针。

*dwStyle*<br/>
[在][窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的位组合 （OR）。

*nID*<br/>
[在]命令 ID。

*pPalette*<br/>
[在]指向颜色调色板的指针。 默认值为 NULL。

*nColumns*<br/>
[在]颜色栏控件中的列数。 默认值为 0。

*n 罗索多克霍尔兹*<br/>
[在]颜色栏控件中水平停靠的行数。 默认值为 0。

*n科尔多克弗特*<br/>
[在]颜色条控件中垂直停靠的列数。 默认值为 0。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

要构造对象`CMFCColorBar`，请调用类构造函数，然后调用此方法。 该方法`Create`创建 Windows 控件并初始化颜色列表。

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a>CMFCColorBar：创建控制

创建颜色栏控件窗口，将其附加到`CMFCColorBar`对象，并调整控件窗口的大小以包含指定的调色板。

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
[在]指向父窗口的指针。 不能为 NULL。

*矩形*<br/>
[在]指定绘制颜色条控件的位置的边界矩形。

*nID*<br/>
[在]控件 ID。

*nColumns*<br/>
[在]颜色条控件中理想的列数。 此方法修改该数字以适合指定的颜色调色板。 默认值为 -1，这意味着未指定此参数。

*pPalette*<br/>
[在]指向颜色调色板的指针，或 NULL。 如果此参数为 NULL，则此方法计算颜色条控件的大小，就像指定了 20 种颜色一样。 默认值为 NULL。

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

此方法使用*rect、nColumns*和*pPalette*参数计算颜色栏控件中的适当数字或行和列，然后调用[CMFCColorBar：：create](#create)方法。 *nColumns*

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a>CMFCColorBar：创建调色板

使用指定颜色数组中的颜色初始化调色板。

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*阿尔颜色*|[在]颜色数组。|
|*调色板 (palette)*|[在]颜色的调色板。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorBar：启用自动按钮

显示或隐藏自动按钮。

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]*自动*（默认）颜色按钮或 NULL 的文本标签。

自动按钮的标准标签是 **"自动**"。

*颜色 自动*<br/>
[在]单击自动按钮时框架适用的默认颜色。

*b 启用*<br/>
[在]TRUE 启用自动按钮;FALSE 以禁用自动按钮。 默认值为 TRUE。

### <a name="remarks"></a>备注

如果*lpszLabel*参数为 NULL 或*bEnable*参数为 FALSE，则自动按钮的文本标签将被删除。

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorBar：启用其他按钮

启用或禁用允许用户选择更多颜色的对话框的显示。

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*lpszLabel*<br/>
[在]*另*一个按钮的文本标签，显示更多颜色选项，或 NULL。

此按钮的标准标签是**更多颜色...**

*巴尔特·博拉尔德格*<br/>
[在]TRUE 显示[CMFCColor对话框](../../mfc/reference/cmfccolordialog-class.md);FALSE 以显示标准[CColorDialog](../../mfc/reference/ccolordialog-class.md)对话框。 默认值为 TRUE。

*b 启用*<br/>
[在]TRUE 启用按钮;FALSE 以禁用按钮。 默认值为 TRUE。

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a>CMFCColorBar：获取颜色

检索当前选择的颜色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>返回值

当前选择的颜色。

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a>CMFCColorBar：获取颜色网格大小

计算颜色条控件网格中的行数和列数。

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*bVertDock*|[在]TRUE 以执行垂直停靠的色条控件的计算;否则，对水平停靠控件执行计算。|

### <a name="return-value"></a>返回值

其`cx`组件包含列数及其`cy`组件包含行数的[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a>CMFCColorBar：获取命令ID

检索当前颜色栏控件的命令 ID。

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>返回值

命令 ID。

### <a name="remarks"></a>备注

当用户选择新颜色时，框架将发送WM_COMMAND消息中的命令 ID 以通知`CMFCColorBar`对象的父级。

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a>CMFCColorBar：获取额外高度

计算当前颜色栏显示其他用户界面元素（如 **"其他**"按钮或文档颜色）所需的额外高度。

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*nNumColumns*|[在]如果颜色条控件包含文档颜色，则要在文档颜色网格中显示的列数。 否则，不使用此值。|

### <a name="return-value"></a>返回值

所需的计算额外高度。

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCColorBar：获取突出显示的颜色

检索表示颜色按钮具有焦点的颜色;也就是说，按钮是*热*的。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>返回值

RGB 值。

### <a name="remarks"></a>备注

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a>CMFCColorBar：获取霍兹边缘

检索水平边距，即左或右颜色单元格和工作区边界之间的空间。

```
int GetHorzMargin();
```

### <a name="return-value"></a>返回值

水平边距。

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a>CMFCColorBar：获取 VertMargin

检索垂直边距，即顶部或底部颜色单元格和工作区边界之间的空间。

```
int GetVertMargin() const;
```

### <a name="return-value"></a>返回值

垂直边距。

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a>CMFCColorbar：：以颜色

使用指定调色板中的颜色或系统默认调色板初始化颜色数组。

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pPalette*|[在]指向调色板对象的指针，或 NULL。 如果此参数为 NULL，则此方法使用操作系统的默认调色板。|
|*阿尔颜色*|[在]颜色数组。|

### <a name="return-value"></a>返回值

颜色数组中的元素数。

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a>CMFCColorBar：IsTearoff

指示当前颜色条是否可停靠。

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>返回值

如果当前颜色条控件可停靠，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

如果颜色条控件可停靠，则可以将其从控制栏上撕下并停靠在另一个位置。

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a>CMFCColorbar：：打开钥匙

当用户按下键盘按钮时，框架调用。

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>参数

*n查尔*<br/>
[在]用户按下的密钥的虚拟密钥代码。

### <a name="return-value"></a>返回值

如果此方法处理指定的密钥，则为 TRUE;如果此方法处理指定的密钥，则为 TRUE。否则，FALSE。

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a>CMFCColorbar：打开发送命令

由框架调用以关闭弹出窗口控件的层次结构。

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pButton*|[在]指向驻留在工具栏上的控件的指针。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCColorBar：关于更新CmdUI

框架调用以在显示项目之前启用或禁用颜色条控件的用户界面项。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>参数

*p目标*<br/>
[在]指向包含要更新的用户界面项的窗口的指针。

*b 禁用IfNoHndler*<br/>
[在]如果消息映射中未定义处理程序，则为禁用用户界面项;如果消息映射中未定义任何处理程序，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

当应用程序的用户单击用户界面项时，该项必须知道该项应显示为已启用还是禁用。 命令消息的目标通过实现ON_UPDATE_COMMAND_UI命令处理程序来提供此信息。 使用此方法可帮助处理该命令。 有关详细信息，请参阅[CCmdUI 类](../../mfc/reference/ccmdui-class.md)。

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a>CMFCColorBar：：打开颜色对话

打开颜色对话框。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>参数

*颜色 默认*<br/>
[在]默认情况下，颜色对话框打开时选择的颜色。

*颜色 Res*<br/>
[出]用户选择的颜色。

### <a name="return-value"></a>返回值

如果用户选择了颜色，则为 TRUE;如果用户选择了颜色。如果用户取消了颜色对话框，则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a>CMFCColorBar：重建

完全重绘色条控件。

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a>CMFCColor 栏：选择调色板

将指定设备上下文的逻辑调色板设置为当前颜色栏控件的父按钮的调色板。

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pDC*|[在]指向当前颜色栏控件的父按钮的设备上下文。|

### <a name="return-value"></a>返回值

指针指向由当前颜色条控件的父按钮的调色板替换的调色板。

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a>CMFCColor 栏：设置颜色

设置当前选择的颜色。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]RGB 颜色值。

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a>CMFC颜色栏：设置颜色名称

为指定颜色设置新名称。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]颜色的 RGB 值。

*strName*<br/>
[在]指定颜色的新名称。

### <a name="remarks"></a>备注

此方法更改应用程序中所有`CMFCColorBar`对象中指定颜色的名称。

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a>CMFCColorBar：setCommandID

为颜色条控件设置新的命令 ID。

```cpp
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>参数

*nCommandID*<br/>
[在]命令 ID。

### <a name="remarks"></a>备注

调用此方法以修改颜色条控件的命令 ID，并通知控件的父窗口 ID 已更改。

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColor 栏：设置文档颜色

设置当前文档中使用的颜色列表。

```cpp
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>参数

*lpszCaption*<br/>
[在]颜色条控件未停靠时显示的标题。

*lstDocColors*<br/>
[在]替换当前文档颜色的颜色列表。

*b 显示当已装*<br/>
[在]TRUE 显示颜色条控件停靠时的文档颜色;否则，FALSE。 默认值是 FALSE。

### <a name="remarks"></a>备注

*文档颜色*是文档中当前使用的颜色。 框架会自动维护文档颜色的列表，但您可以使用此方法修改列表。

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a>CMFCColorBar：SetHorz边缘

设置水平边距，即左侧或右侧颜色单元格与工作区边界之间的空间。

```cpp
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>参数

*nHorzMargin*<br/>
[在]水平边距，以像素为单位。

### <a name="remarks"></a>备注

默认情况下[，CMFCColorBar：CMFCColorBar](#cmfccolorbar)构造函数将水平边距设置为 4 像素。

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a>CMFCColor 栏：设置Proplist

将`m_pWndPropList`受保护的数据成员设置到指向属性网格控件的指定指针。

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pwndlist*|[在]指向属性网格控制对象的指针。|

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a>CMFC颜色栏：设置Vert边缘

设置垂直边距，即顶部或底部颜色单元格和工作区边界之间的空间。

```cpp
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>参数

*nVertMargin*<br/>
[在]垂直边距，以像素为单位。

### <a name="remarks"></a>备注

默认情况下[，CMFCColorBar：CMFCColorBar](#cmfccolorbar)构造函数将垂直边距设置为 4 像素。

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a>CMFCColorBar：：显示命令消息字符串

请求拥有颜色栏控件的帧窗口更新状态栏中的消息行。

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>参数

*乌伊CmDId*<br/>
[在]命令 ID。 （此参数将被忽略。

### <a name="remarks"></a>备注

此方法将WM_SETMESSAGESTRING消息发送到颜色栏控件的所有者。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
