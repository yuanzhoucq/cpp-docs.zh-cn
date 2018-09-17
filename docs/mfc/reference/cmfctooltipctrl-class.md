---
title: CMFCToolTipCtrl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f395ae726725507bf27f5033b20a4ece2a226a6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715658"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl 类
基于 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)的扩展工具提示实现。 基于 `CMFCToolTipCtrl` 类的工具提示可显示图标、标签和说明。 可以使用渐变填充、自定义文本和边框颜色、粗体文本、圆角或气球样式来自定义可视外观。  

 有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。  
  
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
 使用`CMFCToolTipCtrl`， `CMFCToolTipInfo`，并[CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)对象，以在应用程序中实现自定义工具提示。  
  
 例如，若要使用气球样式的工具提示，请按照下列步骤执行：  
  
 1. 使用[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)方法以初始化应用程序中的工具提示管理器。  
  
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
    params.m_clrFill = RGB (255,
    255,
    255);

    params.m_clrFillGradient = RGB (228,
    228,
    240);

    params.m_clrText = RGB (61,
    83,
    80);

    params.m_clrBorder = RGB (144,
    149,
    168);

 }  
```  
3. 使用[ctooltipmanager:: Settooltipparams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams)方法使用的样式中定义的应用程序中设置所有工具提示的视觉样式`CMFCToolTipInfo`对象：  
  
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
 **标头：** afxtooltipctrl.h  
  
##  <a name="cmfctooltipctrl"></a>  CMFCToolTipCtrl::CMFCToolTipCtrl  

  
```  
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in]*pParams*  
  
### <a name="remarks"></a>备注  
  
##  <a name="geticonsize"></a>  CMFCToolTipCtrl::GetIconSize  
 返回工具提示中的图标大小。  
  
```  
virtual CSize GetIconSize();
```  
  
### <a name="return-value"></a>返回值  
 该图标，以像素为单位的大小。  
  
##  <a name="getparams"></a>  CMFCToolTipCtrl::GetParams  
 返回工具提示的显示设置。  
  
```  
const CMFCToolTipInfo& GetParams() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的工具提示显示设置，它们将存储在[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)对象。  
  
##  <a name="ondrawborder"></a>  CMFCToolTipCtrl::OnDrawBorder  
 绘制工具提示的边框。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>参数  
*pDC*<br/>
[in]指向设备上下文指针。  
  
*rect*<br/>
[in]在工具提示的边框。  
  
*clrLine*<br/>
[in]边框颜色。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类以自定义工具提示边框的外观。  
  
##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription  

  
```  
virtual CSize OnDrawDescription(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>参数  
*pDC*<br/>
[in][in]*rect*  
 [in]*bCalcOnly*  
  
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
[in]指向设备上下文的指针。  
  
*rectImage*<br/>
[in]图标的坐标。  
  
### <a name="return-value"></a>返回值  
 如果绘制图标，则为 TRUE。 否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类以显示自定义图标。 您还必须重写[CMFCToolTipCtrl::GetIconSize](#geticonsize)启用工具提示以正确地计算的文本和说明的布局。  
  
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
[in]指向设备上下文的指针。  
  
*rect*<br/>
[in]标签区域的边界矩形。  
  
*bCalcOnly*<br/>
[in]如果为 TRUE，将不绘制标签。  
  
### <a name="return-value"></a>返回值  
 该标签，以像素为单位的大小。  
  
### <a name="remarks"></a>备注  
 如果你想要自定义工具提示标签的外观，重写此方法在派生类中。  
  
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
[in]指向设备上下文的指针。  
  
*x1*<br/>
[in]分隔符的水平坐标。  
  
*x2*<br/>
[in]右端的分隔符的水平坐标。  
  
*Y*<br/>
[in]分隔符的垂直坐标。  
  
### <a name="remarks"></a>备注  
 默认实现从点绘制一条线 (x1，y) 到点 (x2，y)。  
  
 重写此方法在派生类来自定义分隔符的外观。  
  
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
[in]指向设备上下文的指针。  
  
*rect*<br/>
[in]指定要填充的区域的边框。  
  
*clrText*<br/>
[in]工具提示前景色。  
  
*clrLine*<br/>
[in]边框和标签和说明之间的分隔符线的颜色。  
  
### <a name="remarks"></a>备注  
 默认实现来填充指定的矩形*rect*使用的颜色或指定的最新调用模式[CMFCToolTipCtrl::SetParams](#setparams)。  
  
 如果你想要自定义工具提示的外观，重写此方法在派生类中。  
  
##  <a name="setdescription"></a>  CMFCToolTipCtrl::SetDescription  
 设置将由工具提示显示的说明。  
  
```  
virtual void SetDescription(const CString strDesrciption);
```  
  
### <a name="parameters"></a>参数  
*strDesrciption*<br/>
[in]说明文本。  
  
### <a name="remarks"></a>备注  
 在分隔符下的工具提示上显示的说明文本。  
  
##  <a name="setfixedwidth"></a>  CMFCToolTipCtrl::SetFixedWidth  

  
```  
void SetFixedWidth(
    int nWidthRegular,  
    int nWidthLargeImage);
```  
  
### <a name="parameters"></a>参数  
*nWidthRegular*<br/>
[in][in]*nWidthLargeImage*  
  
### <a name="remarks"></a>备注  
  
##  <a name="sethotribbonbutton"></a>  CMFCToolTipCtrl::SetHotRibbonButton  

  
```  
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```  
  
### <a name="parameters"></a>参数  
 [in]*pRibbonButton*  
  
### <a name="remarks"></a>备注  
  
##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation  

  
```  
void SetLocation(CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 [in]*pt*  
  
### <a name="remarks"></a>备注  
  
##  <a name="setparams"></a>  CMFCToolTipCtrl::SetParams  
 通过使用指定的工具提示的视觉外观[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)对象。  
  
```  
void SetParams(CMFCToolTipInfo* pParams);
```  
  
### <a name="parameters"></a>参数  
*pParams*<br/>
[in]指向[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)对象，其中包含显示参数。  
  
### <a name="remarks"></a>备注  
 每当显示工具提示、 使用的颜色绘制和视觉样式*pParams*指定。 值*pParams*存储在受保护的成员`m_Params`，重写的派生类来访问它[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)， [CMFCToolTipCtrl:: OnDrawIcon](#ondrawicon)， [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)， [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)，或[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)来保持指定的外观。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CToolTipCtrl 类](../../mfc/reference/ctooltipctrl-class.md)   
 [CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)   
 [CWinAppEx 类](../../mfc/reference/cwinappex-class.md)
