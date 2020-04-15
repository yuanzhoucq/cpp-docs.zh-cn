---
title: CDrawingManager 类
ms.date: 11/04/2016
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
ms.openlocfilehash: 59c34a69b96cc9986db99b5f34bc38cf76f4909a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374020"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager 类

类`CDrawingManager`实现复杂的绘图算法。

## <a name="syntax"></a>语法

```
class CDrawingManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C绘图管理器：CDRAWING管理器](#cdrawingmanager)|构造 `CDrawingManager` 对象。|
|`CDrawingManager::~CDrawingManager`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDrawing 管理器：：CreateBitmap_32](#createbitmap_32)|创建与设备无关的 32 位位位图 （DIB），应用程序可以直接写入该位图。|
|[C绘图管理器：:D原阿尔法](#drawalpha)|显示具有透明或半透明像素的位图。|
|[Cdrawing 管理器：:D原始旋转](#drawrotated)|在给定矩形内旋转源 DC 内容 ，按 +/- 90 度旋转|
|[C 绘图管理器：:D原始椭圆](#drawellipse)|使用提供的填充和边框颜色绘制椭圆。|
|[CDrawing 管理器：:D原始渐变](#drawgradientring)|绘制环并填充其颜色渐变。|
|[C绘图管理器：:Drawline，Cdrawing经理：:DrawlineA](#drawline_cdrawingmanager__drawlinea)|画一条线。|
|[Cdrawing管理器：:D原始](#drawrect)|使用提供的填充和边框颜色绘制矩形。|
|[C绘图管理器：:D原始阴影](#drawshadow)|为矩形区域绘制阴影。|
|[绘图管理器：：填充4颜色渐变](#fill4colorsgradient)|用两个颜色渐变填充矩形区域。|
|[C 绘图管理器：：填充渐变](#fillgradient)|使用指定的颜色渐变填充矩形区域。|
|[C 绘图管理器：：填充渐变2](#fillgradient2)|使用指定的颜色渐变填充矩形区域。 还指定渐变颜色变化的方向。|
|[C 绘制管理器：灰色 Rect](#grayrect)|用指定的灰色填充矩形。|
|[Cdrawing 管理器：：突出显示](#highlightrect)|突出显示矩形区域。|
|[CDrawing 管理器：HLStoRGB_ONE](#hlstorgb_one)|将颜色从 HLS 表示形式转换为 RGB 表示形式。|
|[CDrawing管理器：：HLStoRGB_TWO](#hlstorgb_two)|将颜色从 HLS 表示形式转换为 RGB 表示形式。|
|[CDrawing 管理器：：HSVtoRGB](#hsvtorgb)|将颜色从 HSV 表示形式转换为 RGB 表示形式。|
|[CDrawing 管理器：：HuetoRGB](#huetorgb)|将色调值转换为红色、绿色或蓝色分量的帮助器方法。|
|[C 绘图管理器：：镜像重新](#mirrorrect)|翻转矩形区域。|
|[CDrawing经理：:Pixix阿尔法](#pixelalpha)|用于确定半透明像素的最终颜色的帮助器方法。|
|[C 绘图管理器：:P重影阴影掩码](#prepareshadowmask)|创建可用作阴影的位图。|
|[CDrawing 管理器：：RGBtoHSL](#rgbtohsl)|将颜色从 RGB 表示形式转换为 HSL 表示形式。|
|[CDrawing管理器：：RGBtoHSV](#rgbtohsv)|将颜色从 RGB 表示形式转换为 HSV 表示形式。|
|[C 绘图管理器：：设置Alpha像素](#setalphapixel)|帮助方法，该方法在位图中为部分透明像素提供颜色。|
|[C 绘图管理器：：设置像素](#setpixel)|帮助方法，将位图中的单个像素更改为指定颜色。|
|[绘图管理器：：智能混合颜色](#smartmixcolors)|基于加权比组合两种颜色。|

## <a name="remarks"></a>备注

该`CDrawingManager`类提供用于绘制阴影、颜色渐变和突出显示矩形的函数。 它还执行 alpha 混合。 可以使用此类直接更改应用程序的 UI。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>要求

**标题：** afxdraw 管理器.h

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a>C绘图管理器：CDRAWING管理器

构造[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)对象。

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>参数

*直流*<br/>
[在]对设备上下文的引用。 使用此`CDrawingManager`上下文进行绘图。

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a>CDrawing 管理器：：CreateBitmap_32

创建与设备无关的 32 位位位图 （DIB），应用程序可以直接写入该位图。

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*大小*|[在]指示位图大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)参数。|
|*pBits*|[出]指向接收 DIB 位值位置的数据指针的指针。|
|*位图*|原始位图的句柄|
|*clr透明*|指定原始位图的透明颜色的 RGB 值。|

### <a name="return-value"></a>返回值

如果此方法成功，则对新创建的 DIB 位图的句柄;否则 NULL。

### <a name="remarks"></a>备注

有关如何创建 DIB 位图的详细信息，请参阅[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap)。

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a>C绘图管理器：:D原阿尔法

显示具有透明或半透明像素的位图。

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>参数

*pDstDC*<br/>
[在]指向目标设备上下文的指针。

*rectDst*<br/>
[在]目标矩形。

*pSrcDC*<br/>
[在]指向源的设备上下文的指针。

*雷克斯尔*<br/>
[在]源矩形。

### <a name="remarks"></a>备注

此方法对两个位图执行 alpha 混合。 有关 Alpha 混合的详细信息，请参阅 Windows SDK 中的[AlphaBlend。](/windows/win32/api/wingdi/nf-wingdi-alphablend)

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a>C 绘图管理器：:D原始椭圆

使用提供的填充和边框颜色绘制椭圆。

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]椭圆的边界矩形。

*clrFill*<br/>
[在]此方法用于填充椭圆的颜色。

*clrLine*<br/>
[在]此方法用作椭圆边框的颜色。

### <a name="remarks"></a>备注

如果任一颜色设置为 -1，则此方法返回时不绘制椭圆。 如果边界矩形的任一尺寸为 0，则不绘制椭圆即可返回。

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a>CDrawing 管理器：:D原始渐变

绘制环并填充其颜色渐变。

```
BOOL DrawGradientRing(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    COLORREF colorBorder,
    int nAngle,
    int nWidth,
    COLORREF clrFace = (COLORREF)-1);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]指定渐变环边界的[CRect](../../atl-mfc-shared/reference/crect-class.md)参数。

