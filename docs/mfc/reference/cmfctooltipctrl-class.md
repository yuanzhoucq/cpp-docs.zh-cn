---
title: CMFCToolTipCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
ms.openlocfilehash: 6c8bb41b82d1dca9235e1184c2152a61c07c8071
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377343"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl 类

基于 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)的扩展工具提示实现。 基于 `CMFCToolTipCtrl` 类的工具提示可显示图标、标签和说明。 可以使用渐变填充、自定义文本和边框颜色、粗体文本、圆角或气球样式来自定义可视外观。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```cpp
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCToolTipCtrl：：获取图标大小](#geticonsize)|返回工具提示中的图标大小。|
|[CMFCToolTipCtrl：：GetParams](#getparams)|返回工具提示的显示设置。|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|绘制工具提示的边框。|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|显示工具提示中的图标。|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|绘制工具提示标签或计算标签的大小。|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|绘制工具提示中标签和说明之间的分隔符。|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|填充工具提示的背景。|
|[CMFCToolTipCtrl::SetDescription](#setdescription)|设置将由工具提示显示的说明。|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|通过使用 `CMFCToolTipInfo` 对象指定工具提示的视觉外观。|

## <a name="remarks"></a>备注

将`CMFCToolTipCtrl``CMFCToolTipInfo`和 和[CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)对象一起使用，在应用程序中实现自定义的工具提示。

例如，若要使用气球样式的工具提示，请按照下列步骤执行：

1. 使用[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)方法在应用程序中初始化工具提示管理器。

2. 创建 `CMFCToolTipInfo` 结构，以指定所需的视觉样式：

    ```cpp
    CMFCToolTipInfo params;
    params.m_bBoldLabel = FALSE;
    params.m_bDrawDescription = FALSE;
    params.m_bDrawIcon = FALSE;
    params.m_bRoundedCorners = TRUE;
    params.m_bDrawSeparator = FALSE;
    if (m_bCustomColors)
    {
        params.m_clrFill = RGB (255, 255, 255);
        params.m_clrFillGradient = RGB (228, 228, 240);
        params.m_clrText = RGB (61, 83, 80);
        params.m_clrBorder = RGB (144, 149, 168);

    }
    ```

3. 使用[CTooltipManager：setTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams)方法使用对象中定义的样式设置应用程序中所有工具提示的视觉`CMFCToolTipInfo`样式：

    ```cpp
    theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
        RUNTIME_CLASS (CMFCToolTipCtrl), &params);
    ```

你也可以从 `CMFCToolTipCtrl` 派生新类以控制工具提示行为和呈现。 若要指定新的工具提示控制类，请使用 `CTooltipManager::SetTooltipParams` 方法：

```cpp
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```

若要恢复默认的工具提示控件类并将工具提示外观重置回其默认状态，请指定运行时类中的 NULL 和 `SetTooltipParams` 的工具提示信息参数：

```cpp
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>示例

下面的示例演示了如何构造 `CMFCToolTipCtrl` 对象、如何设置工具提示显示的说明以及如何设置工具提示控件的宽度。

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>要求

**标题：** afxtooltipctrl.h

## <a name="cmfctooltipctrlcmfctooltipctrl"></a><a name="cmfctooltipctrl"></a>CMFCToolTipCtrl：：CMFCToolTipCtrl

```cpp
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>参数

[在]*pParams*<br/>

### <a name="remarks"></a>备注

## <a name="cmfctooltipctrlgeticonsize"></a><a name="geticonsize"></a>CMFCToolTipCtrl：：获取图标大小

返回工具提示中的图标大小。

```cpp
virtual CSize GetIconSize();
```

### <a name="return-value"></a>返回值

图标的大小（以像素为单位）。

## <a name="cmfctooltipctrlgetparams"></a><a name="getparams"></a>CMFCToolTipCtrl：：GetParams

返回工具提示的显示设置。

```cpp
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>返回值

当前工具提示显示设置 ，这些设置存储在[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)对象中。

## <a name="cmfctooltipctrlondrawborder"></a><a name="ondrawborder"></a>CMFCToolTipCtrl：：在绘制边框

绘制工具提示的边框。

```cpp
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]工具提示的边界矩形。

*clrLine*<br/>
[在]边框颜色。

### <a name="remarks"></a>备注

在派生类中重写此方法以自定义工具提示边框的外观。

## <a name="cmfctooltipctrlondrawdescription"></a><a name="ondrawdescription"></a>CMFCToolTipCtrl：：在画描述

```cpp
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>参数

