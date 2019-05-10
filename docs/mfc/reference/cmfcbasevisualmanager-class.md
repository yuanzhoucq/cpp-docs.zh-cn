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
ms.openlocfilehash: 0c26c0c9c9026f8312218b2ac15f83a50a67be79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403849"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager 类

派生的视觉管理器和 Windows 主题 API 之间的层。

`CMFCBaseVisualManager` 如果可用，请加载 UxTheme.dll，并管理对 Windows 主题 API 方法的访问。

此类是仅供内部使用。

## <a name="syntax"></a>语法

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|构造并初始化一个 `CMFCBaseVisualManager` 对象。|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|通过使用当前 Windows 主题绘制复选框控件。|
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|绘制使用当前 Windows 主题的组合框边框。|
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|绘制使用当前 Windows 主题的组合框下拉按钮。|
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|绘制使用当前 Windows 主题的推送按钮。|
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|通过使用当前 Windows 主题绘制单选按钮控件。|
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|状态栏控件上绘制进度栏 ( [CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)) 使用当前 Windows 主题。|
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|通过使用当前 Windows 主题填充 rebar 控件的背景。|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|获取当前 Windows 主题。|

### <a name="protected-methods"></a>受保护的方法

|||
|-|-|
|名称|描述|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|调用`CloseThemeData`中获取所有句柄的`UpdateSystemColors`。|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|调用`OpenThemeData`若要获取用于绘制各种控件的句柄： windows、 工具栏、 按钮和等等。|

## <a name="remarks"></a>备注

无需直接实例化此类的对象。

因为它是所有的视觉管理器的基类，可以只需调用[CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)、 获取的指针到当前视觉对象管理器，并访问有关方法`CMFCBaseVisualManager`使用该指针。 但是，如果您必须使用当前 Windows 主题显示一个控件，则最好使用`CMFCVisualManagerWindows`接口。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>要求

**标头：** afxvisualmanager.h

##  <a name="cleanupthemes"></a>  CMFCBaseVisualManager::CleanUpThemes

调用`CloseThemeData`中获取所有句柄的`UpdateSystemColors`。

```
void CleanUpThemes();
```

### <a name="remarks"></a>备注

仅限内部使用。

##  <a name="cmfcbasevisualmanager"></a>  CMFCBaseVisualManager::CMFCBaseVisualManager

构造并初始化一个 `CMFCBaseVisualManager` 对象。

```
CMFCBaseVisualManager();
```

##  <a name="drawcheckbox"></a>  CMFCBaseVisualManager::DrawCheckBox

通过使用当前 Windows 主题绘制复选框控件。

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
[in]一个指向设备上下文

*rect*<br/>
[in]复选框的边框。

*bHighlighted*<br/>
[in]指定是否突出显示复选框。

*nState*<br/>
[in] 0 用于选中正常、 未选中，1

如混合常规 2。

*bEnabled*<br/>
[in]指定是否启用复选框。

*bPressed*<br/>
[in]指定是否按下复选框。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

值*nState*对应于以下的复选框样式。

|nState|复选框样式|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

##  <a name="drawcomboborder"></a>  CMFCBaseVisualManager::DrawComboBorder

绘制使用当前 Windows 主题的组合框边框。

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
[in]指向设备上下文的指针。

*rect*<br/>
[in]组合框边框的边框。

*bDisabled*<br/>
[in]指定是否禁用组合框边框。

*bIsDropped*<br/>
[in]指定是否向下删除组合框边框。

*bIsHighlighted*<br/>
[in]指定是否突出显示组合框边框。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE否则为 FALSE。

##  <a name="drawcombodropbutton"></a>  CMFCBaseVisualManager::DrawComboDropButton

绘制使用当前 Windows 主题的组合框下拉按钮。

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pDC*|[in]指向设备上下文的指针。|
|*rect*|[in]组合框下拉按钮的边框。|
|*bDisabled*|[in]指定是否禁用组合框下拉按钮。|
|*bIsDropped*|[in]指定是否向下删除组合框下拉按钮。|
|*bIsHighlighted*|[in]指定组合框下拉按钮是否突出显示。|

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE否则为 FALSE。

##  <a name="drawpushbutton"></a>  CMFCBaseVisualManager::DrawPushButton

绘制使用当前 Windows 主题的推送按钮。

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

*rect*<br/>
[in]推送按钮的边框。

*pButton*<br/>
[in]一个指向[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)对象来绘制。

*uiState*<br/>
[in]忽略。 状态取自*pButton*。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE否则为 FALSE。

##  <a name="drawradiobutton"></a>  CMFCBaseVisualManager::DrawRadioButton

通过使用当前 Windows 主题绘制单选按钮控件。

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
[in]指向设备上下文的指针。

*rect*<br/>
[in]单选按钮的边框。

*bHighlighted*<br/>
[in]指定是否突出显示的单选按钮。

*bChecked*<br/>
[in]指定是否已选中的单选按钮。

*bEnabled*<br/>
[in]指定是否启用单选按钮。

*bPressed*<br/>
[in]指定是否按下的单选按钮。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE否则为 FALSE。

##  <a name="drawstatusbarprogress"></a>  CMFCBaseVisualManager::DrawStatusBarProgress

状态栏控件上绘制进度栏 ( [CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)) 使用当前 Windows 主题。

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
[in]指向设备上下文的指针。

*pStatusBar*<br/>
[in]指向状态栏的指针。 忽略此值。

*rectProgress*<br/>
[in]中的进度栏的边界矩形*pDC*坐标。

*nProgressTotal*<br/>
[in]总进度值。

*nProgressCurr*<br/>
[in]当前的进度值。

*clrBar*<br/>
[in]开始颜色。 `CMFCBaseVisualManager` 将忽略这种情况。 派生的类可以使用它的颜色渐变。

*clrProgressBarDest*<br/>
[in]结束颜色。 `CMFCBaseVisualManager` 将忽略这种情况。 派生的类可以使用它的颜色渐变。

*clrProgressText*<br/>
[in]进度文本颜色。 `CMFCBaseVisualManager` 将忽略这种情况。 由定义的文本颜色`afxGlobalData.clrBtnText`。

*bProgressText*<br/>
[in]指定是否显示进度的文本。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE否则为 FALSE。

##  <a name="fillrebarpane"></a>  CMFCBaseVisualManager::FillReBarPane

通过使用当前 Windows 主题填充 rebar 控件的背景。

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

*pBar*<br/>
[in]指向一个窗格，应绘制其背景的指针。

*rectClient*<br/>
[in]要填充的区域的边框。

### <a name="return-value"></a>返回值

如果启用了主题 API，则为 TRUE否则为 FALSE。

##  <a name="getstandardwindowstheme"></a>  CMFCBaseVisualManager::GetStandardWindowsTheme

获取当前 Windows 主题。

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>返回值

当前所选的 Windows 主题颜色。 可以是下列枚举值之一：

- `WinXpTheme_None` -没有启用无主题。

- `WinXpTheme_NonStandard` -非标准主题处于选中状态 （即主题处于选中状态，但不从下面的列表）。

- `WinXpTheme_Blue` -蓝色主题 (Luna)。

- `WinXpTheme_Olive` -橄榄色主题。

- `WinXpTheme_Silver` -银色主题。

##  <a name="updatesystemcolors"></a>  CMFCBaseVisualManager::UpdateSystemColors

调用`OpenThemeData`若要获取用于绘制各种控件的句柄： windows、 工具栏、 按钮和等等。

```
void UpdateSystemColors();
```

### <a name="remarks"></a>备注

仅限内部使用。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
