---
title: CMFCPopupMenuBar 类
ms.date: 11/04/2016
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
ms.openlocfilehash: acb1e2be7d40e5e0c569fffcc92c57c750be8f91
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776773"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar 类

嵌入到弹出菜单的菜单栏。

## <a name="syntax"></a>语法

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|立即重新计算窗格的布局。 (重写[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|从指定的菜单资源加载弹出菜单项。|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|关闭延迟的弹出菜单按钮。|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|生成从弹出菜单按钮的菜单。|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|查找工具栏位于指定的点的位置。|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|指示菜单按钮图像的大小。|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|返回默认菜单项的标识符。|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|获取最近一次调用的菜单命令的索引。|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|获取弹出菜单栏中的行偏移量。|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|从指定的菜单导入弹出菜单按钮。|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|指示弹出菜单栏是否在下拉列表列表模式下。|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|指示弹出菜单栏是否处于调色板模式。|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|指示这是否是一个功能区面板 (默认为 FALSE)。|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|指示是否为功能区面板以常规模式 (默认为 FALSE)。|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|加载已存档的菜单。|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|还原用于关闭弹出菜单条延迟的菜单按钮。|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|设置给定索引处的工具栏按钮的样式。 (重写[CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle)。)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|设置弹出窗口菜单栏中的行偏移量。|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|启动指定的延迟的弹出菜单按钮的计时器。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|指定应用程序具有 Windows XP 外观时是否将显示灰色侧栏。|

## <a name="remarks"></a>备注

`CMFCPopupMenuBar`作为同时创建[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)和嵌入其内部。 `CMFCPopupMenuBar`涵盖整个工作区的`CMFCPopupMenu`对象。 它支持键盘和鼠标输入。 它也能进行通信的输入`CMFCPopupMenu`和到顶级框架窗口。

## <a name="example"></a>示例

下面的示例演示如何初始化`CMFCPopupMenuBar`对象从`CMFCPopupMenu`对象。 此代码片段属于 [Draw Client 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>要求

**标头：** afxpopupmenubar.h

##  <a name="adjustsizeimmediate"></a>  CMFCPopupMenuBar::AdjustSizeImmediate

立即重新计算弹出菜单栏窗格的布局。 (重写[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>参数

*bRecalcLayout*<br/>
[in]为 TRUE，则会自动重新计算的弹出菜单栏窗格; 布局否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="buildorigitems"></a>  CMFCPopupMenuBar::BuildOrigItems

从指定的菜单资源加载弹出菜单项。

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>参数

*uiMenuResID*<br/>
[in]指定要加载该菜单资源菜单 ID。

### <a name="return-value"></a>返回值

如果成功则为 TRUE 或 FALSE，如果不是返回。

### <a name="remarks"></a>备注

##  <a name="closedelayedsubmenu"></a>  CMFCPopupMenuBar::CloseDelayedSubMenu

关闭已推迟的弹出菜单按钮。

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>备注

##  <a name="exporttomenu"></a>  CMFCPopupMenuBar::ExportToMenu

生成从弹出菜单按钮的菜单。

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>返回值

返回的句柄的新菜单中。

### <a name="remarks"></a>备注

##  <a name="finddestintationtoolbar"></a>  CMFCPopupMenuBar::FindDestintationToolBar

查找工具栏位于指定的点的位置。

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>参数

*point*<br/>
[in]在屏幕上的点。

### <a name="return-value"></a>返回值

返回的句柄工具栏位置点位于，如果有的话，或如果不为 NULL。

### <a name="remarks"></a>备注

##  <a name="getcurrentmenuimagesize"></a>  CMFCPopupMenuBar::GetCurrentMenuImageSize

指示菜单按钮图像的大小。

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>返回值

返回工具栏上的菜单按钮图像的大小。

### <a name="remarks"></a>备注

##  <a name="getdefaultmenuid"></a>  CMFCPopupMenuBar::GetDefaultMenuId

返回默认菜单项的标识符。

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>返回值

在弹出菜单栏中返回的默认菜单项的标识符。

### <a name="remarks"></a>备注

##  <a name="getlastcommandindex"></a>  CMFCPopupMenuBar::GetLastCommandIndex

获取最近一次调用的菜单命令的索引。

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>返回值

返回已调用的最后一个菜单命令的索引。

### <a name="remarks"></a>备注

##  <a name="getoffset"></a>  CMFCPopupMenuBar::GetOffset

获取弹出菜单栏中的行偏移量。

```
int GetOffset() const;
```

### <a name="return-value"></a>返回值

返回的行偏移量的弹出菜单栏。

### <a name="remarks"></a>备注

此值设置为使用[CMFCPopupMenuBar::SetOffset](#setoffset)。

##  <a name="importfrommenu"></a>  CMFCPopupMenuBar::ImportFromMenu

从指定的菜单导入弹出菜单按钮。

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
[in]要从中导入的弹出菜单按钮菜单。

*bShowAllCommands*<br/>
[in]如果所有命令的菜单上是要导入，或如果很少使用的可能处于隐藏状态，则为 FALSE。

### <a name="return-value"></a>返回值

如果菜单按钮已成功导入从菜单中或 FALSE; 不，返回 TRUE。

### <a name="remarks"></a>备注

##  <a name="isdropdownlistmode"></a>  CMFCPopupMenuBar::IsDropDownListMode

指示弹出菜单栏是否在下拉列表列表模式下。

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>返回值

如果弹出菜单栏不是在下拉列表列表模式或 false，则返回 TRUE。

### <a name="remarks"></a>备注

##  <a name="ispalettemode"></a>  CMFCPopupMenuBar::IsPaletteMode

指示弹出菜单栏是否处于调色板模式。

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>返回值

如果启用了调色板模式，则为 TRUE 或 FALSE，如果不是返回。

### <a name="remarks"></a>备注

当菜单栏设置为调色板模式下时，菜单项将出现在多个列和有限的数量的行。

##  <a name="isribbonpanel"></a>  CMFCPopupMenuBar::IsRibbonPanel

指示这是否是一个功能区面板 (默认为 FALSE)。

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>返回值

默认情况下，该值指示这不一个功能区面板返回 FALSE。

### <a name="remarks"></a>备注

##  <a name="isribbonpanelinregularmode"></a>  CMFCPopupMenuBar::IsRibbonPanelInRegularMode

指示是否为功能区面板以常规模式 (默认为 FALSE)。

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>返回值

默认情况下，该值指示，这不功能区面板在常规模式下返回 FALSE。

### <a name="remarks"></a>备注

##  <a name="loadfromhash"></a>  CMFCPopupMenuBar::LoadFromHash

加载已存档的菜单。

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
[in]存档菜单上，若要加载到一个句柄。

### <a name="return-value"></a>返回值

如果菜单为加载成功，或如果不是 FALSE，则返回 TRUE。

### <a name="remarks"></a>备注

##  <a name="m_bdisablesidebarinxpmode"></a>  CMFCPopupMenuBar::m_bDisableSideBarInXPMode

一个布尔参数，指示具有 Windows XP 外观时，你的应用程序是否具有灰色侧栏。

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>备注

如果此成员变量设置为 FALSE，并且你的应用程序具有 Windows XP 的外观，框架将在应用程序中绘制灰色侧栏。

默认值是 FALSE。

##  <a name="restoredelayedsubmenu"></a>  CMFCPopupMenuBar::RestoreDelayedSubMenu

还原用于关闭弹出菜单条延迟的菜单按钮。

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>备注

##  <a name="setbuttonstyle"></a>  CMFCPopupMenuBar::SetButtonStyle

设置给定索引处的工具栏按钮的样式。 (重写[CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle)。)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[in]设置其样式是工具栏按钮的从零开始的索引。

*nStyle*<br/>
[in]按钮的样式。 请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)可用工具栏按钮样式的列表。

### <a name="remarks"></a>备注

##  <a name="setoffset"></a>  CMFCPopupMenuBar::SetOffset

设置弹出窗口菜单栏中的行偏移量。

```
void SetOffset(int iOffset);
```

### <a name="parameters"></a>参数

*iOffset*<br/>
[in]应偏移弹出菜单栏中的行数。

### <a name="remarks"></a>备注

##  <a name="startpopupmenutimer"></a>  CMFCPopupMenuBar::StartPopupMenuTimer

启动指定的延迟的弹出菜单按钮的计时器。

```
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>参数

*pMenuButton*<br/>
[in]指向要为其设置延迟计时器的菜单按钮。

*nDelayFactor*<br/>
[in]一个延迟的系数，等于至少一个，将按标准菜单延迟时间 （通常为半秒和 5 秒）。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)
