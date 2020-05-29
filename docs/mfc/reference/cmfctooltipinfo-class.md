---
title: CMFCTool提示信息类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
ms.openlocfilehash: 000a2fd33928e59685efa6f145406542a4935819
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377337"
---
# <a name="cmfctooltipinfo-class"></a>CMFCTool提示信息类

存储有关工具提示视觉外观的信息。

## <a name="syntax"></a>语法

```
class CMFCToolTipInfo
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCToolTipInfo::operator=](#operator_eq)||

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFCTool提示信息：：m_bBalloonTooltip](#m_bballoontooltip)|指示工具提示是否具有气球外观的布尔变量。|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|指示工具提示标签是否以粗体显示的布尔变量。|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|指示工具提示是否包含说明的布尔变量。|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|指示工具提示是否包含图标的布尔变量。|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|指示分隔符是否显示在工具提示标签和工具提示说明之间的布尔变量。|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|指示工具提示是否具有圆角的布尔变量。|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|一个布尔变量，指示工具提示的外观是否应由可视化管理器控制（请参阅[CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)）。|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|工具提示边框的颜色。|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|工具提示背景的颜色。|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|工具提示中渐变填充的颜色。|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|工具提示中的文本颜色。|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|工具提示中渐变填充的角度。|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|工具提示中说明的最大可能宽度（以像素为单位）。|

## <a name="remarks"></a>备注

将[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)`CMFCToolTipInfo`类 和[CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)一起使用，在应用程序中实现自定义的工具提示。 有关如何使用这些工具提示类的示例，请参阅[CMFCToolTipCtrl 类主题](../../mfc/reference/cmfctooltipctrl-class.md)。

## <a name="example"></a>示例

下面的示例演示了如何在 `CMFCToolTipInfo` 类中设置多个成员变量的值的方法。

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>要求

**标题：** afxtooltipctrl.h

## <a name="cmfctooltipinfom_bballoontooltip"></a><a name="m_bballoontooltip"></a>CMFCTool提示信息：：m_bBalloonTooltip

指定所有工具提示的显示样式。

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>备注

TRUE 表示工具提示使用气球样式，FALSE 表示工具提示使用矩形样式。

## <a name="cmfctooltipinfom_bboldlabel"></a><a name="m_bboldlabel"></a>CMFCTool提示信息：：m_bBoldLabel

指定工具提示文本的字体是否为粗体。

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>备注

将此成员设置为 TRUE 以显示带有粗体字体的工具提示文本，或将 FALSE 设置为显示非粗体字体的工具提示标签。

## <a name="cmfctooltipinfom_bdrawdescription"></a><a name="m_bdrawdescription"></a>CMFCTool提示信息：：m_bDrawDescription

指定每个工具提示是否显示描述文本。

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>备注

将此成员设置为 TRUE 以显示说明，或 FALSE 以隐藏说明。 您可以通过调用[CMFCToolTipCtrl：：：设置描述](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)来指定工具提示上的说明

## <a name="cmfctooltipinfom_bdrawicon"></a><a name="m_bdrawicon"></a>CMFCTool提示信息：：m_bDrawIcon

指定是否显示所有工具提示显示图标。

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>备注

将此成员设置为 TRUE 以在每个工具提示上显示图标，或"FALSE"显示没有图标的工具提示。

## <a name="cmfctooltipinfom_bdrawseparator"></a><a name="m_bdrawseparator"></a>CMFCTool提示信息：：m_bDrawSeparator

指定每个工具提示的标签和说明之间是否有分隔符。

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>备注

将此成员设置为 TRUE 以在工具提示标签和说明之间显示分隔符，或将 FALSE 设置为显示没有分隔符的工具提示。

## <a name="cmfctooltipinfom_broundedcorners"></a><a name="m_broundedcorners"></a>CMFCTool提示信息：：m_bRoundedCorners

指定所有工具提示是否具有圆角。

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>备注

将此成员设置为 TRUE 以在工具提示上显示圆角，或"FALSE"以在工具提示上显示矩形角。

## <a name="cmfctooltipinfom_clrborder"></a><a name="m_clrborder"></a>CMFCTool提示信息：m_clrBorder

指定所有工具提示上的边框颜色。

```
COLORREF m_clrBorder;
```

## <a name="cmfctooltipinfom_clrfill"></a><a name="m_clrfill"></a>CMFCTool提示信息：：m_clrFill

指定工具提示背景的颜色。

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>备注

如果[CMFCToolTipInfo：m_clrFillGradient](#m_clrfillgradient)为 -1，则工具提示背景颜色`m_clrFill`为 。 否则，`m_clrFill`指定渐变开头的颜色，并`m_clrFillGradient`指定渐变末尾的颜色。 [CMFCToolTipInfo：m_nGradientAngle](#m_ngradientangle)确定渐变的方向。

## <a name="cmfctooltipinfom_clrfillgradient"></a><a name="m_clrfillgradient"></a>CMFCTool提示信息：m_clrFillGradient

指定工具提示渐变背景的结束颜色。

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>备注

如果`m_clrFillGradient`为 -1，则没有渐变。 否则，渐变初始颜色由[CMFCToolTipInfo：：m_clrFill](#m_clrfill)指定，渐变完成颜色由 指定`m_clrFillGradient`。 [CMFCToolTipInfo：m_nGradientAngle](#m_ngradientangle)确定渐变的方向。

## <a name="cmfctooltipinfom_clrtext"></a><a name="m_clrtext"></a>CMFCTool提示信息：：m_clrText

指定所有工具提示的文本颜色。

```
COLORREF m_clrText;
```

## <a name="cmfctooltipinfom_ngradientangle"></a><a name="m_ngradientangle"></a>CMFCTool提示信息：：m_nGradientAngle

指定在工具提示的背景上绘制渐变的角度。

```
int m_nGradientAngle;
```

### <a name="remarks"></a>备注

`m_nGradientAngle`指定工具尖背景上的渐变与水平偏移的角度（以度表示）。 如果`m_nGradientAngle`为 0，则从左向右绘制渐变。 如果`m_nGradientAngle`介于 1 和 360 之间，则渐变按该度数顺时针旋转。 如果`m_nGradientAngle`为 -1（默认值），则渐变从上到下绘制。 这与设置为`m_nGradientAngle`90 相同。

[CMFCToolTipInfo：：m_clrFill](#m_clrfill)`clrFill`指定渐变开头的颜色[，CMFCToolTipInfo：：m_clrFillGradient](#m_clrfillgradient)`clrFillGradient`指定渐变末端的颜色。 如果`m_clrFillGradient`为 -1，则没有渐变。

## <a name="cmfctooltipinfom_nmaxdescrwidth"></a><a name="m_nmaxdescrwidth"></a>CMFCTool提示信息：：m_nMaxDescrWidth

指定它在每个工具提示中显示的描述的最大宽度。 如果描述宽度超过指定值，则换行文本。

```
int m_nMaxDescrWidth;
```

## <a name="cmfctooltipinfom_bvislmanagertheme"></a><a name="m_bvislmanagertheme"></a>CMFCTool提示信息：：m_bVislManagerTheme

指定应用程序的可视化管理器是否控制所有工具提示的外观。

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>备注

如果`m_bVislManagerTheme`为 TRUE，则每个工具提示都会在应用程序的视觉管理器出现在屏幕上之前向应用程序的视觉管理器请求新的[CMFCToolTipInfo，](../../mfc/reference/cmfctooltipinfo-class.md)并使用该对象中的值来确定它们的外观。 [您的 CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)的其他成员将被忽略。

## <a name="cmfctooltipinfooperator"></a><a name="operator_eq"></a>CMFCTool提示信息：：操作员*

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>参数

[在]*斯尔克*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CTooltipManager 类](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipCtrl 类](../../mfc/reference/cmfctooltipctrl-class.md)