[在]*pDC*<br/>
[在]*rect*<br/>
[在]*bCalcOnly*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfctooltipctrlondrawicon"></a><a name="ondrawicon"></a>CMFCToolTipctrl：：画中

显示工具提示中的图标。

```cpp
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*rectImage*<br/>
[在]图标的坐标。

### <a name="return-value"></a>返回值

如果绘制了图标，则为 TRUE。 否则，FALSE。

### <a name="remarks"></a>备注

重写派生类中的此方法以显示自定义图标。 您还必须重写[CMFCToolTipCtrl：：GetIconSize](#geticonsize)使工具提示能够正确计算文本和说明的布局。

## <a name="cmfctooltipctrlondrawlabel"></a><a name="ondrawlabel"></a>CMFCToolTipCtrl：：在DrawLabel

绘制工具提示标签或计算标签的大小。

```cpp
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]标签区域的边界矩形。

*bCalcOnly*<br/>
[在]如果为 TRUE，将不会绘制标签。

### <a name="return-value"></a>返回值

标签的大小，以像素为单位。

### <a name="remarks"></a>备注

如果要自定义工具提示标签的外观，请在派生类中重写此方法。

## <a name="cmfctooltipctrlondrawseparator"></a><a name="ondrawseparator"></a>CMFCToolTipctrl：OnDraw分离器

绘制工具提示中标签和说明之间的分隔符。

```cpp
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*x1*<br/>
[在]分隔符左端的水平坐标。

*x2*<br/>
[在]分隔符右端的水平坐标。

*Y*<br/>
[在]分隔符的垂直坐标。

### <a name="remarks"></a>备注

默认实现从点 （x1， y） 绘制一条线到点 （x2， y）。

重写派生类中的此方法以自定义分隔符的外观。

## <a name="cmfctooltipctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCToolTipctrl：：在填充背景

填充工具提示的背景。

```cpp
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]指定要填充的区域的边界矩形。

*clrText*<br/>
[在]工具提示前景颜色。

*clrLine*<br/>
[在]边框的颜色和标签和描述之间的分隔线。

### <a name="remarks"></a>备注

默认实现填充由*rect*指定的矩形，该矩形的颜色或图案由最近对[CMFCToolTipCtrl 的调用指定：：：SetParams](#setparams)。

如果要自定义工具提示的外观，请在派生类中重写此方法。

## <a name="cmfctooltipctrlsetdescription"></a><a name="setdescription"></a>CMFCToolTipCtrl：：设置描述

设置将由工具提示显示的说明。

```cpp
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>参数

*分吸*<br/>
[在]描述文本。

### <a name="remarks"></a>备注

描述文本显示在分隔符下的工具提示上。

## <a name="cmfctooltipctrlsetfixedwidth"></a><a name="setfixedwidth"></a>CMFCToolTipCtrl：：设置固定宽度

```cpp
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>参数

[在]*nWidth 常规*<br/>
[在]*nWidth 大型图像*<br/>

### <a name="remarks"></a>备注

## <a name="cmfctooltipctrlsethotribbonbutton"></a><a name="sethotribbonbutton"></a>CMFCToolTipCtrl：：设置Hot功能框按钮

```cpp
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>参数

[在]*p 功能按钮*<br/>

### <a name="remarks"></a>备注

## <a name="cmfctooltipctrlsetlocation"></a><a name="setlocation"></a>CMFCToolTipCtrl：：设置位置

```cpp
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>参数

[在]*pt*<br/>

### <a name="remarks"></a>备注

## <a name="cmfctooltipctrlsetparams"></a><a name="setparams"></a>CMFCToolTipCtrl：：SetParams

使用[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)对象指定工具提示的视觉外观。

```cpp
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>参数

*pParams*<br/>
[在]指向包含显示参数的[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)对象的指针。

### <a name="remarks"></a>备注

每当显示工具提示时，都会使用*pParam*指定的颜色和视觉样式绘制工具提示。 *pParams*的值存储在受保护的`m_Params`成员中，该类可以覆盖具有以下位置的派生类，该类重写[CMFCToolTipCtrl：：OnDrawBorder、CMFCToolTipctrl：OnDrawIcon、CMFCToolTipctrl：onDrawTtrl、CMFCToolTipctrl：onDrawSeor](#ondrawborder)或[CMFCToolTipctrl：onFillInon](#onfillbackground) [CMFCToolTipCtrl::OnDrawIcon](#ondrawicon) [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel) [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCTool提示信息类](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
