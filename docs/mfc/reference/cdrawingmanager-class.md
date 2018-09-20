---
title: CDrawingManager 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 013dc05b4ecbfc31f0f475d50e3a3be6d74c846d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386608"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager 类

`CDrawingManager`类实现复杂的绘图算法。

## <a name="syntax"></a>语法

```
class CDrawingManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|构造 `CDrawingManager` 对象。|
|`CDrawingManager::~CDrawingManager`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|创建应用程序可以直接写入一个 32 位与设备无关位图 (DIB)。|
|[CDrawingManager::DrawAlpha](#drawalpha)|显示透明或半透明的像素的位图。|
|[CDrawingManager::DrawRotated](#drawrotated)|旋转的源 DC 的 + /-90 度的给定矩形内的内容|
|[CDrawingManager::DrawEllipse](#drawellipse)|绘制一个椭圆使用提供的填充和边框颜色。|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|绘制一个环，并使用颜色渐变填充它。|
|[CDrawingManager::DrawLine CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|绘制一条线。|
|[CDrawingManager::DrawRect](#drawrect)|绘制一个具有提供的填充和边框颜色的矩形。|
|[CDrawingManager::DrawShadow](#drawshadow)|绘制的矩形区域的阴影。|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|用两种颜色渐变填充的矩形区域。|
|[CDrawingManager::FillGradient](#fillgradient)|用指定的颜色渐变填充的矩形区域。|
|[CDrawingManager::FillGradient2](#fillgradient2)|用指定的颜色渐变填充的矩形区域。 此外指定渐变的颜色更改的方向。|
|[CDrawingManager::GrayRect](#grayrect)|使用指定的灰色颜色填充的矩形。|
|[CDrawingManager::HighlightRect](#highlightrect)|突出显示的矩形区域。|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|将一种颜色从 HLS 表示形式转换为 RGB 表示形式。|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|将一种颜色从 HLS 表示形式转换为 RGB 表示形式。|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|将一种颜色从 HSV 表示形式转换为 RGB 表示形式。|
|[CDrawingManager::HuetoRGB](#huetorgb)|将色调值转换为红色、 绿色还是蓝色组件的帮助器方法。|
|[CDrawingManager::MirrorRect](#mirrorrect)|翻转的矩形区域。|
|[CDrawingManager::PixelAlpha](#pixelalpha)|确定一个半透明的像素的最终颜色的帮助器方法。|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|创建可用作阴影的位图。|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|将一种颜色 RGB 表示形式转换为 HSL 表示形式。|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|将一种颜色 RGB 表示形式转换为 HSV 表示形式。|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|颜色位图中的部分透明像素的帮助器方法。|
|[CDrawingManager::SetPixel](#setpixel)|为指定的颜色更改位图中的单个像素的帮助器方法。|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|结合了两种颜色根据加权的比率。|

## <a name="remarks"></a>备注

`CDrawingManager`类提供用于绘制阴影，颜色渐变和突出显示的矩形的函数。 它还执行 alpha 值混合处理。 此类可用于直接更改应用程序的 UI。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>要求

**标头：** afxdrawmanager.h

##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager

构造[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)对象。

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>参数

*dc*<br/>
[in]对设备上下文的引用。 `CDrawingManager`使用此上下文进行绘制。

##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32

创建应用程序可以直接写入一个 32 位与设备无关位图 (DIB)。

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
|参数|描述|
|*size*|[in]一个[CSize](../../atl-mfc-shared/reference/csize-class.md)参数，用于指示位图的大小。|
|*pBits*|[out]指向接收的 DIB 的位置的数据指针的位值。|
|*位图*|原始位图的句柄|
|*clrTransparent*|一个指定原始位图透明颜色 RGB 值。|

### <a name="return-value"></a>返回值

如果此方法成功，则新创建 DIB 位图的句柄否则为，为 NULL。

### <a name="remarks"></a>备注

有关如何创建 DIB 位图的详细信息，请参阅[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibitmap)。

##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha

显示透明或半透明的像素的位图。

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>参数

*pDstDC*<br/>
[in]指向目标设备上下文的指针。

*rectDst*<br/>
[in]目标矩形。

*pSrcDC*<br/>
[in]指向源的设备上下文的指针。

*rectSrc*<br/>
[in]源矩形。

### <a name="remarks"></a>备注

此方法执行两个位图的 alpha 值混合处理。 Alpha 值混合处理的详细信息，请参阅[AlphaBlend](/windows/desktop/api/wingdi/nf-wingdi-alphablend) Windows SDK 中。

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

绘制一个椭圆使用提供的填充和边框颜色。

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>参数

*rect*<br/>
[in]椭圆的边框。

*clrFill*<br/>
[in]此方法用于填充椭圆颜色。

*clrLine*<br/>
[in]此方法使用作为椭圆的边框颜色。

### <a name="remarks"></a>备注

此方法返回，而不绘制一个椭圆，如果任意一种颜色设置为-1。 它还返回不会绘制一个椭圆，如果边界矩形任一维度为 0。

##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing

绘制一个环，并使用颜色渐变填充它。

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

*rect*<br/>
[in]一个[CRect](../../atl-mfc-shared/reference/crect-class.md)参数，它指定渐变环的边界。

*colorStart*<br/>
[in]第一种颜色的渐变。

*colorFinish*<br/>
[in]最后一种颜色的渐变。

*colorBorder*<br/>
[in]边框的颜色。

*nAngle*<br/>
[in]指定初始渐变绘制角度的参数。 此值应介于 0 至 360 之间。

*nWidth*<br/>
[in]环的边框的宽度。

*clrFace*<br/>
[in]环的内部的颜色。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

定义的矩形*rect*必须至少为 5 像素宽和 5 像素高。

##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine CDrawingManager::DrawLineA

绘制一条线。

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
|参数|描述|
|*x1*|[in]在行的开始位置的 x 坐标。|
|*y1*|[in]在行的开始位置 y 坐标。|
|*x2*|[in]线条终点的 x 坐标。|
|*y2*|[in]线条终点的 y 坐标。|
|*clrLine*|[in]线条的颜色。|

### <a name="remarks"></a>备注

如果此方法将失败*clrLine*等于-1。

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

绘制一个具有提供的填充和边框颜色的矩形。

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>参数

*rect*<br/>
[in]矩形边界。

*clrFill*<br/>
[in]此方法用于填充矩形的颜色。

*clrLine*<br/>
[in]此方法使用为矩形的边框颜色。

### <a name="remarks"></a>备注

此方法返回，而不绘制一个矩形，如果任意一种颜色设置为-1。 它还返回矩形的任一维度如果为 0。

##  <a name="drawshadow"></a>  CDrawingManager::DrawShadow

绘制的矩形区域的阴影。

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

*rect*<br/>
[in]你的应用程序中的矩形区域。 绘制管理器将在此区域的下方绘制阴影。

*nDepth*<br/>
[in]宽度和高度的阴影。

*iMinBrightness*<br/>
[in]阴影的亮度最小。

*iMaxBrightness*<br/>
[in]最大阴影的亮度。

*pBmpSaveBottom*<br/>
[in]指向包含卷影的下半部分的图像的位图的指针。

*pBmpSaveRight*<br/>
[in]指向包含该矩形右侧绘制的阴影的图像的位图的指针。

*clrBase*<br/>
[in]阴影的颜色。

*bRightShadow*<br/>
[in]一个布尔参数，指示如何绘制阴影。 如果*bRightShadow*是`TRUE`，`DrawShadow`矩形右侧绘制阴影。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

可以使用的参数的底部和右侧阴影提供两个有效位图*pBmpSaveBottom*并*pBmpSaveRight*。 如果这些[CBitmap](../../mfc/reference/cbitmap-class.md)对象具有附加的 GDI 对象，`DrawShadow`将使用这些位图作为阴影。 如果`CBitmap`参数不具有附加的 GDI 对象，`DrawShadow`绘制阴影，并将位图附加到的参数。 在将来对`DrawShadow`，可以提供这些位图来加速绘制过程。 有关详细信息`CBitmap`类和 GDI 对象，请参阅[图形对象](../../mfc/graphic-objects.md)。

如果上述这些参数是`NULL`，`DrawShadow`自动绘制阴影。

如果您设置*bRightShadow*为 FALSE，阴影将从中提取到的矩形区域的左侧。

### <a name="example"></a>示例

下面的示例演示如何使用`DrawShadow`方法的`CDrawingManager`类。 此代码片段属于[Prop 表演示示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>  CDrawingManager::Fill4ColorsGradient

用两种颜色渐变填充的矩形区域。

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

*rect*<br/>
[in]要填充的矩形。

*colorStart1*<br/>
[in]第一个颜色渐变的初始颜色。

*colorFinish1*<br/>
[in]第一个颜色渐变的最终颜色。

*colorStart2*<br/>
[in]第二个颜色渐变的初始颜色。

*colorFinish2*<br/>
[in]第二个颜色渐变的最终颜色。

*bHorz*<br/>
[in]一个布尔参数，指示是否`Fill4ColorsGradient`颜色水平或垂直渐变。 TRUE 表示水平渐变。

*nPercentage*<br/>
[in]从 0-100 的整数。 此值指示要使用的第一个颜色渐变填充的矩形的百分比。

### <a name="remarks"></a>备注

当使用两个颜色渐变填充矩形时，它们是位于上面彼此还是到对方，具体取决于值的下一步*bHorz*。 使用方法单独计算每个颜色渐变[CDrawingManager::FillGradient](#fillgradient)。

如果此方法将生成断言失败*nPercentage*小于 0 或大于 100。

##  <a name="fillgradient"></a>  CDrawingManager::FillGradient

用指定的颜色渐变填充的矩形区域。

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

*rect*<br/>
[in]要填充的矩形区域。

*colorStart*<br/>
[in]第一种颜色的渐变。

*colorFinish*<br/>
[in]最终的渐变颜色。

*bHorz*<br/>
[in]一个布尔参数，指定是否`FillGradient`应绘制水平或垂直渐变。

*nStartFlatPercentage*<br/>
[in]矩形的百分比，`FillGradient`填充*colorStart*启动渐变之前。

*nEndFlatPercentage*<br/>
[in]矩形的百分比，`FillGradient`填充*colorFinish*完成渐变后。

### <a name="example"></a>示例

下面的示例演示如何使用`FillGradient`方法的`CDrawingManager`类。 此代码片段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>  CDrawingManager::FillGradient2

用指定的颜色渐变填充的矩形区域。

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>参数

*rect*<br/>
[in]要填充的矩形区域。

*colorStart*<br/>
[in]第一种颜色的渐变。

*colorFinish*<br/>
[in]最后一种颜色的渐变。

*nAngle*<br/>
[in]介于 0 至 360 之间的整数。 此参数指定的颜色渐变的方向。

### <a name="remarks"></a>备注

使用*nAngle*指定的颜色渐变的方向。 当您指定的颜色渐变的方向时，您还指定的颜色渐变的开始位置。 值为 0， *nAngle*指示渐变的开始时间的矩形的顶部。 作为*nAngle*增加，起始位置用于根据表示的角度以逆时针方向移动渐变。

### <a name="example"></a>示例

下面的示例演示如何使用`FillGradient2`方法的`CDrawingManager`类。 此代码片段属于[新的控件示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>  CDrawingManager::GrayRect

使用指定的灰色颜色填充的矩形。

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>参数

*rect*<br/>
[in]要填充的矩形区域。

*nPercentage*<br/>
[in]灰色的矩形中所需的百分比。

*clrTransparent*<br/>
[in]透明的颜色。

*clrDisabled*<br/>
[in]如果此方法使用的重复数据的饱和度的颜色*nPercentage*设置为-1。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

为参数*nPercentage*，较低的值指示较深的颜色。

最大值*nPercentage*为 200。 200 个以上的更大的值不会更改矩形的外观。 如果值为-1，此方法将使用*clrDisabled*限制的矩形的饱和度。

##  <a name="highlightrect"></a>  CDrawingManager::HighlightRect

突出显示的矩形区域。

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>参数

*rect*<br/>
[in]若要突出显示矩形区域。

*nPercentage*<br/>
[in]一个百分比，指示如何透明应为突出显示。

*clrTransparent*<br/>
[in]透明的颜色。

*nTolerance*<br/>
[in]一个介于 0 和 255 之间的整数，指示颜色容差。

*clrBlend*<br/>
[in]用于混合基础颜色。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果*nPercentage*介于 0 和 99 之间`HighlightRect`使用 alpha 值混合处理算法。 Alpha 值混合处理的详细信息，请参阅[Alpha 混合线条和填充](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)。 如果*nPercentage*为-1，此方法使用默认的突出显示级别。 如果*nPercentage*为 100，此方法不执行任何操作，则返回 TRUE。

该方法使用参数*nTolerance*以确定是否要突出显示的矩形区域。 若要突出显示矩形的背景色的应用程序之间的差异和*clrTransparent*必须是小于*nTolerance*中每个颜色组件 （红色、 绿色和蓝色）。

##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE

将一种颜色从 HLS 表示形式转换为 RGB 表示形式。

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>参数

*H*<br/>
[in]介于 0 和 1 之间的数字表示颜色的色调。

*L*<br/>
[in]介于 0 和 1 之间的数字表示颜色的亮度。

*S*<br/>
[in]介于 0 和 1 之间的数字表示颜色的饱和度。

### <a name="return-value"></a>返回值

提供 HLS 颜色的 RGB 表示形式。

### <a name="remarks"></a>备注

一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。

此方法和`CDrawingManager::HLStoRGB_TWO`方法执行相同的操作，但需要不同的值*H*参数。 在此方法中， *H*是圆的百分比。 在中`CDrawingManager::HLStoRGB_TWO`方法， *H*是介于 0 到 360 之间，这两者都代表红色之间的程度。 例如，对于`HLStoRGB_ONE`，值为 0.25 *H*等效于值为 90 与`HLStoRGB_TWO`。

##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO

将一种颜色从 HLS 表示形式转换为 RGB 表示形式。

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>参数

*H*<br/>
[in]表示颜色的色调 0 到 360 之间的数字。

*L*<br/>
[in]介于 0 和 1 之间的数字表示颜色的亮度。

*S*<br/>
[in]介于 0 和 1 之间的数字表示颜色的饱和度。

### <a name="return-value"></a>返回值

提供 HLS 颜色的 RGB 表示形式。

### <a name="remarks"></a>备注

一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。

此方法和[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法执行相同的操作，但需要不同的值*H*参数。 在此方法中， *H*是介于 0 到 360 之间，这两者都代表红色之间的程度。 在中[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法， *H*是圆的百分比。 例如，对于`HLStoRGB_ONE`，值为 0.25 *H*等效于值为 90 与`HLStoRGB_TWO`。

##  <a name="hsvtorgb"></a>  CDrawingManager::HSVtoRGB

将一种颜色从 HSV 表示形式转换为 RGB 表示形式。

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*H*|[in]指示的颜色的色调介于 0 至 360 之间数字。|
|*S*|[in]介于 0 和 1 之间的数字表示颜色的饱和度。|
|*V*|[in]介于 0 和 1，指示该颜色的值之间的数字。|

### <a name="return-value"></a>返回值

提供 HSV 颜色的 RGB 表示形式。

### <a name="remarks"></a>备注

一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。

##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB

将色调值转换为红色、 绿色还是蓝色组件。

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

*M1*<br/>
[in]请参阅备注。

*M2*<br/>
[in]请参阅备注。

*h*<br/>
[in]请参阅备注。

*rm1*<br/>
[in]请参阅备注。

*rm2*<br/>
[in]请参阅备注。

*rh*<br/>
[in]请参阅备注。

### <a name="return-value"></a>返回值

提供 hue 单个红色、 绿色还是蓝色组件。

### <a name="remarks"></a>备注

此方法是帮助器方法的`CDrawingManager`类用来计算颜色 HSV 或 HSL 表示形式中的单个红色、 绿色和蓝色组件。 此方法不用于直接通过程序员调用。 输入的参数是依赖于转换算法的值。

若要将 HSV 或 HSL 颜色转换为 RGB 表示形式，请调用以下方法之一：

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>  CDrawingManager::MirrorRect

翻转的矩形区域。

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>参数

*rect*<br/>
[in]要翻转的区域的边框。

*bHorz*<br/>
[in]一个布尔参数，指示该矩形翻转水平或垂直。

### <a name="remarks"></a>备注

此方法可以浏览任何区域中拥有的设备上下文的`CDrawingManager`类。 如果*bHorz*是设置为 TRUE，此方法水平翻转的区域。 否则，它垂直翻转的区域。

##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha

计算一个半透明的像素的最终颜色。

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
[in]初始颜色像素。

*%*<br/>
[in]表示百分比透明度的 0 到 100 之间的数字。 值为 100 表示的初始颜色完全透明。

*percentR*<br/>
[in]介于 0 和 100 之间的数字表示红色分量的透明性的百分比。

*percentG*<br/>
[in]介于 0 和 100 之间的数字表示绿色组件的透明度的百分比。

*percentB*<br/>
[in]介于 0 和 100 之间的数字表示蓝色分量的透明性的百分比。

*dstPixel*<br/>
[in]基础像素颜色。

### <a name="return-value"></a>返回值

半透明的像素最终颜色。

### <a name="remarks"></a>备注

这是用于着色半透明位图的帮助器类而不是编程人员直接调用。

当使用具有方法的版本*dstPixel*，最终颜色是的组合*dstPixel*并*srcPixel*。 *SrcPixel*颜色通过基础的颜色为部分透明颜色*dstPixel*。

##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask

创建可用作阴影的位图。

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>参数

*nDepth*<br/>
[in]宽度和高度的阴影。

*clrBase*<br/>
[in]阴影的颜色。

*iMinBrightness*<br/>
[in]阴影的亮度最小。

*iMaxBrightness*<br/>
[in]最大阴影的亮度。

### <a name="return-value"></a>返回值

如果成功，则此方法是创建位图的句柄否则为，为 NULL。

### <a name="remarks"></a>备注

如果*nDepth*是设置为 0，此方法退出并返回 NULL。 如果*nDepth*小于 3，则的宽度和阴影的高度设置为 3 个像素。

##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL

将一种颜色从红色、 绿色和蓝色 (RGB) 表示形式转换为色调、 饱和度和亮度 (HSL) 表示形式。

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
|参数|描述|
|*rgb*|[in]RGB 值中的颜色。|
|*H*|[out]指向一个双精度值，该方法存储的颜色色调的位置的指针。|
|*S*|[out]指向一个双精度值，该方法存储的颜色饱和度的位置的指针。|
|*L*|[out]指向一个双精度值，该方法存储的颜色亮度的位置的指针。|

### <a name="remarks"></a>备注

一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。

返回的值*H*表示为介于 0 和 1，0 和 1 表示红色之间的一小部分。 为返回的值*S*并*L*是介于 0 和 1 之间的数字。

##  <a name="rgbtohsv"></a>  CDrawingManager::RGBtoHSV

将一种颜色 RGB 表示形式转换为 HSV 表示形式。

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>参数

*rgb*<br/>
[in]要转换的 RGB 表示形式中的颜色。

*H*<br/>
[out]指向一个双精度值，此方法将生成的颜色色调的存储位置的指针。

*S*<br/>
[out]指向一个双精度值，此方法将生成的颜色饱和度的存储位置的指针。

*V*<br/>
[out]指向一个双精度值，此方法将生成的值的颜色的存储位置的指针。

### <a name="remarks"></a>备注

一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关颜色的不同表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。

返回的值*H*是介于 0 至 360 之间的数字 0 至 360 其中表示红色。 返回值*S*并*V*是介于 0 和 1 之间的数字。

##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel

位图中的透明像素的颜色。

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
[in]指向位图的位值的指针。

*rect*<br/>
[in]你的应用程序中的矩形区域。 绘制 manager 绘制阴影下方和右侧的此区域。

*x*<br/>
[in]为颜色像素水平坐标。

*y*<br/>
[in]为颜色像素垂直坐标。

*%*<br/>
[in]透明度的百分比。

*iShadowSize*<br/>
[in]宽度和高度的阴影。

*clrBase*<br/>
[in]阴影的颜色。

*bIsRight*<br/>
[in]一个布尔参数，指示哪些像素到颜色。 有关详细信息，请参阅备注部分。

### <a name="remarks"></a>备注

此方法是使用一个帮助器方法[CDrawingManager::DrawShadow](#drawshadow)方法。 我们建议，如果你想要绘制阴影，调用`CDrawingManager::DrawShadow`相反。

如果*bIsRight*是设置为 TRUE，为颜色的像素为单位*x*的右边缘像素*rect*。 如果为 FALSE，单位为颜色像素*x*像素，距左边缘*rect*。

##  <a name="setpixel"></a>  CDrawingManager::SetPixel

为指定的颜色更改位图中的单个像素。

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
|参数|描述|
|*pBits*|[in]指向位图的位值的指针。|
|*cx*|[in]位图的总宽度。|
|*cy*|[in]位图的总高度。|
|*x*|[in]中要更改的位图的像素 x 坐标。|
|*y*|[in]中要更改的位图的像素的 y 坐标。|
|*颜色*|[in]新颜色标识由提供的坐标的像素。|

##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors

结合了两种颜色根据加权的比率。

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
|参数|描述|
|*color1*|[in]第一种颜色混合。|
|*color2*|[in]若要混合使用第二种颜色。|
|*dblLumRatio*|[in]新颜色的亮度的比率。 `SmartMixColors` 在确定最终颜色之前乘以此比率在帮助混合颜色的亮度。|
|*版 k1*|[in]第一种颜色加权的比率。|
|*k2*|[in]第二种颜色加权的比率。|

### <a name="return-value"></a>返回值

表示提供颜色的加权的混合的颜色。

### <a name="remarks"></a>备注

此方法会失败并出错，如果任一*k1*或*k2*小于零。 如果这些参数设置为 0，该方法返回`RGB(0, 0, 0)`。

使用以下公式计算加权的比率: (color1 \* k1 + color2 \* k2) /(k1 + k2)。 加权的比率确定后，该方法计算混合的颜色的亮度。 然后将相乘的亮度*dblLumRatio*。 如果值大于 1.0，方法会将混合的颜色的亮度设置为新值。 否则，亮度是设置为 1.0。

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

源 DC 在给定矩形内的内容旋转 90 度。

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>参数

*rectDest*<br/>
目标矩形。

*dcSrc*<br/>
源设备上下文。

*bClockWise*<br/>
TRUE 表示 + 90 度旋转;FALSE 表示旋转-90 度。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
