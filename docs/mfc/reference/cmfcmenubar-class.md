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
ms.openlocfilehash: 278feca6b64915d0cf789e8f68af3c3fdf9b3129
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78869926"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar 类

实现停靠的菜单栏。
有关更多详细信息，请参阅位于你的 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCMenuBar：： AdjustLocations](#adjustlocations)|（重写 `CMFCToolBar::AdjustLocations`。）|
|[CMFCMenuBar：： AllowChangeTextLabels](#allowchangetextlabels)|指定文本标签是否可显示在工具栏按钮上的 "图像" 下。 （重写[CMFCToolBar：： AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels)。）|
|[CMFCMenuBar：： AllowShowOnPaneMenu](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|
|[CMFCMenuBar：： CalcFixedLayout](#calcfixedlayout)|计算工具栏的水平大小。 （重写[CMFCToolBar：： CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout)。）|
|[CMFCMenuBar：： CalcLayout](#calclayout)|（重写 `CMFCToolBar::CalcLayout`。）|
|[CMFCMenuBar：： CalcMaxButtonHeight](#calcmaxbuttonheight)|计算工具栏中按钮的最大高度。 （重写[CMFCToolBar：： CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight)。）|
|[CMFCMenuBar：： CanBeClosed](#canbeclosed)|指定用户是否可以关闭工具栏。 （重写[CMFCToolBar：： CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed)。）|
|[CMFCMenuBar：： CanBeRestored](#canberestored)|确定系统是否可以在自定义后将工具栏还原到其原始状态。 （重写[CMFCToolBar：： CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。）|
|[CMFCMenuBar：： Create](#create)|创建一个菜单控件，并将其附加到 `CMFCMenuBar` 对象上。|
|[CMFCMenuBar：： CreateEx](#createex)|使用其他样式选项创建 `CMFCMenuBar` 对象。|
|[CMFCMenuBar：： CreateFromMenu](#createfrommenu)|初始化 `CMFCMenuBar` 的对象。 接受 HMENU 参数，该参数充当填充 `CMFCMenuBar`的模板。|
|[CMFCMenuBar：： EnableHelpCombobox](#enablehelpcombobox)|启用位于菜单栏右侧的 "**帮助**" 组合框。|
|[CMFCMenuBar：： EnableMenuShadows](#enablemenushadows)|指定是否为弹出菜单显示阴影。|
|[CMFCMenuBar：： GetAvailableExpandSize](#getavailableexpandsize)|（重写[CPane：： GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize)。）|
|[CMFCMenuBar：： GetColumnWidth](#getcolumnwidth)|返回工具栏按钮的宽度。 （重写[CMFCToolBar：： GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth)。）|
|[CMFCMenuBar：： GetDefaultMenu](#getdefaultmenu)|返回资源文件中的原始菜单的句柄。|
|[CMFCMenuBar：： GetDefaultMenuResId](#getdefaultmenuresid)|返回资源文件中的原始菜单的资源标识符。|
|[CMFCMenuBar：： GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar：： GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar：： GetHelpCombobox](#gethelpcombobox)|返回一个指向 "**帮助**" 组合框的指针。|
|[CMFCMenuBar：： GetHMenu](#gethmenu)|返回连接到 `CMFCMenuBar` 对象的菜单的句柄。|
|[CMFCMenuBar：： GetMenuFont](#getmenufont)|返回菜单对象的当前全局字体。|
|[CMFCMenuBar：： GetMenuItem](#getmenuitem)|返回与所提供的项索引相关联的工具栏按钮。|
|[CMFCMenuBar：： GetRowHeight](#getrowheight)|返回工具栏按钮的高度。 （重写[CMFCToolBar：： GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight)。）|
|[CMFCMenuBar：： GetSystemButton](#getsystembutton)||
|[CMFCMenuBar：： GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar：： GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar：： HighlightDisabledItems](#highlightdisableditems)|指示是否突出显示禁用的菜单项。|
|[CMFCMenuBar：： IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|确定工具栏是否可以显示具有扩展边框的按钮。 （重写[CMFCToolBar：： IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable)。）|
|[CMFCMenuBar：： IsHighlightDisabledItems](#ishighlightdisableditems)|指示是否突出显示禁用的项。|
|[CMFCMenuBar：： IsMenuShadows](#ismenushadows)|指示是否为弹出菜单绘制阴影。|
|[CMFCMenuBar：： IsRecentlyUsedMenus](#isrecentlyusedmenus)|指示最近使用的菜单命令是否显示在菜单栏上。|
|[CMFCMenuBar：： IsShowAllCommands](#isshowallcommands)|指示弹出菜单是否显示所有命令。|
|[CMFCMenuBar：： IsShowAllCommandsDelay](#isshowallcommandsdelay)|指示菜单在短暂延迟后是否显示所有命令。|
|[CMFCMenuBar：： LoadState](#loadstate)|从注册表加载 `CMFCMenuBar` 对象的状态。|
|[CMFCMenuBar：： OnChangeHot](#onchangehot)|当用户选择工具栏上的按钮时由框架调用。 （重写[CMFCToolBar：： OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot)。）|
|[CMFCMenuBar：： OnDefaultMenuLoaded](#ondefaultmenuloaded)|当框架窗口从资源文件加载默认菜单时由框架调用。|
|[CMFCMenuBar：： OnSendCommand](#onsendcommand)|（重写 `CMFCToolBar::OnSendCommand`。）|
|[CMFCMenuBar：： OnSetDefaultButtonText](#onsetdefaultbuttontext)|当菜单处于自定义模式并且用户更改菜单项的文本时由框架调用。|
|[CMFCMenuBar：： OnToolHitTest](#ontoolhittest)|（重写 `CMFCToolBar::OnToolHitTest`。）|
|[CMFCMenuBar：:P reTranslateMessage](#pretranslatemessage)|（重写 `CMFCToolBar::PreTranslateMessage`。）|
|[CMFCMenuBar：： RestoreOriginalstate](#restoreoriginalstate)|当菜单处于自定义模式并且用户为菜单栏选择 "**重置**" 时由框架调用。|
|[CMFCMenuBar：： SaveState](#savestate)|将 `CMFCMenuBar` 对象的状态保存到注册表中。|
|[CMFCMenuBar：： SetDefaultMenuResId](#setdefaultmenuresid)|设置资源文件中的原始菜单。|
|[CMFCMenuBar：： SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar：： SetMaximizeMode](#setmaximizemode)|当 MDI 子窗口更改其显示模式时由框架调用。 如果 MDI 子窗口新近最大化或不再最大化，则此方法会更新菜单栏。|
|[CMFCMenuBar：： SetMenuButtonRTC](#setmenubuttonrtc)|设置用户动态创建菜单按钮时生成的运行时类信息。|
|[CMFCMenuBar：： SetMenuFont](#setmenufont)|为应用程序中的所有菜单设置字体。|
|[CMFCMenuBar：： SetRecentlyUsedMenus](#setrecentlyusedmenus)|指定菜单栏是否显示最近使用的菜单命令。|
|[CMFCMenuBar：： SetShowAllCommands](#setshowallcommands)|指定菜单栏是否显示所有命令。|

## <a name="remarks"></a>备注

`CMFCMenuBar` 类是实现停靠功能的菜单栏。 它类似于工具栏，但它不能关闭-始终显示。

`CMFCMenuBar` 支持显示最近使用的菜单项对象的选项。 如果启用此选项，则在第一次查看时，`CMFCMenuBar` 仅显示可用命令的子集。 此后，最近使用的命令与命令的原始子集一起显示在一起。 此外，用户始终可以展开菜单来查看所有可用命令。 因此，每个可用命令都配置为经常显示，或仅在最近选择的命令时显示。

若要使用 `CMFCMenuBar` 对象，请将其嵌入主窗口框架对象。 处理 `WM_CREATE` 消息时，调用 `CMFCMenuBar::Create` 或 `CMFCMenuBar::CreateEx`。 无论使用哪种 create 函数，都将传入指向主框架窗口的指针。 然后通过调用[CFrameWndEx：： EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking)启用插接。 通过调用 CFrameWndEx，停靠此菜单[：:D ockpane](../../mfc/reference/cframewndex-class.md#dockpane)。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCMenuBar` 类中的各种方法。 该示例演示如何设置窗格的样式，启用 "自定义" 按钮，启用 "帮助" 框，为弹出菜单启用阴影，并更新菜单栏。 此代码片段是[IE 演示示例](../../overview/visual-cpp-samples.md)的一部分。

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

**标头：** afxmenubar

##  <a name="adjustlocations"></a>CMFCMenuBar：： AdjustLocations

调整菜单栏上菜单项的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>备注

##  <a name="allowchangetextlabels"></a>CMFCMenuBar：： AllowChangeTextLabels

确定是否允许在菜单栏中的图像下使用文本标签。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>返回值

如果用户可以选择在图像下显示文本标签，则返回 TRUE。

### <a name="remarks"></a>备注

##  <a name="allowshowonpanemenu"></a>CMFCMenuBar：： AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="calcfixedlayout"></a>CMFCMenuBar：： CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>parameters

中*bStretch*<br/>

中*bHorz*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="calclayout"></a>CMFCMenuBar：： CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>parameters

中*dwMode*<br/>

中*nLength*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="calcmaxbuttonheight"></a>CMFCMenuBar：： CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="canbeclosed"></a>CMFCMenuBar：： CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="canberestored"></a>CMFCMenuBar：： CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="create"></a>CMFCMenuBar：： Create

创建一个菜单控件，并将其附加到[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>parameters

*pParentWnd*<br/>
中指向新的 `CMFCMenuBar` 对象的父窗口的指针。

*dwStyle*<br/>
中新菜单栏的样式。

*nID*<br/>
中菜单栏的子窗口的 ID。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

构造 `CMFCMenuBar` 对象之后，必须调用 `Create`。 此方法创建 `CMFCMenuBar` 控件并将其附加到 `CMFCMenuBar` 对象。

有关工具栏样式的详细信息，请参阅[CBasePane：： SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle)。

##  <a name="createex"></a>CMFCMenuBar：： CreateEx

使用指定的扩展样式创建[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。

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

### <a name="parameters"></a>parameters

*pParentWnd*<br/>
中指向新 `CMFCMenuBar` 对象的父窗口的指针。

*dwCtrlStyle*<br/>
中新菜单栏的其他样式。

*dwStyle*<br/>
中新菜单栏的主样式。

*rcBorders*<br/>
中一个 `CRect` 参数，该参数指定 `CMFCMenuBar` 对象的边框的大小。

*nID*<br/>
中菜单栏的子窗口的 ID。

### <a name="return-value"></a>返回值

如果方法成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

除了使用工具栏样式以外，还应使用此函数，而不是使用[CMFCMenuBar：： Create](#create)来指定样式。 一些经常使用的附加样式是 TBSTYLE_TRANSPARENT 和 CBRS_TOP。

有关其他样式的列表，请参阅[Toolbar 控件和按钮样式](/windows/win32/Controls/toolbar-control-and-button-styles)、[公共控件样式](/windows/win32/Controls/common-control-styles)和[常见窗口样式](/windows/win32/winmsg/window-styles)。

### <a name="example"></a>示例

下面的示例演示如何使用 `CMFCMenuBar` 类的 `CreateEx` 方法。 此代码片段是[IE 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

##  <a name="createfrommenu"></a>CMFCMenuBar：： CreateFromMenu

初始化[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。 此方法对 HMENU 参数之后的 `CMFCMenuBar` 对象建模。

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>parameters

*hMenu*<br/>
中菜单资源的句柄。 `CreateFromMenu` 使用此资源作为 `CMFCMenuBar`的模板。

*bDefaultMenu*<br/>
中指示新菜单是否为默认菜单的布尔值。

*bForceUpdate*<br/>
中指示此方法是否强制菜单更新的布尔值。

### <a name="remarks"></a>备注

如果希望菜单控件具有与菜单资源相同的菜单项，请使用此方法。 调用[CMFCMenuBar：： Create](#create)或[CMFCMenuBar：： CreateEx](#createex)后，调用此方法。

##  <a name="enablehelpcombobox"></a>CMFCMenuBar：： EnableHelpCombobox

启用位于菜单栏右侧的 "**帮助**" 组合框。

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>parameters

*uiID*<br/>
中"**帮助**" 组合框的按钮的命令 ID。

*lpszPrompt*<br/>
中一个字符串，其中包含框架在组合框中显示的文本（如果它为空且不处于活动状态）。 例如，"在此处输入文本"。

*nComboBoxWidth*<br/>
中组合框按钮的宽度（以像素为单位）。

### <a name="remarks"></a>备注

"**帮助**" 组合框类似于 Microsoft Word 菜单栏中的 "**帮助**" 组合框。

当你在将*uiID*设置为0的情况下调用此方法时，此方法将隐藏组合框。 否则，此方法会自动在菜单栏右侧显示组合框。 调用此方法后，调用[CMFCMenuBar：： GetHelpCombobox](#gethelpcombobox)以获取指向插入的[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象的指针。

##  <a name="enablemenushadows"></a>CMFCMenuBar：： EnableMenuShadows

为弹出菜单启用阴影。

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>parameters

*bEnable*<br/>
中指示是否应为弹出菜单启用阴影的布尔型参数。

### <a name="remarks"></a>备注

此方法使用的算法非常复杂，可能会降低应用程序在速度较慢的系统上的性能。

##  <a name="getavailableexpandsize"></a>CMFCMenuBar：： GetAvailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getcolumnwidth"></a>CMFCMenuBar：： GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getdefaultmenu"></a>CMFCMenuBar：： GetDefaultMenu

检索原始菜单的句柄。 框架从资源文件加载原始菜单。

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>返回值

菜单资源的句柄。

### <a name="remarks"></a>备注

如果你的应用程序自定义菜单，则可以使用此方法检索原始菜单的句柄。

##  <a name="getdefaultmenuresid"></a>CMFCMenuBar：： GetDefaultMenuResId

检索默认菜单的资源标识符。

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>返回值

菜单资源标识符。

### <a name="remarks"></a>备注

框架从资源文件加载 `CMFCMenuBar` 对象的默认菜单。

##  <a name="getfloatpopupdirection"></a>CMFCMenuBar：： GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>parameters

中*pButton*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getforcedownarrows"></a>CMFCMenuBar：： GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="gethelpcombobox"></a>CMFCMenuBar：： GetHelpCombobox

返回一个指向 "**帮助**" 组合框的指针。

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>返回值

指向 "**帮助**" 组合框的指针。 如果 "**帮助**" 组合框处于隐藏或未启用状态，则为 NULL。

### <a name="remarks"></a>备注

"**帮助**" 组合框位于菜单栏的右侧。 调用方法[CMFCMenuBar：： EnableHelpCombobox](#enablehelpcombobox)以启用此组合框。

##  <a name="gethmenu"></a>CMFCMenuBar：： GetHMenu

检索附加到[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象的菜单的句柄。

```
HMENU GetHMenu() const;
```

##  <a name="getmenufont"></a>CMFCMenuBar：： GetMenuFont

检索当前菜单字体。

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>parameters

*bHorz*<br/>
中指定是否返回水平或垂直字体的布尔型参数。 如果为 TRUE，则指示水平字体。

### <a name="return-value"></a>返回值

指向包含当前菜单栏字体的[CFont](../../mfc/reference/cfont-class.md)参数的指针。

### <a name="remarks"></a>备注

返回的字体是应用程序的全局参数。 为所有 `CMFCMenuBar` 对象维护两种全局字体。 这些单独的字体用于水平和垂直菜单栏。

##  <a name="getmenuitem"></a>CMFCMenuBar：： GetMenuItem

基于项索引检索菜单栏上的[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)对象。

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>parameters

*iItem*<br/>
中要返回的菜单项的索引。

### <a name="return-value"></a>返回值

指向与*iItem*指定的索引相匹配的 `CMFCToolBarButton` 对象的指针。 如果索引无效，则为 NULL。

##  <a name="getrowheight"></a>CMFCMenuBar：： GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getsystembutton"></a>CMFCMenuBar：： GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>parameters

中*uiBtn*<br/>

中*bByCommand*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getsystembuttonscount"></a>CMFCMenuBar：： GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getsystemmenu"></a>CMFCMenuBar：： GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="highlightdisableditems"></a>CMFCMenuBar：： HighlightDisabledItems

控制框架是否突出显示禁用的菜单项。

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>parameters

*bHighlight*<br/>
中一个布尔参数，指示框架是否突出显示不可用菜单项。

### <a name="remarks"></a>备注

默认情况下，当用户将鼠标指针置于其上方时，框架不会突出显示 "不可用" 菜单项。

##  <a name="isbuttonextrasizeavailable"></a>CMFCMenuBar：： IsButtonExtraSizeAvailable

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ishighlightdisableditems"></a>CMFCMenuBar：： IsHighlightDisabledItems

指示框架是否突出显示不可用菜单项。

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>返回值

如果突出显示 "不可用" 菜单项，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

默认情况下，当用户将鼠标指针置于其上方时，框架不会突出显示 "不可用" 菜单项。 使用[CMFCMenuBar：： HighlightDisabledItems](#highlightdisableditems)方法启用此功能。

##  <a name="ismenushadows"></a>CMFCMenuBar：： IsMenuShadows

指示框架是否为弹出菜单绘制阴影。

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>返回值

如果框架绘制菜单阴影，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

使用[CMFCMenuBar：： EnableMenuShadows](#enablemenushadows)方法启用或禁用此功能。

##  <a name="isrecentlyusedmenus"></a>CMFCMenuBar：： IsRecentlyUsedMenus

指示最近使用的菜单命令是否显示在菜单栏上。

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>返回值

如果 `CMFCMenuBar` 对象显示最近使用的菜单命令，则为非零值;否则为0。

### <a name="remarks"></a>备注

使用函数[CMFCMenuBar：： SetRecentlyUsedMenus](#setrecentlyusedmenus)来控制菜单栏是否显示最近使用的菜单命令。

##  <a name="isshowallcommands"></a>CMFCMenuBar：： IsShowAllCommands

指示菜单是否显示所有命令。

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>返回值

如果 `CMFCMenuBar` 显示所有命令，则为非零值;否则为0。

### <a name="remarks"></a>备注

可以将 `CMFCMenuBar` 对象配置为显示所有命令，或仅显示部分命令。 有关此功能的详细信息，请参阅[CMFCMenuBar 类](../../mfc/reference/cmfcmenubar-class.md)。

`IsShowAllCommands` 将告诉您如何为 `CMFCMenuBar` 对象配置此功能。 若要控制显示的菜单命令，请使用方法[CMFCMenuBar：： SetShowAllCommands](#setshowallcommands)和[CMFCMenuBar：： SetRecentlyUsedMenus](#setrecentlyusedmenus)。

##  <a name="isshowallcommandsdelay"></a>CMFCMenuBar：： IsShowAllCommandsDelay

指示[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象是否在短暂延迟后显示所有命令。

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>返回值

如果菜单栏在短暂延迟后显示完全菜单，则为非零值;否则为0。

### <a name="remarks"></a>备注

将菜单栏配置为显示最近使用的项目时，菜单栏会以下列两种方式之一显示 "完全" 菜单：

- 当用户将光标悬停在菜单底部的箭头上方时，将在程控延迟后显示完全菜单。

- 用户单击菜单底部的箭头后，显示 "完全" 菜单。

默认情况下，所有 `CMFCMenuBar` 对象将使用选项在短暂延迟后显示完全菜单。 此选项不能在 `CMFCMenuBar` 类中以编程方式进行更改。 但是，用户可以通过使用 "**自定义**" 对话框，在自定义工具栏期间更改行为。

##  <a name="loadstate"></a>CMFCMenuBar：： LoadState

从 Windows 注册表加载菜单栏的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>parameters

*lpszProfileName*<br/>
中一个字符串，其中包含 Windows 注册表项的路径。

*nIndex*<br/>
中菜单栏的控件 ID。

*uiID*<br/>
中保留值。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

使用[CMFCMenuBar：： SaveState](#savestate)方法将菜单栏的状态保存到注册表。 保存的信息包括菜单项、停靠状态和菜单栏的位置。

在大多数情况下，应用程序不会调用 `LoadState`。 框架在初始化工作区时调用此方法。

##  <a name="onchangehot"></a>CMFCMenuBar：： OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>parameters

中*iHot*<br/>

### <a name="remarks"></a>备注

##  <a name="ondefaultmenuloaded"></a>CMFCMenuBar：： OnDefaultMenuLoaded

在从资源文件加载菜单资源时，框架会调用此方法。

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>parameters

*hMenu*<br/>
中附加到 `CMFCMenuBar` 对象的菜单的句柄。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 在框架从资源文件加载菜单资源后，重写此函数以执行自定义代码。

##  <a name="onsendcommand"></a>CMFCMenuBar：： OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>parameters

中*pButton*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onsetdefaultbuttontext"></a>CMFCMenuBar：： OnSetDefaultButtonText

当用户更改菜单栏上项的文本时，框架会调用此方法。

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>parameters

*pButton*<br/>
中指向用户要自定义的[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果框架将用户更改应用于菜单栏，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法的默认实现将该按钮的文本更改为用户提供的文本。

##  <a name="ontoolhittest"></a>CMFCMenuBar：： OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>parameters

中*点*<br/>

中*pTI*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="pretranslatemessage"></a>CMFCMenuBar：:P reTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>parameters

中*pMsg*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="restoreoriginalstate"></a>CMFCMenuBar：： RestoreOriginalstate

当用户从 "**自定义**" 对话框中选择 "**重置**" 时由框架调用。

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>返回值

如果方法成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

当用户从 "自定义" 菜单中选择 "**重置**" 时，将调用此方法。 还可以手动调用此方法，以编程方式重置菜单栏的状态。 此方法从资源文件加载原始状态。

如果要在用户选择**重置**选项时进行任何处理，请重写此方法。

##  <a name="savestate"></a>CMFCMenuBar：： SaveState

将[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象的状态保存到 Windows 注册表中。

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>parameters

*lpszProfileName*<br/>
中一个字符串，其中包含 Windows 注册表项的路径。

*nIndex*<br/>
中菜单栏的控件 ID。

*uiID*<br/>
中保留值。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE;否则为 FALSE;

### <a name="remarks"></a>备注

通常，应用程序不会调用 `SaveState`。 当对工作区进行序列化时，框架会调用此方法。 有关详细信息，请参阅[CWinAppEx：： SaveState](../../mfc/reference/cwinappex-class.md#savestate)。

保存的信息包括菜单项、停靠状态和菜单栏的位置。

##  <a name="setdefaultmenuresid"></a>CMFCMenuBar：： SetDefaultMenuResId

基于资源 ID 设置[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象的默认菜单。

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>parameters

*uiResId*<br/>
中新的默认菜单的资源 ID。

### <a name="remarks"></a>备注

[CMFCMenuBar：： RestoreOriginalstate](#restoreoriginalstate)方法从资源文件还原默认菜单。

使用[CMFCMenuBar：： GetDefaultMenuResId](#getdefaultmenuresid)方法检索默认菜单而不还原它。

##  <a name="setforcedownarrows"></a>CMFCMenuBar：： SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>parameters

中*bValue*<br/>

### <a name="remarks"></a>备注

##  <a name="setmaximizemode"></a>CMFCMenuBar：： SetMaximizeMode

当 MDI 更改其显示模式并且必须更新菜单栏时，框架会调用此方法。

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>parameters

*bMax*<br/>
中指定模式的布尔值。 有关详细信息，请参阅“备注”部分。

*pWnd*<br/>
中指向正在更改的 MDI 子窗口的指针。

*bRecalcLayout*<br/>
中一个布尔值，指定是否应立即重新计算菜单栏的布局。

### <a name="remarks"></a>备注

当最大化 MDI 子窗口时，附加到 MDI 主框架窗口的菜单栏会显示 "系统" 菜单以及 "**最小化**"、"**最大化**" 和 "**关闭**" 按钮。 如果*bMax*为 TRUE 且*PWND*不为 NULL，则将最大化 MDI 子窗口，并且菜单栏必须包含额外的控件。 否则，菜单栏将恢复为其正常状态。

##  <a name="setmenubuttonrtc"></a>CMFCMenuBar：： SetMenuButtonRTC

设置框架在用户创建菜单按钮时所使用的运行时类信息。

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>parameters

*pMenuButtonRTC*<br/>
中派生自[CMFCMenuButton 类](../../mfc/reference/cmfcmenubutton-class.md)的类的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)信息。

### <a name="remarks"></a>备注

当用户将新按钮添加到菜单栏时，框架会动态创建按钮。 默认情况下，它会创建 `CMFCMenuButton` 对象。 重写此方法以更改框架创建的 button 对象的类型。

##  <a name="setmenufont"></a>CMFCMenuBar：： SetMenuFont

设置应用程序中所有菜单栏的字体。

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>parameters

*lpLogFont*<br/>
中指向[LOGFONT](/windows/win32/api/dimm/ns-dimm-logfonta)结构的指针，该结构定义要设置的字体。

*bHorz*<br/>
中如果希望将*lpLogFont*参数用于直排字体，则为 TRUE; 如果希望将该参数用于水平字体，则为 FALSE。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

对于所有 `CMFCMenuBar` 对象使用两种字体。 这些单独的字体用于水平和垂直菜单栏。

字体设置是全局变量，会影响所有 `CMFCMenuBar` 对象。

##  <a name="setrecentlyusedmenus"></a>CMFCMenuBar：： SetRecentlyUsedMenus

控制菜单栏是否显示最近使用的菜单命令。

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>parameters

*bOn*<br/>
中用于控制最近使用的菜单命令是否显示的布尔值。

##  <a name="setshowallcommands"></a>CMFCMenuBar：： SetShowAllCommands

控制菜单是否显示所有可用命令。

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>parameters

*bShowAllCommands*<br/>
中一个布尔参数，指定弹出菜单是否显示所有菜单命令。

### <a name="remarks"></a>备注

如果菜单未显示所有菜单命令，它将隐藏很少使用的命令。 有关显示菜单命令的详细信息，请参阅[CMFCMenuBar 类](../../mfc/reference/cmfcmenubar-class.md)。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
