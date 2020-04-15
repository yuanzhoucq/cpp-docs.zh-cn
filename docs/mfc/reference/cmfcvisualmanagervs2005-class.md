---
title: CMFCVisualManagerVS2005 类
ms.date: 11/04/2016
f1_keywords:
- CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetDockingTabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetMDITabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetPropertyGridGroupColor
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetTabFrameColors
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawCaptionButton
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawPaneCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawSeparator
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawTab
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawToolBoxFrame
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnEraseTabsArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillHighlightedArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillMiniFrameCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnUpdateSystemColors
helpviewer_keywords:
- CMFCVisualManagerVS2005 [MFC], GetDockingTabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetMDITabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetPropertyGridGroupColor
- CMFCVisualManagerVS2005 [MFC], GetTabFrameColors
- CMFCVisualManagerVS2005 [MFC], HasOverlappedAutoHideButtons
- CMFCVisualManagerVS2005 [MFC], OnDrawAutoHideButtonBorder
- CMFCVisualManagerVS2005 [MFC], OnDrawCaptionButton
- CMFCVisualManagerVS2005 [MFC], OnDrawPaneCaption
- CMFCVisualManagerVS2005 [MFC], OnDrawSeparator
- CMFCVisualManagerVS2005 [MFC], OnDrawTab
- CMFCVisualManagerVS2005 [MFC], OnDrawToolBoxFrame
- CMFCVisualManagerVS2005 [MFC], OnEraseTabsArea
- CMFCVisualManagerVS2005 [MFC], OnFillAutoHideButtonBackground
- CMFCVisualManagerVS2005 [MFC], OnFillHighlightedArea
- CMFCVisualManagerVS2005 [MFC], OnFillMiniFrameCaption
- CMFCVisualManagerVS2005 [MFC], OnUpdateSystemColors
ms.assetid: ea39b9ae-327e-4a51-bce7-dc84c78f005b
ms.openlocfilehash: b92077ecf4670dd5395296327c767ee3c7b848ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319908"
---
# <a name="cmfcvisualmanagervs2005-class"></a>CMFCVisualManagerVS2005 类

`CMFCVisualManagerVS2005`为应用程序提供 Microsoft Visual Studio 2005 外观。

## <a name="syntax"></a>语法