*颜色开始*<br/>
[在]渐变的第一种颜色。

*颜色装饰*<br/>
[在]渐变的最后一种颜色。

*颜色边框*<br/>
[在]边框的颜色。

*nAngle*<br/>
[在]指定初始渐变绘图角度的参数。 此值应介于 0 和 360 之间。

*n 宽度*<br/>
[在]环的边框宽度。

*clrFace*<br/>
[在]戒指内部的颜色。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

由*矩形*定义的矩形必须至少为 5 像素宽和 5 像素高。

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a>C绘图管理器：:Drawline，Cdrawing经理：:DrawlineA

画一条线。

```
void DrawLine(
    int x1,
    int y1,
    int x2,
    int y2,
    COLORREF clrLine);

void DrawLineA(
    double x1,
    double y1,
    double x2,
    double y2,
    COLORREF clrLine);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*x1*|[在]线起点的 x 坐标。|
|*y1*|[在]线启动位置的 y 坐标。|
|*x2*|[在]x 坐标，线结束的位置。|
|*y2*|[在]线结束位置的 y 坐标。|
|*clrLine*|[在]线条的颜色。|

### <a name="remarks"></a>备注

如果*clrLine*等于 -1，此方法将失败。

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a>Cdrawing管理器：:D原始

使用提供的填充和边框颜色绘制矩形。

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]矩形的边界。

*clrFill*<br/>
[在]此方法用于填充矩形的颜色。

*clrLine*<br/>
[在]此方法用于矩形边框的颜色。

### <a name="remarks"></a>备注

如果任一颜色设置为 -1，则此方法返回而不绘制矩形。 如果矩形的任一尺寸为 0，它也会返回。

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a>C绘图管理器：:D原始阴影

为矩形区域绘制阴影。

```
BOOL DrawShadow(
    CRect rect,
    int nDepth,
    int iMinBrightness = 100,
    int iMaxBrightness = 50,
    CBitmap* pBmpSaveBottom = NULL,
    CBitmap* pBmpSaveRight = NULL,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bRightShadow = TRUE);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]应用程序中的矩形区域。 绘图管理器将在此区域下方绘制阴影。

*n 深度*<br/>
[在]阴影的宽度和高度。

*伊明亮度*<br/>
[在]阴影的最小亮度。

*iMax亮度*<br/>
[在]阴影的最大亮度。

*pBmp保存底*<br/>
[在]指向位图的指针，其中包含阴影底部的图像。

