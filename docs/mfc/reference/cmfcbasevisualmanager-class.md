---
title: CMFCBaseVisualManager 类
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
ms.openlocfilehash: a3288949bd4867115c32d2cbffd09cf4f7c6b40b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367809"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager 类

派生视觉管理器和 Windows 主题 API 之间的图层。

`CMFCBaseVisualManager`加载 UxTheme.dll（如果可用）并管理对 Windows 主题 API 方法的访问。

此类仅供内部使用。

## <a name="syntax"></a>语法

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|[CMFCBase可视化管理器：CMFCBase可视化管理器](#cmfcbasevisualmanager)|构造并初始化一个 `CMFCBaseVisualManager` 对象。|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFCBase可视化管理器：:D原始检查盒](#drawcheckbox)|使用当前 Windows 主题绘制复选框控件。|
|[CMFCBase可视化管理器：:D原始孔博边界](#drawcomboborder)|使用当前 Windows 主题绘制组合框边框。|
|[CMFCBase可视化管理器：:D原始孔滴按钮](#drawcombodropbutton)|使用当前 Windows 主题绘制组合框下拉按钮。|
|[CMFCBase可视化管理器：:D原始按钮](#drawpushbutton)|使用当前 Windows 主题绘制按钮。|
|[CMFCBase可视化管理器：:D原始无线按钮](#drawradiobutton)|使用当前 Windows 主题绘制单选按钮控件。|
|[CMFCBase 可视化管理器：:D原始状态栏进度](#drawstatusbarprogress)|使用当前 Windows 主题在状态栏控件[（CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)） 上绘制进度条。|
|[CMFCBase可视化管理器：：填充钢筋](#fillrebarpane)|使用当前 Windows 主题填充钢筋控件的背景。|
|[CMFCBase可视化管理器：获取标准视窗主题](#getstandardwindowstheme)|获取当前 Windows 主题。|

### <a name="protected-methods"></a>受保护的方法

|||
|-|-|
|名称|说明|
|[CMFCBase可视化管理器：：清理主题](#cleanupthemes)|调用`CloseThemeData`在 中`UpdateSystemColors`获取的所有句柄。|
|[CMFCBase可视化管理器：更新系统颜色](#updatesystemcolors)|调用`OpenThemeData`以获取用于绘制各种控件的句柄：窗口、工具栏、按钮等。|

## <a name="remarks"></a>备注

您不必直接实例化此类的对象。

因为它是所有可视化管理器的基类，因此只需调用[CMFCVisualManager：：getInstance，](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)获取指向当前可视化管理器的指针，并访问使用该`CMFCBaseVisualManager`指针的方法。 但是，如果必须使用当前 Windows 主题显示控件，最好使用该`CMFCVisualManagerWindows`接口。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBase可视化管理器](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>要求

**标题：** afxvisualmanager.h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a>CMFCBase可视化管理器：：清理主题

调用`CloseThemeData`在 中`UpdateSystemColors`获取的所有句柄。

```
void CleanUpThemes();
```

### <a name="remarks"></a>备注

仅供内部使用。

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a>CMFCBase可视化管理器：CMFCBase可视化管理器

构造并初始化一个 `CMFCBaseVisualManager` 对象。

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a>CMFCBase可视化管理器：:D原始检查盒

使用当前 Windows 主题绘制复选框控件。

```
virtual BOOL DrawCheckBox(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    int nState,
    BOOL bEnabled,
    BOOL bPressed);

);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针

*矩形*<br/>
[在]复选框的边界矩形。

*b 突出显示*<br/>
[在]指定该复选框是否突出显示。

*n州*<br/>
[in] 0 表示未选中，1 表示检查正常，

2 表示混合正常。

*b 启用*<br/>
[在]指定是否启用了复选框。

*bPressed*<br/>
[在]指定是否按下该复选框。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

*nState*的值对应于以下复选框样式。

|n州|复选框样式|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a>CMFCBase可视化管理器：:D原始孔博边界

使用当前 Windows 主题绘制组合框边框。

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]组合框边框的边界矩形。

*b 残疾*<br/>
[在]指定是否禁用组合框边框。

*bIs放弃*<br/>
[在]指定是否删除组合框边框。

*bIs 突出显示*<br/>
[在]指定组合框边框是否突出显示。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE;否则 FALSE。

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a>CMFCBase可视化管理器：:D原始孔滴按钮

使用当前 Windows 主题绘制组合框下拉按钮。

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pDC*|[在]指向设备上下文的指针。|
|*矩形*|[在]组合框下拉按钮的边界矩形。|
|*b 残疾*|[在]指定是否禁用组合框下拉按钮。|
|*bIs放弃*|[在]指定组合框下拉按钮是否下拉。|
|*bIs 突出显示*|[在]指定组合框下拉按钮是否突出显示。|

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE;否则 FALSE。

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a>CMFCBase可视化管理器：:D原始按钮

使用当前 Windows 主题绘制按钮。

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]按钮的边界矩形。

*pButton*<br/>
[在]指向要绘制的[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)对象的指针。

*uiState*<br/>
[在]忽视。 状态取自*pButton*。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE;否则 FALSE。

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a>CMFCBase可视化管理器：:D原始无线按钮

使用当前 Windows 主题绘制单选按钮控件。

```
virtual BOOL DrawRadioButton(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    BOOL bChecked,
    BOOL bEnabled,
    BOOL bPressed);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]单选按钮的边界矩形。

*b 突出显示*<br/>
[在]指定单选按钮是否突出显示。

*bChecked*<br/>
[在]指定是否选中单选按钮。

*b 启用*<br/>
[在]指定是否启用单选按钮。

*bPressed*<br/>
[在]指定是否按下单选按钮。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE;否则 FALSE。

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a>CMFCBase 可视化管理器：:D原始状态栏进度

使用当前 Windows 主题在状态栏控件[（CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)） 上绘制进度条。

```
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,
    CMFCStatusBar* pStatusBar,
    CRect rectProgress,
    int nProgressTotal,
    int nProgressCurr,
    COLORREF clrBar,
    COLORREF clrProgressBarDest,
    COLORREF clrProgressText,
    BOOL bProgressText);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*pStatusbar*<br/>
[在]指向状态栏的指针。 忽略此值。

*rectProgress*<br/>
[在]*pDC*坐标中进度条的边界矩形。

*nProgressTotal*<br/>
[在]总进度值。

*nProgressCurr*<br/>
[在]当前进度值。

*clrBar*<br/>
[在]起始颜色。 `CMFCBaseVisualManager`忽略这一点。 派生类可以将其用于颜色渐变。

*clrProgressBarDest*<br/>
[在]结束颜色。 `CMFCBaseVisualManager`忽略这一点。 派生类可以将其用于颜色渐变。

*clrProgressText*<br/>
[在]进度文本颜色。 `CMFCBaseVisualManager`忽略这一点。 文本颜色由 定义`afxGlobalData.clrBtnText`。

*bProgressText*<br/>
[在]指定是否显示进度文本。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE;否则 FALSE。

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a>CMFCBase可视化管理器：：填充钢筋

使用当前 Windows 主题填充钢筋控件的背景。

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*pBar*<br/>
[在]指向应绘制其背景的窗格的指针。

*rectClient*<br/>
[在]要填充的区域的边界矩形。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE;否则 FALSE。

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a>CMFCBase可视化管理器：获取标准视窗主题

获取当前 Windows 主题。

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>返回值

当前选定的 Windows 主题颜色。 可以是以下枚举值之一：

- `WinXpTheme_None`- 未启用主题。

- `WinXpTheme_NonStandard`- 选择非标准主题（表示选择主题，但从下面的列表中没有主题）。

- `WinXpTheme_Blue`- 蓝色主题（露娜）。

- `WinXpTheme_Olive`-橄榄主题

- `WinXpTheme_Silver`-银色主题

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a>CMFCBase可视化管理器：更新系统颜色

调用`OpenThemeData`以获取用于绘制各种控件的句柄：窗口、工具栏、按钮等。

```
void UpdateSystemColors();
```

### <a name="remarks"></a>备注

仅供内部使用。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
