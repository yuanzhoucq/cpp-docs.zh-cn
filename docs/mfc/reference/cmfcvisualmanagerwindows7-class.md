---
title: CMFCVisualManagerWindows7 类
ms.date: 03/27/2019
f1_keywords:
- CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor
- AFXVISUALMANAGERWINDOWS7/CMFCVisualManagerWindows7::OnFillMenuImageRect
helpviewer_keywords:
- CMFCVisualManagerWindows7 Class [MFC]
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
ms.openlocfilehash: 6686afecc2b8ef97ea24ef45ff5225433677a954
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319836"
---
# <a name="cmfcvisualmanagerwindows7-class"></a>CMFCVisualManagerWindows7 类

为`CMFCVisualManagerWindows7`应用程序提供 Windows 7 应用程序的外观。

## <a name="syntax"></a>语法

```
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC视觉管理器窗口7：：CMFC视觉管理器Windows7](#cmfcvisualmanagerwindows7)|默认构造函数。|
|[CMFC视觉管理器窗口7：：~CMFC视觉管理器7](#_dtorcmfcvisualmanagerwindows7)|默认析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCVisualManagerWindows7::CleanStyle`|清除当前视觉样式并重置默认视觉样式。|
|`CMFCVisualManagerWindows7::CleanUp`|清除用户界面中的所有对象并重置菜单。|
|`CMFCVisualManagerWindows7::DrawNcBtn`|在框架的非工作区中绘制一个按钮。 框架使用此方法在窗口框架的右上角绘制最小化、最大化、关闭和恢复按钮。 仅当程序使用`Aero`主题时，才调用此方法。|
|`CMFCVisualManagerWindows7::DrawNcText`|在框架的非工作区中绘制文本。 框架使用此方法在框架窗口顶部的标题栏中绘制应用程序标题。|
|`CMFCVisualManagerWindows7::DrawSeparator`|在[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)上绘制分隔符。|
|`CMFCVisualManagerWindows7::GetRibbonBar`|检索与用户界面关联的[CMFCRibbonBar 类](../../mfc/reference/cmfcribbonbar-class.md)。|
|[CMFC视觉管理器窗口7：：获取功能编辑背景颜色](#getribboneditbackgroundcolor)|获取功能区编辑框背景颜色。|
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|覆盖[CMFC 可视化管理器：：获取放大缩小字体功能 放大缩小字体功能](../../mfc/reference/cmfcvisualmanager-class.md#getribbonpopupbordersize)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|覆盖[CMFC 视觉管理器：：获取功能快速访问工具BarVveV偏移](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarchevronoffset)|
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|覆盖[CMFC 视觉管理器：：获取功能快速访问工具栏边缘](../../mfc/reference/cmfcvisualmanager-class.md#getribbonquickaccesstoolbarrightmargin)|
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|覆盖[CMFC 可视化管理器窗口：：是突出显示完整菜单项目](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ishighlightwholemenuitem)|
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|覆盖[CMFC 可视化管理器：：所有者DrawMenu检查](../../mfc/reference/cmfcvisualmanager-class.md#isownerdrawmenucheck)|
|`CMFCVisualManagerWindows7::IsRibbonPresent`|确定 是否存在`CMFCRibbonBar`和可见。|
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|覆盖[CMFC 可视化管理器窗口：：在绘制按钮边框](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|覆盖[CMFC 可视化管理器窗口：：在DrawCheckBoxEx上](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcheckboxex)|
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|覆盖[CMFC 可视化管理器窗口：：OnDrawComDropButton](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawcombodropbutton)|
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|覆盖[CMFC 可视化管理器：：在绘制默认功能图片](../../mfc/reference/cmfcvisualmanager-class.md#ondrawdefaultribbonimage)|
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|覆盖[CMFC 可视化管理器窗口：：在绘制菜单边框](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawmenuborder)|
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|覆盖[CMFC 视觉管理器：：在绘制菜单检查](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck)|
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|覆盖[CMFC 视觉管理器：：在DrawMenu标签上](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenulabel)|
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|重写 `CMFCVisualManager::OnDrawRadioButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|覆盖[CMFC 可视化管理器：：在绘制功能应用程序按钮](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonapplicationbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|覆盖[CMFC 视觉管理器：：在绘制功能按钮边框](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonborder)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|覆盖[CMFC 视觉管理器：：绘制功能标题](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|覆盖[CMFC 视觉管理器：：在绘制功能字幕按钮](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncaptionbutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|覆盖[CMFC 可视化管理器：：OnDraw 功能区类别](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategory)|
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|覆盖[CMFC 可视化管理器：：在绘制功能符类别选项卡](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)|
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|覆盖[CMFC 可视化管理器：：在绘制功能区默认窗格按钮](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbondefaultpanebutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|覆盖[CMFC 可视化管理器：：在Draw功能区画廊按钮](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbongallerybutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|重写 `CMFCVisualManager::OnDrawRibbonLaunchButton`|
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|覆盖[CMFC 可视化管理器：：绘制功能菜单检查框架](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonmenucheckframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|覆盖[CMFC 视觉管理器：：在绘制功能面板](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|覆盖[CMFC 视觉管理器：：在DrawRibbon面板标题](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonpanelcaption)|
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|覆盖[CMFC 可视化管理器：：在绘制功能进度栏](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)|
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|覆盖[CMFC 可视化管理器：：绘制功能最近文件框](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonrecentfilesframe)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|覆盖[CMFC 可视化管理器：：在绘制功能滑块通道](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|覆盖[CMFC 可视化管理器：：在绘制功能滑块](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)|
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|覆盖[CMFC 可视化管理器：：在绘制功能滑块缩放按钮](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)|
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|覆盖[CMFC 可视化管理器：：在绘制功能状态栏窗格](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonstatusbarpane)|
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|覆盖[CMFC 可视化管理器：：在绘制功能符选项卡框](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbontabsframe)|
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|覆盖[CMFC 可视化管理器窗口：：在绘制状态栏大小框](../../mfc/reference/cmfcvisualmanagerwindows-class.md#ondrawstatusbarsizebox)|
|`CMFCVisualManagerWindows7::OnFillBarBackground`|覆盖[CMFC 可视化管理器窗口：：打开填充栏背景](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbarbackground)|
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|覆盖[CMFC 可视化管理器窗口：：打开填充按钮内部](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onfillbuttoninterior)|
|[CMFCVisualManagerWindows7：：在填充菜单图像重新ct](#onfillmenuimagerect)|当框架填充菜单项图像周围的区域时，它将调用此方法。|
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|覆盖[CMFC 可视化管理器：：打开填充功能按钮](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonbutton)|
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|覆盖[CMFC 视觉管理器：：在填充功能快速访问工具栏弹出](../../mfc/reference/cmfcvisualmanager-class.md#onfillribbonquickaccesstoolbarpopup)|
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|覆盖[CMFC 可视化管理器窗口：：在突出显示菜单项上](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onhighlightmenuitem)|
|`CMFCVisualManagerWindows7::OnNcActivate`|覆盖[CMFC 可视化管理器：：打开 NcActivate](../../mfc/reference/cmfcvisualmanager-class.md#onncactivate)|
|`CMFCVisualManagerWindows7::OnNcPaint`|覆盖[CMFC 可视化管理器：：OnNcPaint](../../mfc/reference/cmfcvisualmanager-class.md#onncpaint)|
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|覆盖[CMFC 可视化管理器窗口：：更新系统颜色](../../mfc/reference/cmfcvisualmanagerwindows-class.md#onupdatesystemcolors)|
|`CMFCVisualManagerWindows7::SetResourceHandle`|设置描述可视化管理器属性的资源句柄。|
|`CMFCVisualManagerWindows7::SetStyle`|设置 GUI 的`CMFCVisualManagerWindows7`配色方案。|

## <a name="remarks"></a>备注

使用`CMFCVisualManagerWindows7`类更改应用程序的外观以模拟默认的 Windows 7 应用程序。 如果应用程序在 Windows 7 之前的版本上运行，则此类可能无效。 在这种情况下，应用程序使用[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)中定义的默认可视化管理器。

CMFCVisualManagerWindows7 从[CMFCVisualManagerWindows 类](../../mfc/reference/cmfcvisualmanagerwindows-class.md)和`CMFCVisualManager`类继承多种方法。 上一节中列出的方法是类`CMFCVisualManagerWindows7`的新方法。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBase可视化管理器](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFC可视化经理办公室XP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

`CMFCVisualManagerWindows7`

## <a name="requirements"></a>要求

**标题：** afxvisualmanagerwindows7.h

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="_dtorcmfcvisualmanagerwindows7"></a>CMFC视觉管理器窗口7：：~CMFC视觉管理器7

默认析构函数。

```
virtual ~CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7cmfcvisualmanagerwindows7"></a><a name="cmfcvisualmanagerwindows7"></a>CMFC视觉管理器窗口7：：CMFC视觉管理器Windows7

默认构造函数。

```
CMFCVisualManagerWindows7();
```

## <a name="cmfcvisualmanagerwindows7getribboneditbackgroundcolor"></a><a name="getribboneditbackgroundcolor"></a>CMFC视觉管理器窗口7：：获取功能编辑背景颜色

获取功能区编辑框的背景颜色。

```
virtual COLORREF GetRibbonEditBackgroundColor (
    CMFCRibbonRichEditCtrl* pEdit,
    BOOL bIsHighlighted,
    BOOL bIsPaneHighlighted,
    BOOL bIsDisabled);
```

### <a name="parameters"></a>参数

*pEdit*<br/>
[在]指向编辑控件的指针。 此值不能为 NULL。

*bIs 突出显示*<br/>
[出]返回功能区框是否突出显示。

*bIsPane 突出显示*<br/>
[出]如果突出显示包含*pEdit*的功能区面板，则返回 TRUE。

*bIs 已禁用*<br/>
[出]返回是否禁用*pEdit。*

### <a name="return-value"></a>返回值

编辑框*pEdit*的背景颜色。

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagerwindows7onfillmenuimagerect"></a><a name="onfillmenuimagerect"></a>CMFCVisualManagerWindows7：：在填充菜单图像重新ct

当框架填充菜单项图像周围的区域时，它将调用此方法。

```
virtual void OnFillMenuImageRect(
    CDC* pDC,
    CMFCToolBarButton* pButton,
    CRect rectangle,
    CMFCVisualManager::AFX_BUTTON_STATE state);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向菜单按钮的设备上下文的指针。

*pButton*<br/>
[在]指向 的`CMFCToolBarButton`指针。 框架填充此按钮的背景。

*矩形 (rectangle)*<br/>
[在]指定菜单按钮图像区域边界的矩形。

*状态*<br/>
[在]按钮状态。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerWindows 类](../../mfc/reference/cmfcvisualmanagerwindows-class.md)
