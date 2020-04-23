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
ms.openlocfilehash: c0ba90246d19e8dd07c856eec6a518a8513ee665
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751918"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar 类

嵌入到弹出菜单的菜单栏。

## <a name="syntax"></a>语法

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|立即重新计算窗格的布局。 （覆盖[CPane：调整大小立即](../../mfc/reference/cpane-class.md#adjustsizeimmediate).）|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|从指定的菜单资源加载弹出菜单项。|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|关闭延迟的弹出菜单按钮。|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|从弹出式菜单按钮生成菜单。|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|查找指定点所在的工具栏。|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|指示菜单按钮图像的大小。|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|返回默认菜单项的标识符。|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|获取最近调用的菜单命令的索引。|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|获取弹出菜单栏的行偏移量。|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|从指定的菜单导入弹出菜单按钮。|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|指示弹出菜单栏是否处于下拉列表模式。|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|指示弹出菜单栏是否处于调色板模式。|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|指示这是否是功能区面板（默认情况下为 FALSE）。|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|指示这是否是常规模式下的功能区面板（默认情况下为 FALSE）。|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|加载存档的菜单。|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|还原用于关闭弹出菜单栏的延迟菜单按钮。|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|设置给定索引处工具栏按钮的样式。 （覆盖[CMFC 工具栏：设置按钮样式](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).）|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|设置弹出菜单栏的行偏移量。|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|启动指定延迟弹出菜单按钮的计时器。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFC弹出菜单栏：：m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|指定当应用程序具有 Windows XP 外观时，是否将显示灰色边栏。|

## <a name="remarks"></a>备注

`CMFCPopupMenuBar`与[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)同时创建，并嵌入其中。 覆盖`CMFCPopupMenuBar``CMFCPopupMenu`对象的整个工作区。 它支持键盘和鼠标输入。 它还将输入与 顶层框架窗口`CMFCPopupMenu`和 顶部框架窗口通信。

## <a name="example"></a>示例

下面的示例演示如何从`CMFCPopupMenuBar``CMFCPopupMenu`对象初始化对象。 此代码片段属于 [Draw Client 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具栏](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>要求

**标题：** afxpopupmenubar.h

## <a name="cmfcpopupmenubaradjustsizeimmediate"></a><a name="adjustsizeimmediate"></a>CMFC弹出菜单栏：：立即调整大小

立即重新计算弹出式菜单栏窗格的布局。 （覆盖[CPane：调整大小立即](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>参数

*bRecalcLayout*<br/>
[在]TRUE 自动重新计算弹出菜单栏窗格的布局;否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarbuildorigitems"></a><a name="buildorigitems"></a>CMFCPopupMenu菜单栏：：构建Orig项目

从指定的菜单资源加载弹出菜单项。

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>参数

*uiMenuResID*<br/>
[在]指定要加载的菜单资源的菜单 ID。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE;如果成功则返回 FALSE;如果成功则返回 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarclosedelayedsubmenu"></a><a name="closedelayedsubmenu"></a>CMFC弹出菜单栏：：关闭延迟的子菜单

关闭已延迟的弹出菜单按钮。

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarexporttomenu"></a><a name="exporttomenu"></a>CMFCPopupMenu栏：：导出到菜单

从弹出式菜单按钮生成菜单。

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>返回值

返回新菜单的句柄。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarfinddestintationtoolbar"></a><a name="finddestintationtoolbar"></a>CMFCPopup菜单栏：：查找"选择工具栏"

查找指定点所在的工具栏。

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>参数

*点*<br/>
[在]屏幕上的一个点。

### <a name="return-value"></a>返回值

将句柄返回到点所在的工具栏（如果有），或 NULL（如果没有）。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubargetcurrentmenuimagesize"></a><a name="getcurrentmenuimagesize"></a>CMFCPopup菜单栏：获取当前菜单图像大小

指示菜单按钮图像的大小。

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>返回值

返回工具栏中的菜单按钮图像的大小。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubargetdefaultmenuid"></a><a name="getdefaultmenuid"></a>CMFCPopup菜单栏：获取默认菜单Id

返回默认菜单项的标识符。

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>返回值

在弹出式菜单栏中返回默认菜单项的标识符。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubargetlastcommandindex"></a><a name="getlastcommandindex"></a>CMFCPopupMenu菜单栏：获取最后命令索引

获取最近调用的菜单命令的索引。

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>返回值

返回已调用的最后一个菜单命令的索引。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubargetoffset"></a><a name="getoffset"></a>CMFCPopup菜单栏：获取偏移

获取弹出菜单栏的行偏移量。

```
int GetOffset() const;
```

### <a name="return-value"></a>返回值

返回弹出菜单栏的行偏移量。

### <a name="remarks"></a>备注

此值使用[CMFCPopupMenuMenu 栏设置：：设置偏移](#setoffset)量 。

## <a name="cmfcpopupmenubarimportfrommenu"></a><a name="importfrommenu"></a>CMFC弹出菜单栏：：从Menu导入

从指定的菜单导入弹出菜单按钮。

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
[在]要从中导入弹出菜单按钮的菜单。

*b 显示所有命令*<br/>
[在]如果要导入菜单上的所有命令，则为 TRUE;如果很少使用命令，则 FALSE 可能会隐藏。

### <a name="return-value"></a>返回值

如果菜单按钮已成功从菜单导入，则返回 TRUE;如果菜单按钮未从菜单中成功导入，则返回 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarisdropdownlistmode"></a><a name="isdropdownlistmode"></a>CMFC弹出菜单栏：：是向下列表模式

指示弹出菜单栏是否处于下拉列表模式。

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>返回值

如果弹出菜单栏处于下拉列表模式，则返回 TRUE;如果没有，则返回 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarispalettemode"></a><a name="ispalettemode"></a>CMFCPopup菜单栏：：是调色板模式

指示弹出菜单栏是否处于调色板模式。

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>返回值

如果启用了调色板模式，则返回 TRUE;如果未启用，则返回 FALSE。

### <a name="remarks"></a>备注

当菜单栏设置为调色板模式时，菜单项将显示在多个列和数量有限的行中。

## <a name="cmfcpopupmenubarisribbonpanel"></a><a name="isribbonpanel"></a>CMFCPopupMenu菜单栏：：是带状面板

指示这是否是功能区面板（默认情况下为 FALSE）。

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>返回值

默认情况下返回 FALSE，表示这不是功能区面板。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarisribbonpanelinregularmode"></a><a name="isribbonpanelinregularmode"></a>CMFCPopupMenubar：：在常规模式下，是带彩板

指示这是否是常规模式下的功能区面板（默认情况下为 FALSE）。

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>返回值

默认情况下返回 FALSE，表示这不是常规模式下的功能区面板。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarloadfromhash"></a><a name="loadfromhash"></a>CMFCPopupMenuBar：：从哈什加载

加载存档的菜单。

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>参数

*hMenu*<br/>
[在]要加载的存档菜单的句柄。

### <a name="return-value"></a>返回值

如果菜单已成功加载，则返回 TRUE;如果未加载，则返回 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarm_bdisablesidebarinxpmode"></a><a name="m_bdisablesidebarinxpmode"></a>CMFC弹出菜单栏：：m_bDisableSideBarInXPMode

Boolean 参数，指示应用程序在具有 Windows XP 外观时是否有灰色侧边栏。

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>备注

如果此成员变量设置为 FALSE，并且应用程序具有 Windows XP 外观，则框架将绘制应用程序中的灰色侧边栏。

默认值是 FALSE。

## <a name="cmfcpopupmenubarrestoredelayedsubmenu"></a><a name="restoredelayedsubmenu"></a>CMFC弹出菜单栏：：恢复延迟的子菜单

还原用于关闭弹出菜单栏的延迟菜单按钮。

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CMFC弹出菜单栏：：设置按钮样式

设置给定索引处工具栏按钮的样式。 （覆盖[CMFC 工具栏：设置按钮样式](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).）

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]要设置其样式的工具栏按钮的零基索引。

*nStyle*<br/>
[在]按钮的样式。 有关可用工具栏按钮样式的列表，请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarsetoffset"></a><a name="setoffset"></a>CMFC弹出菜单栏：：设置偏移

设置弹出菜单栏的行偏移量。

```cpp
void SetOffset(int iOffset);
```

### <a name="parameters"></a>参数

*i 偏移*<br/>
[在]弹出菜单栏应偏移的行数。

### <a name="remarks"></a>备注

## <a name="cmfcpopupmenubarstartpopupmenutimer"></a><a name="startpopupmenutimer"></a>CMFC弹出菜单栏：：启动弹出菜单计时器

启动指定延迟弹出菜单按钮的计时器。

```cpp
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>参数

*pMenu按钮*<br/>
[在]指向要为其设置延迟计时器的菜单按钮。

*nDelay 因子*<br/>
[在]延迟因子（至少等于一个）乘以标准菜单延迟时间（通常介于半秒到五秒之间）。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 类](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)
