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
ms.openlocfilehash: 5376fd21f84411c86ade564d7c76d073ccb909a6
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273695"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl 类

基于 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)的扩展工具提示实现。 基于 `CMFCToolTipCtrl` 类的工具提示可显示图标、标签和说明。 可以使用渐变填充、自定义文本和边框颜色、粗体文本、圆角或气球样式来自定义可视外观。

有关更多详细信息，请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|返回工具提示中的图标大小。|
|[CMFCToolTipCtrl::GetParams](#getparams)|返回工具提示的显示设置。|
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

在`CMFCToolTipCtrl`应用`CMFCToolTipInfo`程序中将、和[CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)对象一起使用，以实现自定义的工具提示。

例如，若要使用气球样式的工具提示，请按照下列步骤执行：

1. 使用[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)方法可在应用程序中初始化 tooltip 管理器。

2. 创建 `CMFCToolTipInfo` 结构，以指定所需的视觉样式：

```
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
3. 使用[CTooltipManager：： SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams)方法，通过使用`CMFCToolTipInfo`对象中定义的样式为应用程序中的所有工具提示设置视觉样式：

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```
你也可以从 `CMFCToolTipCtrl` 派生新类以控制工具提示行为和呈现。 若要指定新的工具提示控制类，请使用 `CTooltipManager::SetTooltipParams` 方法：

```
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```
若要恢复默认的工具提示控件类并将工具提示外观重置回其默认状态，请指定运行时类中的 NULL 和 `SetTooltipParams` 的工具提示信息参数：

```
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

**标头：** afxtooltipctrl

##  <a name="cmfctooltipctrl"></a>CMFCToolTipCtrl：： CMFCToolTipCtrl

```
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>参数

中*pParams*<br/>

### <a name="remarks"></a>备注

##  <a name="geticonsize"></a>CMFCToolTipCtrl：： GetIconSize

返回工具提示中的图标大小。

```
virtual CSize GetIconSize();
```

### <a name="return-value"></a>返回值

图标的大小（以像素为单位）。

##  <a name="getparams"></a>CMFCToolTipCtrl：： GetParams

返回工具提示的显示设置。

```
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>返回值

当前工具提示显示设置，存储在[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)对象中。

##  <a name="ondrawborder"></a>CMFCToolTipCtrl：： OnDrawBorder

绘制工具提示的边框。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*rect*<br/>
中Tooltip 的边框。

*clrLine*<br/>
中边框颜色。

### <a name="remarks"></a>备注

在派生类中重写此方法以自定义工具提示边框的外观。

##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription

```
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>参数

[in] *pDC*<br/>
中*rect*<br/>
中*bCalcOnly*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ondrawicon"></a>  CMFCToolTipCtrl::OnDrawIcon

显示工具提示中的图标。

```
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*rectImage*<br/>
中图标的坐标。

### <a name="return-value"></a>返回值

如果已绘制图标，则为 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

在派生类中重写此方法以显示自定义图标。 还必须重写[CMFCToolTipCtrl：： GetIconSize](#geticonsize)以使工具提示能够正确计算文本和说明的布局。

##  <a name="ondrawlabel"></a>  CMFCToolTipCtrl::OnDrawLabel

绘制工具提示标签或计算标签的大小。

```
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*rect*<br/>
中标签区域的边框。

*bCalcOnly*<br/>
中如果为 TRUE，则不绘制标签。

### <a name="return-value"></a>返回值

标签的大小（以像素为单位）。

### <a name="remarks"></a>备注

如果要自定义工具提示标签的外观，请在派生类中重写此方法。

##  <a name="ondrawseparator"></a>  CMFCToolTipCtrl::OnDrawSeparator

绘制工具提示中标签和说明之间的分隔符。

```
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*x1*<br/>
中分隔符左端的水平坐标。

*x2*<br/>
中分隔符右端的水平坐标。

*Y*<br/>
中分隔符的垂直坐标。

### <a name="remarks"></a>备注

默认实现从点（x1，y）绘制直线到点（x2，y）。

在派生类中重写此方法以自定义分隔符的外观。

##  <a name="onfillbackground"></a>  CMFCToolTipCtrl::OnFillBackground

填充工具提示的背景。

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*rect*<br/>
中指定要填充的区域的边框。

*clrText*<br/>
中工具提示的前景色。

*clrLine*<br/>
中边框的颜色和标签和说明之间的分隔线。

### <a name="remarks"></a>备注

默认实现使用由对[CMFCToolTipCtrl：： SetParams](#setparams)的最新调用所指定的颜色或模式填充*rect*指定的矩形。

如果要自定义工具提示的外观，请在派生类中重写此方法。

##  <a name="setdescription"></a>  CMFCToolTipCtrl::SetDescription

设置将由工具提示显示的说明。

```
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>参数

*strDesrciption*<br/>
中说明文本。

### <a name="remarks"></a>备注

说明文本将显示在工具提示下分隔符下。

##  <a name="setfixedwidth"></a>CMFCToolTipCtrl：： SetFixedWidth

```
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>参数

[in] *nWidthRegular*<br/>
[in] *nWidthLargeImage*<br/>

### <a name="remarks"></a>备注

##  <a name="sethotribbonbutton"></a>CMFCToolTipCtrl：： SetHotRibbonButton

```
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>参数

中*pRibbonButton*<br/>

### <a name="remarks"></a>备注

##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation

```
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>参数

[in] *pt*<br/>

### <a name="remarks"></a>备注

##  <a name="setparams"></a>  CMFCToolTipCtrl::SetParams

使用[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)对象指定工具提示的可视外观。

```
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>参数

*pParams*<br/>
中指向包含显示参数的[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)对象的指针。

### <a name="remarks"></a>备注

只要显示工具提示，就会使用*pParams*指定的颜色和视觉样式来绘制工具提示。 *PParams*的值存储在受保护的成员`m_Params`中，此派生类可以通过重写[CMFCToolTipCtrl：： OnDrawBorder](#ondrawborder)、 [CMFCToolTipCtrl：： OnDrawIcon](#ondrawicon)、 [CMFCToolTipCtrl：： OnDrawLabel 的派生类对其进行访问。](#ondrawlabel)、 [CMFCToolTipCtrl：： OnDrawSeparator](#ondrawseparator)或[CMFCToolTipCtrl：： OnFillBackground](#onfillbackground)来维护指定的外观。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl 类](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
