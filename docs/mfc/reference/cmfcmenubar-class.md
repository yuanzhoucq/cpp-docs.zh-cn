---
title: CMFCMenuBar 类
ms.date: 10/18/2018
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
helpviewer_keywords:
- CMFCMenuBar [MFC], AdjustLocations
- CMFCMenuBar [MFC], AllowChangeTextLabels
- CMFCMenuBar [MFC], AllowShowOnPaneMenu
- CMFCMenuBar [MFC], CalcFixedLayout
- CMFCMenuBar [MFC], CalcLayout
- CMFCMenuBar [MFC], CalcMaxButtonHeight
- CMFCMenuBar [MFC], CanBeClosed
- CMFCMenuBar [MFC], CanBeRestored
- CMFCMenuBar [MFC], Create
- CMFCMenuBar [MFC], CreateEx
- CMFCMenuBar [MFC], CreateFromMenu
- CMFCMenuBar [MFC], EnableHelpCombobox
- CMFCMenuBar [MFC], EnableMenuShadows
- CMFCMenuBar [MFC], GetAvailableExpandSize
- CMFCMenuBar [MFC], GetColumnWidth
- CMFCMenuBar [MFC], GetDefaultMenu
- CMFCMenuBar [MFC], GetDefaultMenuResId
- CMFCMenuBar [MFC], GetFloatPopupDirection
- CMFCMenuBar [MFC], GetForceDownArrows
- CMFCMenuBar [MFC], GetHelpCombobox
- CMFCMenuBar [MFC], GetHMenu
- CMFCMenuBar [MFC], GetMenuFont
- CMFCMenuBar [MFC], GetMenuItem
- CMFCMenuBar [MFC], GetRowHeight
- CMFCMenuBar [MFC], GetSystemButton
- CMFCMenuBar [MFC], GetSystemButtonsCount
- CMFCMenuBar [MFC], GetSystemMenu
- CMFCMenuBar [MFC], HighlightDisabledItems
- CMFCMenuBar [MFC], IsButtonExtraSizeAvailable
- CMFCMenuBar [MFC], IsHighlightDisabledItems
- CMFCMenuBar [MFC], IsMenuShadows
- CMFCMenuBar [MFC], IsRecentlyUsedMenus
- CMFCMenuBar [MFC], IsShowAllCommands
- CMFCMenuBar [MFC], IsShowAllCommandsDelay
- CMFCMenuBar [MFC], LoadState
- CMFCMenuBar [MFC], OnChangeHot
- CMFCMenuBar [MFC], OnDefaultMenuLoaded
- CMFCMenuBar [MFC], OnSendCommand
- CMFCMenuBar [MFC], OnSetDefaultButtonText
- CMFCMenuBar [MFC], OnToolHitTest
- CMFCMenuBar [MFC], PreTranslateMessage
- CMFCMenuBar [MFC], RestoreOriginalstate
- CMFCMenuBar [MFC], SaveState
- CMFCMenuBar [MFC], SetDefaultMenuResId
- CMFCMenuBar [MFC], SetForceDownArrows
- CMFCMenuBar [MFC], SetMaximizeMode
- CMFCMenuBar [MFC], SetMenuButtonRTC
- CMFCMenuBar [MFC], SetMenuFont
- CMFCMenuBar [MFC], SetRecentlyUsedMenus
- CMFCMenuBar [MFC], SetShowAllCommands
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
ms.openlocfilehash: 87844e843057bb295c904b5f1b3d7dd03fa4d797
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775889"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar 类

实现停靠的菜单栏。
有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。