*pBmpSaveRight*<br/>
[在]指向位图的指针，其中包含在矩形右侧绘制的阴影的图像。

*clrBase*<br/>
[在]阴影的颜色。

*b 右影*<br/>
[在]指示阴影绘制方式的布尔参数。 如果*bRightShadow*是`TRUE`，`DrawShadow`则在矩形的右侧绘制阴影。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

您可以使用参数*pBmpSaveBottom*和*pBmpSaveRight*为底部和右侧阴影提供两个有效的位图。 如果这些[CBitmap](../../mfc/reference/cbitmap-class.md)对象具有附加的 GDI`DrawShadow`对象，则使用这些位图作为阴影。 如果`CBitmap`参数没有附加的 GDI 对象，请`DrawShadow`绘制阴影并将位图附加到参数。 在将来调用`DrawShadow`中，可以提供这些位图以加快绘图过程。 有关`CBitmap`类和 GDI 对象的详细信息，请参阅[图形对象](../../mfc/graphic-objects.md)。

如果这些参数中的任何一个为`NULL`，`DrawShadow`将自动绘制阴影。

如果将*bRightShadow*设置为 FALSE，阴影将在矩形区域的下方和左侧绘制。

### <a name="example"></a>示例

下面的示例演示如何使用`DrawShadow``CDrawingManager`类的方法。 此代码段是[道具表演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a>绘图管理器：：填充4颜色渐变

用两个颜色渐变填充矩形区域。

```
void Fill4ColorsGradient(
    CRect rect,
    COLORREF colorStart1,
    COLORREF colorFinish1,
    COLORREF colorStart2,
    COLORREF colorFinish2,
    BOOL bHorz = TRUE,
    int nPercentage = 50);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]要填充的矩形。

*颜色开始1*<br/>
[在]第一个颜色渐变的初始颜色。

*颜色完成1*<br/>
[在]第一个颜色渐变的最终颜色。

*颜色开始2*<br/>
[在]第二个颜色渐变的初始颜色。

*颜色完成2*<br/>
[在]第二个颜色渐变的最终颜色。

*布霍兹*<br/>
[在]表示`Fill4ColorsGradient`是水平渐变还是垂直渐变颜色的布尔参数。 TRUE 表示水平渐变。

*n 百分比*<br/>
[在]0-100 的整数。 此值指示要填充第一个颜色渐变的矩形的百分比。

### <a name="remarks"></a>备注

当矩形填充两个颜色渐变时，它们要么位于彼此之上，要么位于彼此旁边，具体取决于*bHorz*的值。 每个颜色渐变都使用方法[CDrawingManager：：fill 渐变](#fillgradient)独立计算。

如果*n%* 小于 0 或超过 100，此方法将生成断言失败。

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a>C 绘图管理器：：填充渐变

使用指定的颜色渐变填充矩形区域。

```
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]要填充的矩形区域。

*颜色开始*<br/>
[在]渐变的第一种颜色。

*颜色装饰*<br/>
[在]渐变的最终颜色。

*布霍兹*<br/>
[在]指定是`FillGradient`绘制水平渐变还是垂直渐变的布尔参数。

*n 开始平率*<br/>
[在]在开始渐变之前用`FillGradient`*颜色"开始"* 填充的矩形的百分比。

*n 结束平率*<br/>
[在]完成渐变后用颜色`FillGradient`*Finish*填充的矩形的百分比。

### <a name="example"></a>示例

下面的示例演示如何使用`FillGradient``CDrawingManager`类的方法。 此代码段是 MS [Office 2007 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a>C 绘图管理器：：填充渐变2

使用指定的颜色渐变填充矩形区域。

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]要填充的矩形区域。

*颜色开始*<br/>
[在]渐变的第一种颜色。

*颜色装饰*<br/>
[在]渐变的最后一种颜色。

*nAngle*<br/>
[在]介于 0 和 360 之间的整数。 此参数指定颜色渐变的方向。

### <a name="remarks"></a>备注

使用*nAngle*指定颜色渐变的方向。 指定颜色渐变的方向时，还可以指定颜色渐变的开始位置。 *nAngle*的值为 0 表示渐变从矩形顶部开始。 随着*nAngle*的增加，渐变的起始位置根据角度以逆时针方向移动。

### <a name="example"></a>示例

下面的示例演示如何使用`FillGradient2``CDrawingManager`类的方法。 此代码段是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a>C 绘制管理器：灰色 Rect

用指定的灰色填充矩形。

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]要填充的矩形区域。

