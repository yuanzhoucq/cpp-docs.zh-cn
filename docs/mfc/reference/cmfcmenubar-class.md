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
ms.openlocfilehash: 50dd488d1f59c99b8fee1eb96acf6d0041547df9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369689"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar 类

实现停靠的菜单栏。
有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|（重写 `CMFCToolBar::AdjustLocations`。）|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|指定文本标签是否可以显示在工具栏按钮上的图像下。 （覆盖[CMFC 工具栏：：允许更改文本标签](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).）|
|[CMFC菜单栏：：允许显示帕内菜单](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|
|[CMFC菜单栏：钙固定布局](#calcfixedlayout)|计算工具栏的水平大小。 （覆盖[CMFCTool 栏：CalcFixed布局](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).）|
|[CMFC菜单栏：卡路里布局](#calclayout)|（重写 `CMFCToolBar::CalcLayout`。）|
|[CMFC菜单栏：：卡尔马克斯按钮高度](#calcmaxbuttonheight)|计算工具栏中按钮的最大高度。 （覆盖[CMFC 工具栏：：CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).）|
|[CMFC菜单栏：可关闭](#canbeclosed)|指定用户是否可以关闭工具栏。 （覆盖[CMFC 工具栏：：可以关闭](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).）|
|[CMFC菜单栏：可还原](#canberestored)|确定系统在自定义后是否可以将工具栏还原到其原始状态。 （覆盖[CMFCTool 栏：可以还原](../../mfc/reference/cmfctoolbar-class.md#canberestored).）|
|[CMFC菜单栏：创建](#create)|创建菜单控件并将其附加到`CMFCMenuBar`对象。|
|[CMFC菜单栏：创建Ex](#createex)|创建具有`CMFCMenuBar`其他样式选项的对象。|
|[CMFC菜单栏：从Menu创建](#createfrommenu)|初始化`CMFCMenuBar`对象。 接受充当填充`CMFCMenuBar`的模板的 HMENU 参数。|
|[CMFC菜单栏：启用帮助Combobox](#enablehelpcombobox)|启用位于菜单栏右侧**的帮助**组合框。|
|[CMFC菜单栏：启用菜单阴影](#enablemenushadows)|指定是否显示弹出式菜单的阴影。|
|[CMFCMenuBar：：获取可用扩展大小](#getavailableexpandsize)|（覆盖[CPane：获取可用扩展大小](../../mfc/reference/cpane-class.md#getavailableexpandsize)。|
|[CMFC菜单栏：获取柱宽度](#getcolumnwidth)|返回工具栏按钮的宽度。 （覆盖[CMFC 工具栏：获取柱宽度](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).）|
|[CMFC菜单栏：：获取默认菜单](#getdefaultmenu)|返回资源文件中原始菜单的句柄。|
|[CMFC菜单栏：获取默认菜单Resid](#getdefaultmenuresid)|返回资源文件中原始菜单的资源标识符。|
|[CMFC菜单栏：获取浮动弹出方向](#getfloatpopupdirection)||
|[CMFC菜单栏：获取力量向下箭头](#getforcedownarrows)||
|[CMFC菜单栏：获取帮助Combobox](#gethelpcombobox)|返回指向 **"帮助**组合"框的指针。|
|[CMFC菜单栏：获取HMenu](#gethmenu)|返回附加到对象的菜单的`CMFCMenuBar`句柄。|
|[CMFC菜单栏：获取菜单方](#getmenufont)|返回菜单对象的当前全局字体。|
|[CMFC菜单栏：获取菜单项目](#getmenuitem)|返回与提供的物料索引关联的工具栏按钮。|
|[CMFC菜单栏：获取罗高](#getrowheight)|返回工具栏按钮的高度。 （覆盖[CMFC 工具栏：获取罗高](../../mfc/reference/cmfctoolbar-class.md#getrowheight).）|
|[CMFC菜单栏：获取系统按钮](#getsystembutton)||
|[CMFC菜单栏：获取系统按钮计数](#getsystembuttonscount)||
|[CMFC菜单：获取系统菜单](#getsystemmenu)||
|[CMFC菜单栏：：突出显示禁用项目](#highlightdisableditems)|指示是否突出显示禁用的菜单项。|
|[CMFC菜单栏：是按钮外尺寸可用](#isbuttonextrasizeavailable)|确定工具栏是否可以显示具有扩展边框的按钮。 （覆盖[CMFC 工具栏：是按钮外大尺寸](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).）|
|[CMFC菜单栏：是突出显示的禁用项目](#ishighlightdisableditems)|指示是否突出显示已禁用的项目。|
|[CMFC菜单栏：：正菜单阴影](#ismenushadows)|指示是否为弹出式菜单绘制阴影。|
|[CMFCMenuBar：是最近使用的菜单](#isrecentlyusedmenus)|指示菜单栏上是否显示最近使用的菜单命令。|
|[CMFC菜单栏：：是显示所有命令](#isshowallcommands)|指示弹出式菜单是否显示所有命令。|
|[CMFC菜单栏：：是显示所有命令延迟](#isshowallcommandsdelay)|指示菜单在短暂延迟后是否显示所有命令。|
|[CMFC菜单栏：加载状态](#loadstate)|从注册表加载`CMFCMenuBar`对象的状态。|
|[CMFC菜单栏：上更改热](#onchangehot)|当用户选择工具栏上的按钮时，框架调用。 （覆盖[CMFC 工具栏：打开更改热](../../mfc/reference/cmfctoolbar-class.md#onchangehot).）|
|[CMFC菜单栏：打开默认菜单加载](#ondefaultmenuloaded)|当框架窗口从资源文件加载默认菜单时，框架调用。|
|[CMFC菜单栏：打开发送命令](#onsendcommand)|（重写 `CMFCToolBar::OnSendCommand`。）|
|[CMFC菜单栏：打开默认按钮文本](#onsetdefaultbuttontext)|当菜单处于自定义模式且用户更改菜单项的文本时，由框架调用。|
|[CMFCMenuBar：：在工具命中测试](#ontoolhittest)|（重写 `CMFCToolBar::OnToolHitTest`。）|
|[CMFCMenuBar：:P重新翻译消息](#pretranslatemessage)|（重写 `CMFCToolBar::PreTranslateMessage`。）|
|[CMFCMenuBar：恢复原始状态](#restoreoriginalstate)|当菜单处于自定义模式且用户为菜单栏选择 **"重置"** 时，由框架调用。|
|[CMFC菜单栏：保存状态](#savestate)|将`CMFCMenuBar`对象的状态保存到注册表。|
|[CMFC菜单栏：：设置默认菜单Resid](#setdefaultmenuresid)|在资源文件中设置原始菜单。|
|[CMFC菜单栏：设置强制向下箭头](#setforcedownarrows)||
|[CMFC菜单栏：：设置最大化模式](#setmaximizemode)|当 MDI 子窗口更改其显示模式时，由框架调用。 如果 MDI 子窗口是新最大化或不再最大化，此方法将更新菜单栏。|
|[CMFC菜单栏：设置菜单按钮RTC](#setmenubuttonrtc)|设置用户动态创建菜单按钮时生成的运行时类信息。|
|[CMFCMenuBar：setMenuFont](#setmenufont)|设置应用程序中所有菜单的字体。|
|[CMFC菜单栏：设置最近使用的菜单](#setrecentlyusedmenus)|指定菜单栏是否显示最近使用的菜单命令。|
|[CMFC菜单栏：：设置显示所有命令](#setshowallcommands)|指定菜单栏是否显示所有命令。|

## <a name="remarks"></a>备注

类`CMFCMenuBar`是实现停靠功能的菜单栏。 它类似于工具栏，尽管它无法关闭 - 它总是显示。

`CMFCMenuBar`支持显示最近使用的菜单项对象的选项。 如果启用此选项，则第`CMFCMenuBar`一次查看时仅显示可用命令的子集。 此后，最近使用的命令与命令的原始子集一起显示。 此外，用户始终可以展开菜单以查看所有可用的命令。 因此，每个可用命令都配置为持续显示，或仅在最近选择时显示。

要使用对象`CMFCMenuBar`，请将它嵌入到主窗口框架对象中。 处理`WM_CREATE`消息时，调用`CMFCMenuBar::Create`或`CMFCMenuBar::CreateEx`。 无论您使用哪种创建函数，都会将指针传递到主框架窗口。 然后通过调用[CFrameWndEx：：启用停靠](../../mfc/reference/cframewndex-class.md#enabledocking)来启用停靠。 通过调用[CFrameWndEx：:DockPane](../../mfc/reference/cframewndex-class.md#dockpane)）来停靠此菜单。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCMenuBar` 类中的各种方法。 该示例演示如何设置窗格的样式、启用自定义按钮、启用帮助框、为弹出式菜单启用阴影以及更新菜单栏。 此代码段是[IE 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具栏](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>要求

**标题：** afxmenubar.h

## <a name="cmfcmenubaradjustlocations"></a><a name="adjustlocations"></a>CMFC菜单栏：调整位置

调整菜单栏上菜单项的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>备注

## <a name="cmfcmenubarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFC菜单栏：允许更改文本标签

确定菜单栏中的图像下是否允许文本标签。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>返回值

如果用户可以选择在图像下显示文本标签，则返回 TRUE。

### <a name="remarks"></a>备注

## <a name="cmfcmenubarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFC菜单栏：：允许显示帕内菜单

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFC菜单栏：钙固定布局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

[在]*b 拉伸*<br/>

[在]*布霍兹*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarcalclayout"></a><a name="calclayout"></a>CMFC菜单栏：卡路里布局

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>参数

[在]*dwMode*<br/>

[在]*n 长度*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarcalcmaxbuttonheight"></a><a name="calcmaxbuttonheight"></a>CMFC菜单栏：：卡尔马克斯按钮高度

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarcanbeclosed"></a><a name="canbeclosed"></a>CMFC菜单栏：可关闭

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarcanberestored"></a><a name="canberestored"></a>CMFC菜单栏：可还原

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarcreate"></a><a name="create"></a>CMFC菜单栏：创建

创建菜单控件并将其附加到[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
[在]指向新`CMFCMenuBar`对象的父窗口。

*dwStyle*<br/>
[在]新菜单栏的样式。

*nID*<br/>
[在]菜单栏的子窗口的 ID。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

构造`CMFCMenuBar`对象后，必须调用`Create`。 此方法创建`CMFCMenuBar`控件并将其附加到`CMFCMenuBar`对象。

有关工具栏样式的详细信息，请参阅[CBasePane：：设置窗格样式](../../mfc/reference/cbasepane-class.md#setpanestyle)。

## <a name="cmfcmenubarcreateex"></a><a name="createex"></a>CMFC菜单栏：创建Ex

创建具有指定扩展样式的[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。

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

*pparentwnd*<br/>
[在]指向新`CMFCMenuBar`对象的父窗口。

*dwCtrl风格*<br/>
[在]新菜单栏的其他样式。

*dwStyle*<br/>
[在]新菜单栏的主样式。

*rcBorders*<br/>
[在]指定`CRect``CMFCMenuBar`对象边框大小的参数。

*nID*<br/>
[在]菜单栏的子窗口的 ID。

### <a name="return-value"></a>返回值

如果方法成功，则非零;否则 0。

### <a name="remarks"></a>备注

除了工具栏样式之外，还应使用此函数而不是[CMFCMenuBar：：在](#create)指定样式时创建。 TBSTYLE_TRANSPARENT和CBRS_TOP一些常用的其他样式。

有关其他样式的列表，请参阅[工具栏控件和按钮样式](/windows/win32/Controls/toolbar-control-and-button-styles)、[常见控件样式](/windows/win32/Controls/common-control-styles)和[常见窗口样式](/windows/win32/winmsg/window-styles)。

### <a name="example"></a>示例

下面的示例演示如何使用`CreateEx``CMFCMenuBar`类的方法。 此代码段是[IE 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

## <a name="cmfcmenubarcreatefrommenu"></a><a name="createfrommenu"></a>CMFC菜单栏：从Menu创建

初始化[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。 此方法在`CMFCMenuBar`HMENU 参数后对对象建模。

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
[在]菜单资源的句柄。 `CreateFromMenu`使用此资源作为 的`CMFCMenuBar`模板。

*b默认菜单*<br/>
[在]指示新菜单是否为默认菜单的布尔。

*bForce更新*<br/>
[在]指示此方法是否强制菜单更新的布尔。

### <a name="remarks"></a>备注

如果希望菜单控件具有与菜单资源相同的菜单项，请使用此方法。 调用[CMFCMenuBar：：：创建](#create)或[CMFCMenuBar：：createEx](#createex)后，调用此方法。

## <a name="cmfcmenubarenablehelpcombobox"></a><a name="enablehelpcombobox"></a>CMFC菜单栏：启用帮助Combobox

启用位于菜单栏右侧**的帮助**组合框。

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[在]**"帮助**组合"框按钮的命令 ID。

*lpszPrompt*<br/>
[在]包含框架在组合框中显示的文本（如果文本为空且不处于活动状态）的字符串。 例如，"在此处输入文本"。

*nComboBox宽度*<br/>
[在]组合框的按钮宽度（以像素为单位）。

### <a name="remarks"></a>备注

**"帮助**组合"框类似于 Microsoft Word 菜单栏中的 **"帮助**组合"框。

当您使用*uiID*设置为 0 调用此方法时，此方法将隐藏组合框。 否则，此方法会自动在菜单栏的右侧显示组合框。 调用此方法后，调用[CMFCMenuBar：：获取帮助Combobox](#gethelpcombobox)以获取指向插入[的 CMFCToolBarComboxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象的指针。

## <a name="cmfcmenubarenablemenushadows"></a><a name="enablemenushadows"></a>CMFC菜单栏：启用菜单阴影

为弹出式菜单启用阴影。

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]布尔参数，指示是否应为弹出式菜单启用阴影。

### <a name="remarks"></a>备注

此方法使用的算法很复杂，可能会降低应用程序在较慢系统上的性能。

## <a name="cmfcmenubargetavailableexpandsize"></a><a name="getavailableexpandsize"></a>CMFCMenuBar：：获取可用扩展大小

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubargetcolumnwidth"></a><a name="getcolumnwidth"></a>CMFC菜单栏：获取柱宽度

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubargetdefaultmenu"></a><a name="getdefaultmenu"></a>CMFC菜单栏：：获取默认菜单

检索原始菜单的句柄。 框架从资源文件加载原始菜单。

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>返回值

菜单资源的句柄。

### <a name="remarks"></a>备注

如果应用程序自定义菜单，则可以使用此方法检索原始菜单的句柄。

## <a name="cmfcmenubargetdefaultmenuresid"></a><a name="getdefaultmenuresid"></a>CMFC菜单栏：获取默认菜单Resid

检索默认菜单的资源标识符。

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>返回值

菜单资源标识符。

### <a name="remarks"></a>备注

框架从资源文件加载`CMFCMenuBar`对象的默认菜单。

## <a name="cmfcmenubargetfloatpopupdirection"></a><a name="getfloatpopupdirection"></a>CMFC菜单栏：获取浮动弹出方向

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>参数

[在]*pButton*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubargetforcedownarrows"></a><a name="getforcedownarrows"></a>CMFC菜单栏：获取力量向下箭头

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubargethelpcombobox"></a><a name="gethelpcombobox"></a>CMFC菜单栏：获取帮助Combobox

返回指向 **"帮助**组合"框的指针。

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>返回值

指向 **"帮助**组合"框的指针。 如果 **"帮助**组合"框处于隐藏状态或未启用，则为 NULL。

### <a name="remarks"></a>备注

**"帮助**组合"框位于菜单栏的右侧。 调用方法[CMFCMenuBar：启用帮助Combobox](#enablehelpcombobox)以启用此组合框。

## <a name="cmfcmenubargethmenu"></a><a name="gethmenu"></a>CMFC菜单栏：获取HMenu

检索附加到[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象的菜单的句柄。

```
HMENU GetHMenu() const;
```

## <a name="cmfcmenubargetmenufont"></a><a name="getmenufont"></a>CMFC菜单栏：获取菜单方

检索当前菜单字体。

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>参数

*布霍兹*<br/>
[在]指定是返回水平字体还是垂直字体的布尔参数。 TRUE 表示水平字体。

### <a name="return-value"></a>返回值

指向包含当前菜单栏字体的[CFont](../../mfc/reference/cfont-class.md)参数的指针。

### <a name="remarks"></a>备注

返回的字体是应用程序的全局参数。 为所有`CMFCMenuBar`对象维护两个全局字体。 这些单独的字体用于水平和垂直菜单栏。

## <a name="cmfcmenubargetmenuitem"></a><a name="getmenuitem"></a>CMFC菜单栏：获取菜单项目

根据项目索引在菜单栏上检索[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)对象。

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>参数

*iItem*<br/>
[在]要返回的菜单项的索引。

### <a name="return-value"></a>返回值

指向与`CMFCToolBarButton`*iItem*指定的索引匹配的对象的指针。 如果索引无效，则为 NULL。

## <a name="cmfcmenubargetrowheight"></a><a name="getrowheight"></a>CMFC菜单栏：获取罗高

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubargetsystembutton"></a><a name="getsystembutton"></a>CMFC菜单栏：获取系统按钮

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>参数

[在]*乌伊布滕*<br/>

[在]*bByCommand*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubargetsystembuttonscount"></a><a name="getsystembuttonscount"></a>CMFC菜单栏：获取系统按钮计数

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubargetsystemmenu"></a><a name="getsystemmenu"></a>CMFC菜单：获取系统菜单

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarhighlightdisableditems"></a><a name="highlightdisableditems"></a>CMFC菜单栏：：突出显示禁用项目

控制框架是否突出显示禁用的菜单项。

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>参数

*b 高光*<br/>
[在]一个布尔参数，指示框架是否突出显示不可用的菜单项。

### <a name="remarks"></a>备注

默认情况下，当用户将鼠标指针放在它们上时，框架不会突出显示不可用的菜单项。

## <a name="cmfcmenubarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFC菜单栏：是按钮外尺寸可用

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarishighlightdisableditems"></a><a name="ishighlightdisableditems"></a>CMFC菜单栏：是突出显示的禁用项目

指示框架是否突出显示不可用的菜单项。

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>返回值

如果突出显示不可用的菜单项，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

默认情况下，当用户将鼠标指针放在它们上时，框架不会突出显示不可用的菜单项。 使用[CMFCMenuBar：突出显示禁用项目](#highlightdisableditems)方法启用此功能。

## <a name="cmfcmenubarismenushadows"></a><a name="ismenushadows"></a>CMFC菜单栏：：正菜单阴影

指示框架是否为弹出式菜单绘制阴影。

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>返回值

如果框架绘制菜单阴影，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

使用[CMFCMenuBar：启用MenuShadows](#enablemenushadows)方法启用或禁用此功能。

## <a name="cmfcmenubarisrecentlyusedmenus"></a><a name="isrecentlyusedmenus"></a>CMFCMenuBar：是最近使用的菜单

指示菜单栏上是否显示最近使用的菜单命令。

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>返回值

如果对象显示最近`CMFCMenuBar`使用的菜单命令，则非零;否则 0。

### <a name="remarks"></a>备注

使用函数[CMFCMenuBar：设置最近使用菜单](#setrecentlyusedmenus)来控制菜单栏是否显示最近使用的菜单命令。

## <a name="cmfcmenubarisshowallcommands"></a><a name="isshowallcommands"></a>CMFC菜单栏：：是显示所有命令

指示菜单是否显示所有命令。

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>返回值

如果显示所有命令`CMFCMenuBar`，则非零;否则 0。

### <a name="remarks"></a>备注

可以将`CMFCMenuBar`对象配置为显示所有命令或仅显示命令的子集。 有关此功能的详细信息，请参阅[CMFCMenuBar 类](../../mfc/reference/cmfcmenubar-class.md)。

`IsShowAllCommands`将告诉您如何为`CMFCMenuBar`对象配置此功能。 要控制显示哪些菜单命令，请使用[CMFCMenuBar：：SetShowAll命令](#setshowallcommands)和[CMFCMenuBar：：设置最近使用的菜单](#setrecentlyusedmenus)。

## <a name="cmfcmenubarisshowallcommandsdelay"></a><a name="isshowallcommandsdelay"></a>CMFC菜单栏：：是显示所有命令延迟

指示[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象在短暂延迟后是否显示所有命令。

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>返回值

如果菜单栏在短暂延迟后显示完整菜单，则非零;否则 0。

### <a name="remarks"></a>备注

将菜单栏配置为显示最近使用的项目时，菜单栏以以下两种方式之一显示完整菜单：

- 在用户将光标悬停在菜单底部的箭头上时，在编程延迟后显示完整菜单。

- 用户单击菜单底部的箭头后显示完整菜单。

默认情况下，所有`CMFCMenuBar`对象都使用 该选项在短暂延迟后显示完整菜单。 此选项无法在`CMFCMenuBar`类中以编程方式更改。 但是，用户可以使用 **"自定义"** 对话框更改工具栏自定义期间的行为。

## <a name="cmfcmenubarloadstate"></a><a name="loadstate"></a>CMFC菜单栏：加载状态

从 Windows 注册表加载菜单栏的状态。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]包含 Windows 注册表项路径的字符串。

*nIndex*<br/>
[在]菜单栏的控制 ID。

*uiID*<br/>
[在]保留值。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

使用[CMFCMenuBar：：保存状态](#savestate)方法将菜单栏的状态保存到注册表。 保存的信息包括菜单项、停靠状态和菜单栏的位置。

在大多数情况下，您的应用程序不调用`LoadState`。 框架在初始化工作区时调用此方法。

## <a name="cmfcmenubaronchangehot"></a><a name="onchangehot"></a>CMFC菜单栏：上更改热

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>参数

[在]*iHot*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcmenubarondefaultmenuloaded"></a><a name="ondefaultmenuloaded"></a>CMFC菜单栏：打开默认菜单加载

当框架从资源文件加载菜单资源时，它将调用此方法。

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
[在]附加到对象的菜单的`CMFCMenuBar`句柄。

### <a name="remarks"></a>备注

此函数的默认实现不执行任何操作。 重写此函数，在框架从资源文件中加载菜单资源后执行自定义代码。

## <a name="cmfcmenubaronsendcommand"></a><a name="onsendcommand"></a>CMFC菜单栏：打开发送命令

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

[在]*pButton*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubaronsetdefaultbuttontext"></a><a name="onsetdefaultbuttontext"></a>CMFC菜单栏：打开默认按钮文本

当用户更改菜单栏上的项的文本时，框架将调用此方法。

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

*pButton*<br/>
[在]指向用户要自定义的[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)对象的指针。

### <a name="return-value"></a>返回值

如果框架将用户更改应用于菜单栏，则为 TRUE;如果框架将用户更改应用于菜单栏。否则 FALSE。

### <a name="remarks"></a>备注

此方法的默认实现将按钮的文本更改为用户提供的文本。

## <a name="cmfcmenubarontoolhittest"></a><a name="ontoolhittest"></a>CMFCMenuBar：：在工具命中测试

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>参数

[在]*点*<br/>

[在]*pTI*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuBar：:P重新翻译消息

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>参数

[在]*pMsg*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcmenubarrestoreoriginalstate"></a><a name="restoreoriginalstate"></a>CMFCMenuBar：恢复原始状态

当用户从 **"自定义"** 对话框中选择 **"重置"** 时，由框架调用。

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>返回值

如果方法成功，则非零;否则 0。

### <a name="remarks"></a>备注

当用户从自定义菜单中选择 **"重置"** 时，将调用此方法。 您还可以手动调用此方法以以编程方式重置菜单栏的状态。 此方法从资源文件加载原始状态。

如果要在用户选择 **"重置"** 选项时执行任何处理，请重写此方法。

## <a name="cmfcmenubarsavestate"></a><a name="savestate"></a>CMFC菜单栏：保存状态

将[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象的状态保存到 Windows 注册表。

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
[在]包含 Windows 注册表项路径的字符串。

*nIndex*<br/>
[在]菜单栏的控制 ID。

*uiID*<br/>
[在]保留值。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE;否则 FALSE;

### <a name="remarks"></a>备注

通常，您的应用程序不调用`SaveState`。 当工作区序列化时，框架调用此方法。 有关详细信息，请参阅[CWinAppEx：：保存状态](../../mfc/reference/cwinappex-class.md#savestate)。

保存的信息包括菜单项、停靠状态和菜单栏的位置。

## <a name="cmfcmenubarsetdefaultmenuresid"></a><a name="setdefaultmenuresid"></a>CMFC菜单栏：：设置默认菜单Resid

根据资源 ID 设置[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象的默认菜单。

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>参数

*uiResId*<br/>
[在]新默认菜单的资源 ID。

### <a name="remarks"></a>备注

[CMFCMenuBar：还原原始状态](#restoreoriginalstate)方法从资源文件还原默认菜单。

使用[CMFCMenuBar：获取默认MenuResId](#getdefaultmenuresid)方法检索默认菜单，而无需还原它。

## <a name="cmfcmenubarsetforcedownarrows"></a><a name="setforcedownarrows"></a>CMFC菜单栏：设置强制向下箭头

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>参数

[在]*bValue*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcmenubarsetmaximizemode"></a><a name="setmaximizemode"></a>CMFC菜单栏：：设置最大化模式

当 MDI 更改其显示模式且菜单栏必须更新时，框架将调用此方法。

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>参数

*bMax*<br/>
[在]指定模式的布尔。 有关详细信息，请参阅“备注”部分。

*pwnd*<br/>
[在]指向正在更改的 MDI 子窗口的指针。

*bRecalcLayout*<br/>
[在]指定是否应立即重新计算菜单栏布局的布尔。

### <a name="remarks"></a>备注

最大化 MDI 子窗口时，连接到 MDI 主框架窗口的菜单栏将显示系统菜单和 **"最小化**"、"**最大化**"和 **"关闭**"按钮。 如果*bMax*为 TRUE，并且*pWnd*不是 NULL，则 MDI 子窗口将最大化，菜单栏必须合并额外的控件。 否则，菜单栏将返回到其常规状态。

## <a name="cmfcmenubarsetmenubuttonrtc"></a><a name="setmenubuttonrtc"></a>CMFC菜单栏：设置菜单按钮RTC

设置用户创建菜单按钮时框架使用的运行时类信息。

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>参数

*pMenuButtonRTC*<br/>
[在]从[CMFCMenuButton 类](../../mfc/reference/cmfcmenubutton-class.md)派生的类的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)信息。

### <a name="remarks"></a>备注

当用户向菜单栏添加新按钮时，框架会动态创建按钮。 默认情况下，它创建`CMFCMenuButton`对象。 重写此方法以更改框架创建的按钮对象的类型。

## <a name="cmfcmenubarsetmenufont"></a><a name="setmenufont"></a>CMFCMenuBar：setMenuFont

设置应用程序中所有菜单栏的字体。

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>参数

*lpLogFont*<br/>
[在]指向[LOGFONT](/windows/win32/api/dimm/ns-dimm-logfonta)结构的指针，用于定义要设置的字体。

*布霍兹*<br/>
[在]如果希望*lpLogFont*参数用于垂直字体，则为 FALSE，如果希望将其用于水平字体，则 FALSE。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

两种字体用于所有`CMFCMenuBar`对象。 这些单独的字体用于水平和垂直菜单栏。

字体设置是全局变量，影响所有`CMFCMenuBar`对象。

## <a name="cmfcmenubarsetrecentlyusedmenus"></a><a name="setrecentlyusedmenus"></a>CMFC菜单栏：设置最近使用的菜单

控制菜单栏是否显示最近使用的菜单命令。

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>参数

*邦*<br/>
[在]控制是否显示最近使用的菜单命令的布尔。

## <a name="cmfcmenubarsetshowallcommands"></a><a name="setshowallcommands"></a>CMFC菜单栏：：设置显示所有命令

控制菜单是否显示所有可用命令。

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>参数

*b 显示所有命令*<br/>
[在]布尔参数，用于指定弹出菜单是否显示所有菜单命令。

### <a name="remarks"></a>备注

如果菜单不显示所有菜单命令，它将隐藏很少使用的命令。 有关显示菜单命令的详细信息，请参阅[CMFCMenuBar 类](../../mfc/reference/cmfcmenubar-class.md)。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