```
class CMFCVisualManagerVS2005 : public CMFCVisualManagerOffice2003
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCVisualManagerVS2005：：获取对接塔布边界大小](#getdockingtabsborderssize)|框架在绘制停靠和选项卡式窗格时调用此方法。 （覆盖[CMFC 视觉管理器：获取停靠选项卡边界大小](../../mfc/reference/cmfcvisualmanager-class.md#getdockingtabsborderssize)。|
|[CMFCVisualManagerVS2005：：获取MDITabsBordersSize](#getmditabsborderssize)|框架调用此方法以确定 MDITabs 窗口在绘制窗口之前的边界大小。 （覆盖[CMFC 视觉管理器：获取MDITabs边界大小](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize)。|
|[CMFCVisualManagerVS2005：：获取财产网格群彩](#getpropertygridgroupcolor)|（覆盖[CMFC 可视化管理器Office2003：获取属性网格群颜色](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#getpropertygridgroupcolor).）|
|[CMFC视觉管理器VS2005：：获取TabFrame颜色](#gettabframecolors)|（覆盖[CMFC 可视化管理器Office2003：获取 TabFrame 颜色](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#gettabframecolors).）|
|[CMFCVisualManagerVS2005：： 已重叠自动隐藏按钮](#hasoverlappedautohidebuttons)|返回自动隐藏按钮是否在当前可视管理器中重叠。 （覆盖[CMFC 视觉管理器：已重叠自动隐藏按钮](../../mfc/reference/cmfcvisualmanager-class.md#hasoverlappedautohidebuttons)。|
|[CMFCVisualManagervs2005：：在Draw自动隐藏按钮边框](#ondrawautohidebuttonborder)|（覆盖[CMFCVisualManagerOffice2003：onDraw 自动隐藏按钮边框](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawautohidebuttonborder).）|
|[CMFCVisualManagerVS2005：：ONDrawCaption按钮](#ondrawcaptionbutton)|（重写 `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`。）|
|[CMFCVisualManagervs2005：：在DrawPaneCaption](#ondrawpanecaption)|（覆盖[CMFCVisualManagerOffice2003：onDrawPaneCaption](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawpanecaption).）|
|[CMFCVisualManagerVS2005：OnDrawSeator](#ondrawseparator)|（覆盖[CMFCVisualManagerOffice2003：onDrawSeor](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawseparator).）|
|[CMFCVisualManagerVS2005：：在DrawTab](#ondrawtab)|（覆盖[CMFCVisualManagerOffice2003：onDrawTab](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawtab).）|
|[CMFCVisualManagerVS2005：：在画工具框框](#ondrawtoolboxframe)|（覆盖[CMFC 视觉管理器：onDrawToolBox框架](../../mfc/reference/cmfcvisualmanager-class.md#ondrawtoolboxframe)。|
|[CMFCVisualManagerVS2005：：在EraseTabs区域](#onerasetabsarea)|（覆盖[CMFCVisualManagerOffice2003：在 EraseTabs 区域](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onerasetabsarea).）|
|[CMFCVisualManagerVS2005：：在填充自动隐藏按钮背景](#onfillautohidebuttonbackground)|（覆盖[CMFCVisualManagerOffice2003：：onfill 自动隐藏按钮背景](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillautohidebuttonbackground).）|
|[CMFCVisualManagerVS2005：：在填充突出显示区域](#onfillhighlightedarea)|（覆盖[CMFCVisualManagerOffice2003：onFill 突出显示区域](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillhighlightedarea).）|
|[CMFCVisualManagerVS2005：：在填充迷你框架标题](#onfillminiframecaption)|（重写 `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`。）|
|[CMFCVisualManagerVS2005：：更新系统颜色](#onupdatesystemcolors)|（覆盖[CMFCVisualManagerOffice2003：上更新系统颜色](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onupdatesystemcolors).）|

## <a name="remarks"></a>备注

您可以使用 CMFCVisualManagerVS2005 类来更改应用程序的可视外观，以类似于 Microsoft Visual Studio 2005。

此类的所有成员都是从此类的祖先[CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)派生的虚拟函数。

## <a name="example"></a>示例

下面的示例演示如何使用可视化管理器 VS 2005。 此代码段是[桌面警报演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DesktopAlertDemo#9](../../mfc/reference/codesnippet/cpp/cmfcvisualmanagervs2005-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBase可视化管理器](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFC可视化经理办公室XP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)

[CMFCVisualManagerVS2005](../../mfc/reference/cmfcvisualmanagervs2005-class.md)

## <a name="requirements"></a>要求

**标题：** afxvisualmanagervs2005.h

## <a name="cmfcvisualmanagervs2005getdockingtabsborderssize"></a><a name="getdockingtabsborderssize"></a>CMFCVisualManagerVS2005：：获取对接塔布边界大小

```
virtual int GetDockingTabsBordersSize();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005getmditabsborderssize"></a><a name="getmditabsborderssize"></a>CMFCVisualManagerVS2005：：获取MDITabsBordersSize

```
virtual int GetMDITabsBordersSize();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005getpropertygridgroupcolor"></a><a name="getpropertygridgroupcolor"></a>CMFCVisualManagerVS2005：：获取财产网格群彩

```
virtual COLORREF GetPropertyGridGroupColor(CMFCPropertyGridCtrl* pPropList);
```

### <a name="parameters"></a>参数

[在]*pProplist*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005gettabframecolors"></a><a name="gettabframecolors"></a>CMFC视觉管理器VS2005：：获取TabFrame颜色

```
virtual void GetTabFrameColors(
    const CMFCBaseTabCtrl* pTabWnd,
    COLORREF& clrDark,
    COLORREF& clrBlack,
    COLORREF& clrHighlight,
    COLORREF& clrFace,
    COLORREF& clrDarkShadow,
    COLORREF& clrLight,
    CBrush*& pbrFace,
    CBrush*& pbrBlack);
```

### <a name="parameters"></a>参数

[在]*pTabwnd*<br/>
[在]*clrDark*<br/>
[在]*clrBlack*<br/>
[在]*clr高光*<br/>
[在]*clrFace*<br/>
[在]*clrDark阴影*<br/>
[在]*clrLight*<br/>
[在]*pbrFace*<br/>
[在]*普布布莱克*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005hasoverlappedautohidebuttons"></a><a name="hasoverlappedautohidebuttons"></a>CMFCVisualManagerVS2005：： 已重叠自动隐藏按钮

```
virtual BOOL HasOverlappedAutoHideButtons() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005ondrawautohidebuttonborder"></a><a name="ondrawautohidebuttonborder"></a>CMFCVisualManagervs2005：：在Draw自动隐藏按钮边框