*n 百分比*<br/>
[在]矩形中所需的灰色百分比。

*clr透明*<br/>
[在]透明颜色。

*clr 已禁用*<br/>
[在]如果*n%* 设置为 -1，则此方法用于消除饱和度的颜色。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

对于参数*n%，* 值越低表示颜色较深。

*n%* 的最大值为 200。 大于 200 的值不会更改矩形的外观。 如果值为 -1，则此方法使用*clr"禁用"* 来限制矩形的饱和度。

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a>Cdrawing 管理器：：突出显示

突出显示矩形区域。

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]要突出显示的矩形区域。

*n 百分比*<br/>
[在]表示突出显示应有多透明的百分比。

*clr透明*<br/>
[在]透明颜色。

*n 公差*<br/>
[在]0 和 255 之间的整数，指示颜色容差。

*clrBlend*<br/>
[在]用于混合的基本颜色。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

如果*n%* 介于 0 和`HighlightRect`99 之间，则使用 alpha 混合算法。 有关 Alpha 混合的详细信息，请参阅[Alpha 混合线和填充](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)。 如果*n%* 为 -1，则此方法使用默认高光级别。 如果*n%* 为 100，则此方法不执行任何操作并返回 TRUE。

该方法使用参数*n 容差*来确定是否突出显示矩形区域。 要突出显示矩形，应用程序的背景颜色和*clrTransparent*之间的差值必须小于每个颜色组件（红色、绿色和蓝色）中的*n 容忍度*。

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a>CDrawing 管理器：HLStoRGB_ONE

将颜色从 HLS 表示形式转换为 RGB 表示形式。

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>参数

*H*<br/>
[在]表示颜色色调的 0 和 1 之间的数字。

*L*<br/>
[在]0 和 1 之间的数字，指示颜色的亮度。

*S*<br/>
[在]0 和 1 之间的数字，指示颜色的饱和度。

### <a name="return-value"></a>返回值

提供的 HLS 颜色的 RGB 表示形式。

### <a name="remarks"></a>备注

颜色可以表示为 HSV（色相、饱和度和值）、HSL（色相、饱和度和亮度）或 RGB（红色、绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](/windows/win32/uxguide/vis-color)。

此方法和`CDrawingManager::HLStoRGB_TWO`方法执行相同的操作，但*要求 H*参数的值不同。 在此方法中 *，H*是圆的百分比。 在方法`CDrawingManager::HLStoRGB_TWO`中 *，H*是介于 0 和 360 之间的度值，两者都表示红色。 例如，对于`HLStoRGB_ONE` *，H*的值为 0.25 等效于 值 90`HLStoRGB_TWO`与 。

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a>CDrawing管理器：：HLStoRGB_TWO

将颜色从 HLS 表示形式转换为 RGB 表示形式。

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>参数

*H*<br/>
[在]表示颜色色调的 0 和 360 之间的数字。

*L*<br/>
[在]0 和 1 之间的数字，指示颜色的亮度。

*S*<br/>
[在]0 和 1 之间的数字，指示颜色的饱和度。

### <a name="return-value"></a>返回值

提供的 HLS 颜色的 RGB 表示形式。

### <a name="remarks"></a>备注

颜色可以表示为 HSV（色相、饱和度和值）、HSL（色相、饱和度和亮度）或 RGB（红色、绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](/windows/win32/uxguide/vis-color)。

此方法和[CDrawingManager：：：HLStoRGB_ONE](#hlstorgb_one)方法执行相同的操作，但*要求 H*参数的值不同。 在此方法中 *，H*是介于 0 和 360 之间的度值，两者都表示红色。 在[CDrawingManager：：HLStoRGB_ONE](#hlstorgb_one)方法中 *，H*是圆的百分比。 例如，对于`HLStoRGB_ONE` *，H*的值为 0.25 等效于 值 90`HLStoRGB_TWO`与 。

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a>CDrawing 管理器：：HSVtoRGB

将颜色从 HSV 表示形式转换为 RGB 表示形式。

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*H*|[在]介于 0 和 360 之间的数字，指示颜色的色调。|
|*S*|[在]0 和 1 之间的数字，指示颜色的饱和度。|
|*五*|[在]0 和 1 之间的数字，指示颜色的值。|

### <a name="return-value"></a>返回值

提供的 HSV 颜色的 RGB 表示形式。

### <a name="remarks"></a>备注

颜色可以表示为 HSV（色相、饱和度和值）、HSL（色相、饱和度和亮度）或 RGB（红色、绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](/windows/win32/uxguide/vis-color)。

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a>CDrawing 管理器：：HuetoRGB

