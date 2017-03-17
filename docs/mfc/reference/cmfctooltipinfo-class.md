---
title: "CMFCToolTipInfo 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolTipInfo class
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ed15ce9f3e1abb48c0a6c4eacdf662cc2ef3f9c9
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo 类
存储有关工具提示视觉外观的信息。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolTipInfo  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolTipInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|指示工具提示是否具有气球外观的布尔变量。|  
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|指示工具提示标签是否以粗体显示的布尔变量。|  
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|指示工具提示是否包含说明的布尔变量。|  
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|指示工具提示是否包含图标的布尔变量。|  
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|指示分隔符是否显示在工具提示标签和工具提示说明之间的布尔变量。|  
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|指示工具提示是否具有圆角的布尔变量。|  
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|该值指示是否应通过的可视管理器控制工具提示的外观的 Boolean 变量 (请参阅[CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md))。|  
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|工具提示边框的颜色。|  
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|工具提示背景的颜色。|  
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|工具提示中渐变填充的颜色。|  
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|工具提示中的文本颜色。|  
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|工具提示中渐变填充的角度。|  
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|工具提示中说明的最大可能宽度（以像素为单位）。|  
  
## <a name="remarks"></a>备注  
 使用[CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)， `CMFCToolTipInfo`，和[CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)在一起以在您的应用程序中实现自定义工具提示。 有关如何使用这些工具提示类的示例，请参阅[CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)主题。  
  
## <a name="example"></a>示例  
 下面的示例演示了如何在 `CMFCToolTipInfo` 类中设置多个成员变量的值的方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&42;](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtooltipctrl.h  
  
##  <a name="m_bballoontooltip"></a>CMFCToolTipInfo::m_bBalloonTooltip  
 指定所有工具提示的显示的样式。  
  
```  
BOOL m_bBalloonTooltip;  
```  
  
### <a name="remarks"></a>备注  
 `TRUE`指示工具提示使用气球样式，`FALSE`指示工具提示使用矩形样式。  
  
##  <a name="m_bboldlabel"></a>CMFCToolTipInfo::m_bBoldLabel  
 指定的工具提示文本的字体为粗体。  
  
```  
BOOL m_bBoldLabel;  
```  
  
### <a name="remarks"></a>备注  
 将此成员设置为`TRUE`来显示工具提示文本，并加粗字体或`FALSE`可与非加粗字体显示工具提示的标签。  
  
##  <a name="m_bdrawdescription"></a>CMFCToolTipInfo::m_bDrawDescription  
 指定是否每个工具提示将显示说明文本。  
  
```  
BOOL m_bDrawDescription;  
```  
  
### <a name="remarks"></a>备注  
 将此成员设置为`TRUE`以显示说明，或`FALSE`来隐藏说明。 您可以通过调用在上一个工具提示指定说明[CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)  
  
##  <a name="m_bdrawicon"></a>CMFCToolTipInfo::m_bDrawIcon  
 指定是否所有工具提示显示的图标。  
  
```  
BOOL m_bDrawIcon;  
```  
  
### <a name="remarks"></a>备注  
 将此成员设置为`TRUE`以在每个工具提示，显示一个图标或`FALSE`显示不带图标的工具提示。  
  
##  <a name="m_bdrawseparator"></a>CMFCToolTipInfo::m_bDrawSeparator  
 指定每个工具提示是否有它的标签和描述之间的分隔符。  
  
```  
BOOL m_bDrawSeparator;  
```  
  
### <a name="remarks"></a>备注  
 将此成员设置为`TRUE`以显示工具提示标签和说明，之间分隔符或`FALSE`来显示工具提示，并没有分隔符。  
  
##  <a name="m_broundedcorners"></a>CMFCToolTipInfo::m_bRoundedCorners  
 指定所有工具提示是否有了圆形角。  
  
```  
BOOL m_bRoundedCorners;  
```  
  
### <a name="remarks"></a>备注  
 将此成员设置为`TRUE`以显示在工具提示，圆的角或`FALSE`以显示在工具提示的矩形的角。  
  
##  <a name="m_clrborder"></a>CMFCToolTipInfo::m_clrBorder  
 在所有的工具提示中指定的边框的颜色。  
  
```  
COLORREF m_clrBorder;  
```  
  
##  <a name="m_clrfill"></a>CMFCToolTipInfo::m_clrFill  
 指定工具提示的背景的颜色。  
  
```  
COLORREF m_clrFill;  
```  
  
### <a name="remarks"></a>备注  
 如果[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)为-1，工具提示的背景色是`m_clrFill`。 否则为`m_clrFill`指定的颜色渐变的开始和`m_clrFillGradient`指定渐变结束颜色。 [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)确定渐变的方向。  
  
##  <a name="m_clrfillgradient"></a>CMFCToolTipInfo::m_clrFillGradient  
 指定工具提示的渐变背景的结束颜色。  
  
```  
COLORREF m_clrFillGradient;  
```  
  
### <a name="remarks"></a>备注  
 如果`m_clrFillGradient`为-1，没有任何渐变。 否则，通过指定渐变初始颜色[CMFCToolTipInfo::m_clrFill](#m_clrfill)和渐变完成颜色由指定`m_clrFillGradient`。 [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)确定渐变的方向。  
  
##  <a name="m_clrtext"></a>CMFCToolTipInfo::m_clrText  
 指定所有工具提示的文本的颜色。  
  
```  
COLORREF m_clrText;  
```  
  
##  <a name="m_ngradientangle"></a>CMFCToolTipInfo::m_nGradientAngle  
 指定渐变绘制工具提示的背景时的角度。  
  
```  
int m_nGradientAngle;  
```  
  
### <a name="remarks"></a>备注  
 `m_nGradientAngle`指定以度为单位，在工具提示的背景的渐变偏离水平的角度。 如果`m_nGradientAngle`为 0，则渐变绘制从左到右。 如果`m_nGradientAngle`是介于 1 至 360，渐变将沿顺时针方向旋转的度数数。 如果`m_nGradientAngle`为-1，这是默认值，渐变从顶部到底部绘制。 这是设置相同`m_nGradientAngle`为 90。  
  
 [CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill`指定的颜色渐变的开始和[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient`指定渐变结束颜色。 如果`m_clrFillGradient`为-1，没有任何渐变。  
  
##  <a name="m_nmaxdescrwidth"></a>CMFCToolTipInfo::m_nMaxDescrWidth  
 指定它在每个工具提示中显示的说明的最大宽度。 如果描述宽度超过指定的值，文本换行。  
  
```  
int m_nMaxDescrWidth;  
```  
  
##  <a name="m_bvislmanagertheme"></a>CMFCToolTipInfo::m_bVislManagerTheme  
 指定应用程序的可视管理器是否控制所有工具提示的外观。  
  
```  
BOOL m_bVislManagerTheme;  
```  
  
### <a name="remarks"></a>备注  
 如果`m_bVislManagerTheme`是`TRUE`，每个工具提示请求一个新[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)从应用程序之前它们出现在屏幕上，并使用该对象中的值来确定它们的外观的可视化管理器。 其他成员您[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)将被忽略。  
  
##  <a name="operator_eq"></a>CMFCToolTipInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)