```
virtual void OnDrawAutoHideButtonBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*rectBunds*<br/>
[在]*整边界大小*<br/>
[在]*pButton*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005ondrawcaptionbutton"></a><a name="ondrawcaptionbutton"></a>CMFCVisualManagerVS2005：：ONDrawCaption按钮

```
virtual void OnDrawCaptionButton(
    CDC* pDC,
    CMFCCaptionButton* pButton,
    BOOL bActive,
    BOOL bHorz,
    BOOL bMaximized,
    BOOL bDisabled,
    int nImageID = -1);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*pButton*<br/>
[在]*b 活动*<br/>
[在]*布霍兹*<br/>
[在]*b 最大化*<br/>
[在]*b 残疾*<br/>
[在]*nImageID*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005ondrawpanecaption"></a><a name="ondrawpanecaption"></a>CMFCVisualManagervs2005：：在DrawPaneCaption

```
virtual COLORREF OnDrawPaneCaption(
    CDC* pDC,
    CDockablePane* pBar,
    BOOL bActive,
    CRect rectCaption,
    CRect rectButtons);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*pBar*<br/>
[在]*b 活动*<br/>
[在]*rectCaption*<br/>
[在]*rectButtons*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005ondrawseparator"></a><a name="ondrawseparator"></a>CMFCVisualManagerVS2005：OnDrawSeator

```
virtual void OnDrawSeparator(
    CDC* pDC,
    CBasePane* pBar,
    CRect rect,
    BOOL bIsHoriz);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*pBar*<br/>
[在]*rect*<br/>
[在]*比绍里兹*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005ondrawtab"></a><a name="ondrawtab"></a>CMFCVisualManagerVS2005：：在DrawTab

```
virtual void OnDrawTab(
    CDC* pDC,
    CRect rectTab,
    int iTab,
    BOOL bIsActive,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*rectTab*<br/>
[在]*iTab*<br/>
[在]*bIsActive*<br/>
[在]*pTabwnd*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005ondrawtoolboxframe"></a><a name="ondrawtoolboxframe"></a>CMFCVisualManagerVS2005：：在画工具框框

```
virtual void OnDrawToolBoxFrame(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*rect*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005onerasetabsarea"></a><a name="onerasetabsarea"></a>CMFCVisualManagerVS2005：：在EraseTabs区域

```
virtual void OnEraseTabsArea(
    CDC* pDC,
    CRect rect,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*rect*<br/>
[在]*pTabwnd*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005onfillautohidebuttonbackground"></a><a name="onfillautohidebuttonbackground"></a>CMFCVisualManagerVS2005：：在填充自动隐藏按钮背景

```
virtual void OnFillAutoHideButtonBackground(
    CDC* pDC,
    CRect rect,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*rect*<br/>
[在]*pButton*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005onfillhighlightedarea"></a><a name="onfillhighlightedarea"></a>CMFCVisualManagerVS2005：：在填充突出显示区域

```
virtual void OnFillHighlightedArea(
    CDC* pDC,
    CRect rect,
    CBrush* pBrush,
    CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*rect*<br/>
[在]*pBrush*<br/>
[在]*pButton*<br/>

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005onfillminiframecaption"></a><a name="onfillminiframecaption"></a>CMFCVisualManagerVS2005：：在填充迷你框架标题

```
virtual COLORREF OnFillMiniFrameCaption(
    CDC* pDC,
    CRect rectCaption,
    CPaneFrameWnd* pFrameWnd,
    BOOL bActive);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*rectCaption*<br/>
[在]*pFramewnd*<br/>
[在]*b 活动*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcvisualmanagervs2005onupdatesystemcolors"></a><a name="onupdatesystemcolors"></a>CMFCVisualManagerVS2005：：更新系统颜色

```
virtual void OnUpdateSystemColors();
```

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerOfficeXP 类](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)<br/>
[CMFCVisualManagerWindows 类](../../mfc/reference/cmfcvisualmanagerwindows-class.md)<br/>
[CMFCVisualManagerOffice2003 类](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)