## <a name="syntax"></a>语法

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|（重写 `CMFCToolBar::AdjustLocations`。）|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|指定是否可以在工具栏按钮上的映像下显示的文本标签。 (重写[CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels)。)|
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|计算工具栏的水平大小。 (重写[CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout)。)|
|[CMFCMenuBar::CalcLayout](#calclayout)|（重写 `CMFCToolBar::CalcLayout`。）|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|计算按钮在工具栏中的最大高度。 (重写[CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight)。)|
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|指定用户是否可以关闭工具栏。 (重写[CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed)。)|
|[CMFCMenuBar::CanBeRestored](#canberestored)|确定是否在系统可以还原工具栏到其原始状态后自定义。 (重写[CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|
|[CMFCMenuBar::Create](#create)|创建菜单控件，并将其附加到`CMFCMenuBar`对象。|
|[CMFCMenuBar::CreateEx](#createex)|创建`CMFCMenuBar`具有其他样式选项对象。|
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|初始化`CMFCMenuBar`对象。 接受充当用于已填充的模板的 HMENU 参数`CMFCMenuBar`。|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|使**帮助**组合框位于菜单栏的右侧。|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|指定是否显示阴影对于弹出菜单。|
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(重写[CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize)。)|
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|返回的工具栏按钮的宽度。 (重写[CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth)。)|
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|返回的句柄的原始菜单中的资源文件。|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|返回资源文件中的原始菜单上的资源标识符。|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|返回一个指向**帮助**组合框。|
|[CMFCMenuBar::GetHMenu](#gethmenu)|返回的句柄附加到的菜单`CMFCMenuBar`对象。|
|[CMFCMenuBar::GetMenuFont](#getmenufont)|返回菜单对象的当前全局字体。|
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|返回具有提供的项索引相关联的工具栏按钮。|
|[CMFCMenuBar::GetRowHeight](#getrowheight)|返回的工具栏按钮的高度。 (重写[CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight)。)|
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|指示是否已禁用的菜单项会突出显示。|
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|确定工具栏是否可以显示已扩展边框的按钮。 (重写[CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable)。)|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|指示是否已禁用的项会突出显示。|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|指示绘制阴影时是否对于弹出菜单。|
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|指示是否在菜单栏上显示最近使用的菜单命令。|
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|指示弹出菜单是否显示所有命令。|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|指示菜单是否一小段延迟后显示的所有命令。|
|[CMFCMenuBar::LoadState](#loadstate)|加载的状态`CMFCMenuBar`注册表中的对象。|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|当用户选择工具栏上的按钮时由框架调用。 (重写[CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot)。)|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|框架窗口从资源文件加载默认菜单时由框架调用。|
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|（重写 `CMFCToolBar::OnSendCommand`。）|
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|当菜单自定义模式并在用户更改菜单项文本时由框架调用。|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|（重写 `CMFCToolBar::OnToolHitTest`。）|
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|（重写 `CMFCToolBar::PreTranslateMessage`。）|
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|菜单中自定义模式，并且用户选择时由框架调用**重置**表示菜单栏。|
|[CMFCMenuBar::SaveState](#savestate)|保存的状态`CMFCMenuBar`对注册表的对象。|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|在资源文件中设置的原始菜单。|
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|MDI 子窗口更改其显示模式时，由框架调用。 如果 MDI 子窗口新最大化或不再最大化，此方法将更新菜单栏。|
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|设置用户动态创建菜单按钮时，将生成的运行时类信息。|
|[CMFCMenuBar::SetMenuFont](#setmenufont)|在应用程序中设置所有菜单的字体。|
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|指定菜单栏是否显示最近使用的菜单命令。|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|指定是否在菜单栏显示了所有命令。|

## <a name="remarks"></a>备注

`CMFCMenuBar`类是实现停靠功能的菜单栏。 它类似于一个工具栏，尽管它不能关闭-始终显示。

`CMFCMenuBar` 支持显示最近使用的菜单项对象的选项。 如果启用此选项，`CMFCMenuBar`显示可用命令的一个子集上第一次查看。 此后，最近使用的命令会显示以及原始命令子集。 此外，用户始终可以展开此菜单可查看所有可用的命令。 因此，不断，显示或显示仅当最近所选配置每个可用命令。

若要使用`CMFCMenuBar`对象，其嵌入主窗口框架对象。 处理时`WM_CREATE`消息，请调用`CMFCMenuBar::Create`或`CMFCMenuBar::CreateEx`。 而不考虑其创建函数使用，将指针传递给主框架窗口。 然后启用通过调用停靠[cframewndex:: Enabledocking](../../mfc/reference/cframewndex-class.md#enabledocking)。 通过调用停靠此菜单[CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane)。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCMenuBar` 类中的各种方法。 该示例演示如何将窗格的样式设置、 启用自定义按钮、 启用的帮助框，启用对于弹出菜单的阴影和更新菜单栏。 此代码片段属于[IE 演示示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>要求

**标头：** afxmenubar.h

##  <a name="adjustlocations"></a>  CMFCMenuBar::AdjustLocations

调整在菜单栏上的菜单项的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>备注

##  <a name="allowchangetextlabels"></a>  CMFCMenuBar::AllowChangeTextLabels

确定是否在菜单栏中的图像下，允许文本标签。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>返回值

如果用户可以选择显示在映像下的文本标签，则返回 TRUE。

### <a name="remarks"></a>备注

##  <a name="allowshowonpanemenu"></a>  CMFCMenuBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="calcfixedlayout"></a>  CMFCMenuBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

[in] *bStretch*<br/>

[in] *bHorz*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="calclayout"></a>  CMFCMenuBar::CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>参数

[in] *dwMode*<br/>

[in] *nLength*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="calcmaxbuttonheight"></a>  CMFCMenuBar::CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="canbeclosed"></a>  CMFCMenuBar::CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="canberestored"></a>  CMFCMenuBar::CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="create"></a>  CMFCMenuBar::Create

创建菜单控件，并将其附加到[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
[in]指向新的父窗口`CMFCMenuBar`对象。

*dwStyle*<br/>
[in]新的菜单栏的样式。

*nID*<br/>
[in]菜单栏的子窗口的 ID。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

在构造之后`CMFCMenuBar`对象，必须调用`Create`。 此方法创建`CMFCMenuBar`控件并将其附加到`CMFCMenuBar`对象。

有关工具栏样式的详细信息，请参阅[CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle)。

##  <a name="createex"></a>  CMFCMenuBar::CreateEx

创建[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象与指定的扩展样式。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    CRect rcBorders = CRect(1,
    1,
    1,
    1),
    UINT nID =AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
[in]指向新的父窗口`CMFCMenuBar`对象。

*dwCtrlStyle*<br/>
[in]新的菜单栏的其他样式。

*dwStyle*<br/>
[in]新的菜单栏主样式。

*rcBorders*<br/>
[in]一个`CRect`参数指定的边框的大小`CMFCMenuBar`对象。

*nID*<br/>
[in]菜单栏的子窗口的 ID。

### <a name="return-value"></a>返回值

如果此方法成功，则非零值否则为 0。

### <a name="remarks"></a>备注

应使用此函数，而不是[CMFCMenuBar::Create](#create)时想要指定除工具栏样式的样式。 一些常用的其他样式是 TBSTYLE_TRANSPARENT 和 CBRS_TOP。

有关其他样式的列表，请参阅[工具栏控件和按钮样式](/windows/desktop/Controls/toolbar-control-and-button-styles)，[常见控件样式](/windows/desktop/Controls/common-control-styles)，并[常见窗口样式](/windows/desktop/winmsg/window-styles)。

### <a name="example"></a>示例

下面的示例演示如何使用`CreateEx`方法的`CMFCMenuBar`类。 此代码片段属于[IE 演示示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

##  <a name="createfrommenu"></a>  CMFCMenuBar::CreateFromMenu

初始化[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。 此方法模型`CMFCMenuBar`HMENU 参数后的对象。

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
[in]菜单资源的句柄。 `CreateFromMenu` 使用此资源的模板`CMFCMenuBar`。

*bDefaultMenu*<br/>
[in]一个布尔值，该值指示新菜单是否为默认菜单。

*bForceUpdate*<br/>
[in]一个布尔值，该值指示是否此方法强制执行菜单更新。

### <a name="remarks"></a>备注

如果您希望具有相同的菜单项的菜单资源作为菜单控件，请使用此方法。 调用此方法后调用放[CMFCMenuBar::Create](#create)或[CMFCMenuBar::CreateEx](#createex)。

##  <a name="enablehelpcombobox"></a>  CMFCMenuBar::EnableHelpCombobox

使**帮助**组合框位于菜单栏的右侧。

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[in]按钮的命令 ID**帮助**组合框。

*lpszPrompt*<br/>
[in]一个字符串，包含框架显示组合框中，如果它为空且未处于活动状态的文本。 例如，"输入文本在此处"。

*nComboBoxWidth*<br/>
[in]按钮的组合框，以像素为单位的宽度。

### <a name="remarks"></a>备注

**帮助**组合框类似于**帮助**菜单栏中的 Microsoft Word 的组合框。

当调用此方法替换*uiID*设置为 0，此方法会隐藏组合框。 否则，此方法显示组合框会自动在菜单栏的右侧。 调用此方法后，调用[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)若要获取指向插入[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象。

##  <a name="enablemenushadows"></a>  CMFCMenuBar::EnableMenuShadows

使弹出菜单的阴影。

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]一个布尔型参数，该值指示阴影是否应启用对于弹出菜单。

### <a name="remarks"></a>备注

此方法使用的算法很复杂，可能会降低速度较慢的系统上的应用程序的性能。

##  <a name="getavailableexpandsize"></a>  CMFCMenuBar::GetAvailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getcolumnwidth"></a>  CMFCMenuBar::GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getdefaultmenu"></a>  CMFCMenuBar::GetDefaultMenu

检索原始菜单的句柄。 框架从资源文件加载原始菜单。

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>返回值

菜单资源的句柄。

### <a name="remarks"></a>备注

如果你的应用程序自定义菜单，可以使用此方法以检索原始菜单的句柄。

##  <a name="getdefaultmenuresid"></a>  CMFCMenuBar::GetDefaultMenuResId

检索默认菜单的资源标识符。

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>返回值

菜单资源标识符。

### <a name="remarks"></a>备注

框架将加载的默认菜单`CMFCMenuBar`从资源文件的对象。

##  <a name="getfloatpopupdirection"></a>  CMFCMenuBar::GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>参数

[in] *pButton*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getforcedownarrows"></a>  CMFCMenuBar::GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="gethelpcombobox"></a>  CMFCMenuBar::GetHelpCombobox

返回一个指向**帮助**组合框。

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>返回值

一个指向**帮助**组合框。 则为 NULL**帮助**隐藏或未启用组合框。

### <a name="remarks"></a>备注

**帮助**组合框位于菜单栏的右侧。 调用方法[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)若要启用此组合框。

##  <a name="gethmenu"></a>  CMFCMenuBar::GetHMenu

检索附加到的菜单的句柄[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。

```
HMENU GetHMenu() const;
```

##  <a name="getmenufont"></a>  CMFCMenuBar::GetMenuFont

检索当前菜单字体。

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>参数

*bHorz*<br/>
[in]一个布尔参数，指定是否返回水平或垂直字体。 TRUE 表示水平字体。

### <a name="return-value"></a>返回值

一个指向[CFont](../../mfc/reference/cfont-class.md)参数，其中包含当前菜单栏字体。

### <a name="remarks"></a>备注

返回的字体是应用程序的全局参数。 为所有维护两个全局字体`CMFCMenuBar`对象。 这些单独的字体用于水平和垂直菜单栏。

##  <a name="getmenuitem"></a>  CMFCMenuBar::GetMenuItem

检索[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)菜单栏上的对象基于的项索引。

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>参数

*iItem*<br/>
[in]要返回的菜单项的索引。

### <a name="return-value"></a>返回值

一个指向`CMFCToolBarButton`与指定的索引相匹配的对象*iItem*。 如果该索引不存在，则为 NULL。

##  <a name="getrowheight"></a>  CMFCMenuBar::GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getsystembutton"></a>  CMFCMenuBar::GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>参数

[in] *uiBtn*<br/>

[in] *bByCommand*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getsystembuttonscount"></a>  CMFCMenuBar::GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getsystemmenu"></a>  CMFCMenuBar::GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="highlightdisableditems"></a>  CMFCMenuBar::HighlightDisabledItems

控制是否在 framework 突出显示已禁用的菜单项。

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>参数

*bHighlight*<br/>
[in]一个布尔参数，指示框架是否突出显示不可用的菜单项。

### <a name="remarks"></a>备注

默认情况下，框架不突出显示不可用的菜单项时用户将鼠标指针定位过它们。

##  <a name="isbuttonextrasizeavailable"></a>  CMFCMenuBar::IsButtonExtraSizeAvailable

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ishighlightdisableditems"></a>  CMFCMenuBar::IsHighlightDisabledItems

指示框架是否突出显示不可用的菜单项。

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>返回值

如果不可用的菜单项会突出显示; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

默认情况下，框架不突出显示不可用的菜单项时用户将鼠标指针定位过它们。 使用[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)方法来启用此功能。

##  <a name="ismenushadows"></a>  CMFCMenuBar::IsMenuShadows

指示框架是否绘制阴影对于弹出菜单。

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>返回值

如果框架绘制菜单阴影; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

使用[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)方法启用或禁用此功能。

##  <a name="isrecentlyusedmenus"></a>  CMFCMenuBar::IsRecentlyUsedMenus

指示是否在菜单栏上显示最近使用的菜单命令。

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>返回值

如果非零`CMFCMenuBar`对象会显示最近使用的菜单命令; 否则为 0。

### <a name="remarks"></a>备注

使用函数[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)来控制菜单栏显示最近使用过的菜单命令。

##  <a name="isshowallcommands"></a>  CMFCMenuBar::IsShowAllCommands

指示菜单是否显示所有命令。

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>返回值

如果非零`CMFCMenuBar`显示所有命令; 否则为 0。

### <a name="remarks"></a>备注

一个`CMFCMenuBar`对象可以配置为显示所有命令或都显示命令的一个子集。 有关此功能的详细信息，请参阅[CMFCMenuBar 类](../../mfc/reference/cmfcmenubar-class.md)。

`IsShowAllCommands` 告诉您如何为配置此功能`CMFCMenuBar`对象。 若要控制显示的菜单命令，使用方法[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)并[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)。

##  <a name="isshowallcommandsdelay"></a>  CMFCMenuBar::IsShowAllCommandsDelay

指示是否[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象一小段延迟后显示所有命令。

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>返回值

如果在菜单栏显示整个菜单一小段延迟; 后，非零值否则为 0。

### <a name="remarks"></a>备注

在配置为显示最近使用过的项的菜单栏时，菜单栏中两种方式之一显示完整菜单上：

- 当用户悬停在菜单的底部的箭头光标从通过编程方式设置延迟后会显示完整的菜单。

- 在用户单击菜单底部的箭头后会显示完整的菜单。

默认情况下，所有`CMFCMenuBar`对象使用的选项一小段延迟后显示完整的菜单。 此选项不能以编程方式在更改`CMFCMenuBar`类。 但是，用户可以更改行为工具栏自定义期间通过使用**自定义**对话框...

##  <a name="loadstate"></a>  CMFCMenuBar::LoadState

从 Windows 注册表加载菜单栏的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
[in]一个字符串，包含 Windows 注册表项的路径。

*nIndex*<br/>
[in]在菜单栏控件 ID。

*uiID*<br/>
[in]保留的值。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

使用[CMFCMenuBar::SaveState](#savestate)方法将菜单栏的状态保存到注册表。 已保存的信息包括菜单项、 停靠状态和菜单栏的位置。

在大多数情况下你的应用程序不会调用`LoadState`。 初始化工作区时，框架将调用此方法。

##  <a name="onchangehot"></a>  CMFCMenuBar::OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>参数

[in] *iHot*<br/>

### <a name="remarks"></a>备注

##  <a name="ondefaultmenuloaded"></a>  CMFCMenuBar::OnDefaultMenuLoaded

从资源文件加载该菜单资源时，框架将调用此方法。

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
[in]在菜单的句柄附加到`CMFCMenuBar`对象。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数可在框架从资源文件加载菜单资源后，执行自定义代码。

##  <a name="onsendcommand"></a>  CMFCMenuBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

[in] *pButton*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onsetdefaultbuttontext"></a>  CMFCMenuBar::OnSetDefaultButtonText

在用户更改文本的菜单栏上的某个项时，框架将调用此方法。

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

*pButton*<br/>
[in]一个指向[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)用户想要自定义的对象。

### <a name="return-value"></a>返回值

该框架将用户更改应用到菜单栏中; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法的默认实现为用户提供的文本更改按钮的文本。

##  <a name="ontoolhittest"></a>  CMFCMenuBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>参数

[in] *point*<br/>

[in] *pTI*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="pretranslatemessage"></a>  CMFCMenuBar::PreTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>参数

[in] *pMsg*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="restoreoriginalstate"></a>  CMFCMenuBar::RestoreOriginalstate

由框架调用，当用户选择**重置**从**自定义**对话框。

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>返回值

如果此方法成功，则非零值否则为 0。

### <a name="remarks"></a>备注

当用户选择调用此方法**重置**从自定义菜单。 您可以手动调用此方法以编程方式重置菜单栏的状态。 此方法从资源文件加载原始状态。

如果你想要执行任何处理，当用户选择重写此方法**重置**选项。

##  <a name="savestate"></a>  CMFCMenuBar::SaveState

保存的状态[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)到 Windows 注册表的对象。

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
[in]一个字符串，包含 Windows 注册表项的路径。

*nIndex*<br/>
[in]在菜单栏控件 ID。

*uiID*<br/>
[in]保留的值。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

通常情况下，你的应用程序不会调用`SaveState`。 在工作区进行序列化时，框架将调用此方法。 有关详细信息，请参阅[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)。

已保存的信息包括菜单项、 停靠状态和菜单栏的位置。

##  <a name="setdefaultmenuresid"></a>  CMFCMenuBar::SetDefaultMenuResId

设置的默认菜单[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象基于资源 id。

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>参数

*uiResId*<br/>
[in]新的默认菜单资源 ID。

### <a name="remarks"></a>备注

[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)方法从资源文件还原默认菜单。

使用[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)方法来检索默认菜单，但不会还原。

##  <a name="setforcedownarrows"></a>  CMFCMenuBar::SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>参数

[in] *bValue*<br/>

### <a name="remarks"></a>备注

##  <a name="setmaximizemode"></a>  CMFCMenuBar::SetMaximizeMode

当 MDI 更改其显示模式，必须更新菜单栏时，框架将调用此方法。

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>参数

*bMax*<br/>
[in]一个布尔值，指定的模式。 有关详细信息，请参阅备注部分。

*pWnd*<br/>
[in]指向正在更改的 MDI 子窗口的指针。

*bRecalcLayout*<br/>
[in]一个布尔值，指定是否应立即计算菜单条的布局。

### <a name="remarks"></a>备注

附加到 MDI 主框架窗口的菜单栏时的 MDI 子窗口已最大化，显示系统菜单并**最小化**，**最大化**并**关闭**按钮。 如果*bMax*为 TRUE 并*pWnd*不为 NULL，MDI 子窗口已最大化和菜单栏中必须加入额外的控件。 否则，在菜单栏返回到其常规状态。

##  <a name="setmenubuttonrtc"></a>  CMFCMenuBar::SetMenuButtonRTC

设置当用户创建菜单按钮时，框架使用的运行时类信息。

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>参数

*pMenuButtonRTC*<br/>
[in][CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)类的信息派生自[CMFCMenuButton 类](../../mfc/reference/cmfcmenubutton-class.md)。

### <a name="remarks"></a>备注

当用户将新的按钮添加到菜单栏时，框架将动态创建按钮。 默认情况下，它会创建`CMFCMenuButton`对象。 重写此方法以更改按钮则框架将创建的对象的类型。

##  <a name="setmenufont"></a>  CMFCMenuBar::SetMenuFont

在应用程序中设置所有菜单栏的字体。

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>参数

*lpLogFont*<br/>
[in]一个指向[LOGFONT](/windows/desktop/api/dimm/ns-dimm-__midl___midl_itf_dimm_0000_0000_0003)结构，它定义要设置的字体。

*bHorz*<br/>
[in]如果你想为 TRUE *lpLogFont*参数，以使用垂直字体，FALSE，如果想要用于水平字体。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

两种字体用于所有`CMFCMenuBar`对象。 这些单独的字体用于水平和垂直菜单栏。

字体设置是全局变量，也会影响所有`CMFCMenuBar`对象。

##  <a name="setrecentlyusedmenus"></a>  CMFCMenuBar::SetRecentlyUsedMenus

是否菜单栏显示最近使用过的菜单命令的控件。

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>参数

*bOn*<br/>
[in]一个布尔值，控制是否显示最近使用的菜单命令。

##  <a name="setshowallcommands"></a>  CMFCMenuBar::SetShowAllCommands

控制菜单是否显示所有可用命令。

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>参数

*bShowAllCommands*<br/>
[in]一个布尔参数，指定是否弹出菜单显示了所有的菜单命令。

### <a name="remarks"></a>备注

如果菜单未显示所有的菜单命令，它会隐藏很少使用的命令。 有关显示的菜单命令的详细信息，请参阅[CMFCMenuBar 类](../../mfc/reference/cmfcmenubar-class.md)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