将色调值转换为红色、绿色或蓝色分量。

```
static double __stdcall HuetoRGB(
    double m1,
    double m2,
    double h);

static BYTE __stdcall HueToRGB(
    float rm1,
    float rm2,
    float rh);
```

### <a name="parameters"></a>参数

*m1*<br/>
[在]请参阅备注。

*m2*<br/>
[在]请参阅备注。

*H*<br/>
[在]请参阅备注。

*rm1*<br/>
[在]请参阅备注。

*rm2*<br/>
[在]请参阅备注。

*Rh*<br/>
[在]请参阅备注。

### <a name="return-value"></a>返回值

提供色调的单个红色、绿色或蓝色分量。

### <a name="remarks"></a>备注

此方法是`CDrawingManager`一种帮助器方法，类用于计算 HSV 或 HSL 表示形式中颜色的单个红色、绿色和蓝色分量。 此方法不是设计为由程序员直接调用的。 输入参数是依赖于转换算法的值。

要将 HSV 或 HSL 颜色转换为 RGB 表示形式，请调用以下方法之一：

- [CDrawing 管理器：：HSVtoRGB](#hsvtorgb)

- [CDrawing 管理器：HLStoRGB_ONE](#hlstorgb_one)

- [CDrawing管理器：：HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a>C 绘图管理器：：镜像重新

翻转矩形区域。

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>参数

*矩形*<br/>
[在]要翻转的区域的边界矩形。

*布霍兹*<br/>
[在]表示矩形是水平翻转还是垂直翻转的布尔参数。

### <a name="remarks"></a>备注

此方法可以翻转`CDrawingManager`类拥有的设备上下文的任何区域。 如果*bHorz*设置为 TRUE，则此方法将水平翻转区域。 否则，它会垂直翻转区域。

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a>CDrawing经理：:Pixix阿尔法

计算半透明像素的最终颜色。

```
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    int percent);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    double percentR,
    double percentG,
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    COLORREF dstPixel,
    int percent);
```

### <a name="parameters"></a>参数

*srcPixel*<br/>
[在]像素的初始颜色。

*百分比*<br/>
[在]表示透明度百分比的 0 和 100 之间的数字。 值 100 表示初始颜色完全透明。

*百分比R*<br/>
[在]表示红色组件透明度百分比的 0 和 100 之间的数字。

*百分比G*<br/>
[在]表示绿色组件透明度百分比的 0 和 100 之间的数字。

*百分比B*<br/>
[在]表示蓝色组件透明度百分比的 0 和 100 之间的数字。

*dstPixel*<br/>
[在]像素的基本颜色。

### <a name="return-value"></a>返回值

半透明像素的最终颜色。

### <a name="remarks"></a>备注

这是一个用于着色半透明位图的帮助器类，并且不是设计为由程序员直接调用的。

当您使用具有*dstPixel*的方法的版本时，最终颜色是*dstPixel*和*srcPixel*的组合。 *srcPixel*颜色是*dstPixel*基础颜色上的部分透明颜色。

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a>C 绘图管理器：:P重影阴影掩码

创建可用作阴影的位图。

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>参数

*n 深度*<br/>
[在]阴影的宽度和高度。

*clrBase*<br/>
[在]阴影的颜色。

*伊明亮度*<br/>
[在]阴影的最小亮度。

*iMax亮度*<br/>
[在]阴影的最大亮度。

### <a name="return-value"></a>返回值

如果此方法成功，则对创建的位图的句柄;否则 NULL。

### <a name="remarks"></a>备注

如果*nDepth*设置为 0，则此方法将退出并返回 NULL。 如果*nDepth*小于 3，阴影的宽度和高度将设置为 3 像素。

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a>CDrawing 管理器：：RGBtoHSL

将颜色从红色、绿色和蓝色 （RGB） 表示转换为色调、饱和度和光度 （HSL） 表示。

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*Rgb*|[在]RGB 值中的颜色。|
|*H*|[出]指向双精度值的指针，该方法在其中存储颜色的色调。|
|*S*|[出]指向双精度值的指针，该方法在其中存储颜色的饱和度。|
|*L*|[出]指向双精度值的指针，该方法在其中存储颜色的轻盈度。|

### <a name="remarks"></a>备注

颜色可以表示为 HSV（色相、饱和度和值）、HSL（色相、饱和度和亮度）或 RGB（红色、绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](/windows/win32/uxguide/vis-color)。

*H*的返回值表示为 0 和 1 之间的分数，其中 0 和 1 表示红色。 *S*和*L*的返回值是介于 0 和 1 之间的数字。

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a>CDrawing管理器：：RGBtoHSV

将颜色从 RGB 表示形式转换为 HSV 表示形式。

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>参数

*Rgb*<br/>
[在]要在 RGB 表示形式中转换的颜色。

*H*<br/>
[出]指向双精度值的指针，此方法在其中存储颜色的结果色调。

*S*<br/>
[出]指向双精度值的指针，此方法存储生成的颜色饱和度。

*五*<br/>
[出]指向双精度值的指针，其中此方法存储颜色的生成值。

### <a name="remarks"></a>备注

颜色可以表示为 HSV（色相、饱和度和值）、HSL（色相、饱和度和亮度）或 RGB（红色、绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](/windows/win32/uxguide/vis-color)。

*H*的返回值是介于 0 和 360 之间的数字，其中 0 和 360 都表示红色。 *S*和*V*的返回值是介于 0 和 1 之间的数字。

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a>C 绘图管理器：：设置Alpha像素

在位图中为透明像素添加颜色。

```
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,
    CRect rect,
    int x,
    int y,
    int percent,
    int iShadowSize,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bIsRight = TRUE);
```

### <a name="parameters"></a>参数

*pBits*<br/>
[在]指向位图的位值的指针。

*矩形*<br/>
[在]应用程序中的矩形区域。 绘图管理器在此区域的下方和右侧绘制阴影。

** x <br/>
[在]像素到颜色的水平坐标。

*Y*<br/>
[在]像素到颜色的垂直坐标。

*百分比*<br/>
[在]透明度的百分比。

*iShadowSize*<br/>
[在]阴影的宽度和高度。

*clrBase*<br/>
[在]阴影的颜色。

*bIsRight*<br/>
[在]指示要着色的像素的布尔参数。 有关详细信息，请参阅“备注”部分。

### <a name="remarks"></a>备注

此方法是[CDrawingManager：:DrawShadow](#drawshadow)方法使用的帮助方法。 我们建议您，如果要绘制阴影，请改为调用`CDrawingManager::DrawShadow`。

如果*bIsRight*设置为 TRUE，则从*rect*的右*边缘测量到*颜色的像素 x 像素。 如果是 FALSE，则从*rect*的左*边缘测量到*颜色的像素 x 像素。

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a>C 绘图管理器：：设置像素

将位图中的单个像素更改为指定颜色。

```
static void __stdcall SetPixel(
    COLORREF* pBits,
    int cx,
    int cy,
    int x,
    int y,
    COLORREF color);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*pBits*|[在]指向位图的位值的指针。|
|*残雪*|[在]位图的总宽度。|
|*cy*|[在]位图的总高度。|
|** x |[在]要更改的位图中像素的 x 坐标。|
|*Y*|[在]要更改的位图中像素的 y 坐标。|
|*颜色*|[在]由提供的坐标标识的像素的新颜色。|

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a>绘图管理器：：智能混合颜色

基于加权比组合两种颜色。

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*颜色1*|[在]要混合的第一种颜色。|
|*颜色2*|[在]要混合的第二种颜色。|
|*德布勒雷比*|[在]新颜色亮度的比率。 `SmartMixColors`在确定最终颜色之前，将混合颜色的亮度乘以此比率。|
|*k1*|[在]第一种颜色的加权比率。|
|*k2*|[在]第二种颜色的加权比率。|

### <a name="return-value"></a>返回值

表示所提供颜色的加权混合的颜色。

### <a name="remarks"></a>备注

如果*k1*或*k2*小于零，则此方法失败，出现错误。 如果这两个参数都设置为 0，则方法将返回`RGB(0, 0, 0)`。

加权比率的计算公式如下：（颜色 1 k1 \* = 颜色\*2 k2）/（k1 = k2）。 确定加权比后，该方法计算混合颜色的亮度。 然后，它将亮度乘以*dblLumratio。* 如果值大于 1.0，则该方法将混合颜色的亮度设置为新值。 否则，亮度设置为 1.0。

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a>Cdrawing 管理器：:D原始旋转

将给定矩形内的源 DC 内容旋转 90 度。

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>参数

*整流*<br/>
目标矩形。

*直流*<br/>
源设备上下文。

*bClockWise*<br/>
TRUE 表示旋转 +90 度;TRUE 表示旋转 90 度;FALSE 表示旋转 -90 度。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
