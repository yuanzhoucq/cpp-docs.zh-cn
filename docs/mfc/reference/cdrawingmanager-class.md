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
ms.openlocfilehash: 69365b66b12d5a9284c9b097b225ba041e07b6b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506810"
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
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|创建应用程序可以直接写入的32位独立于设备的位图 (DIB)。|
|[CDrawingManager::DrawAlpha](#drawalpha)|显示具有透明或半透明像素的位图。|
|[CDrawingManager::DrawRotated](#drawrotated)|将给定矩形内的源 DC 内容旋转 +/-90 度|
|[CDrawingManager::DrawEllipse](#drawellipse)|绘制具有所提供的填充和边框颜色的椭圆。|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|绘制一圈, 并用颜色渐变填充它。|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|绘制线条。|
|[CDrawingManager::DrawRect](#drawrect)|用提供的填充和边框颜色绘制矩形。|
|[CDrawingManager::DrawShadow](#drawshadow)|绘制矩形区域的阴影。|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|使用两个颜色渐变填充矩形区域。|
|[CDrawingManager::FillGradient](#fillgradient)|用指定的颜色渐变填充矩形区域。|
|[CDrawingManager::FillGradient2](#fillgradient2)|用指定的颜色渐变填充矩形区域。 还指定了渐变颜色更改的方向。|
|[CDrawingManager::GrayRect](#grayrect)|用指定的灰色填充矩形。|
|[CDrawingManager::HighlightRect](#highlightrect)|突出显示矩形区域。|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|将颜色从 HLS 表示形式转换为 RGB 表示形式。|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|将颜色从 HLS 表示形式转换为 RGB 表示形式。|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|将颜色从 HSV 表示形式转换为 RGB 表示形式。|
|[CDrawingManager::HuetoRGB](#huetorgb)|将色调值转换为红色、绿色或蓝色分量的帮助器方法。|
|[CDrawingManager::MirrorRect](#mirrorrect)|翻转矩形区域。|
|[CDrawingManager::PixelAlpha](#pixelalpha)|确定半透明像素的最终颜色的帮助器方法。|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|创建可用作阴影的位图。|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|将颜色从 RGB 表示形式转换为 HSL 表示形式。|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|将颜色从 RGB 表示形式转换为 HSV 表示形式。|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|在位图中为部分透明像素着色的帮助器方法。|
|[CDrawingManager::SetPixel](#setpixel)|将位图中的单个像素更改为指定颜色的帮助器方法。|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|基于加权比率合并两种颜色。|

## <a name="remarks"></a>备注

`CDrawingManager`类提供用于绘制阴影、颜色渐变和突出显示矩形的函数。 它还执行 alpha 混合。 可以使用此类直接更改应用程序的 UI。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>要求

**标头:** afxdrawmanager

##  <a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager

构造[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)对象。

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>参数

*dc*<br/>
中对设备上下文的引用。 `CDrawingManager`使用此上下文进行绘制。

##  <a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32

创建应用程序可以直接写入的32位独立于设备的位图 (DIB)。

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
|*size*|中一个指示位图大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)参数。|
|*pBits*|弄指向数据指针的指针, 该指针接收 DIB 的位值的位置。|
|*bitmap*|原始位图的句柄|
|*clrTransparent*|指定原始位图透明颜色的 RGB 值。|

### <a name="return-value"></a>返回值

如果此方法成功, 则为新创建的 DIB 位图的句柄;否则为 NULL。

### <a name="remarks"></a>备注

有关如何创建 DIB 位图的详细信息, 请参阅[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap)。

##  <a name="drawalpha"></a>CDrawingManager::D rawAlpha

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
中指向目标的设备上下文的指针。

*rectDst*<br/>
中目标矩形。

*pSrcDC*<br/>
中指向源的设备上下文的指针。

*rectSrc*<br/>
中源矩形。

### <a name="remarks"></a>备注

此方法执行两个位图的 alpha 混合。 有关 alpha 混合的详细信息, 请参阅 Windows SDK 中的[AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) 。

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

绘制具有所提供的填充和边框颜色的椭圆。

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>参数

*rect*<br/>
中椭圆的边框。

*clrFill*<br/>
中此方法用来填充椭圆的颜色。

*clrLine*<br/>
中此方法用作椭圆的边框的颜色。

### <a name="remarks"></a>备注

如果任意一种颜色设置为-1, 则此方法返回而不绘制椭圆。 如果边界矩形的任一维度为 0, 它也将返回, 而不绘制椭圆。

##  <a name="drawgradientring"></a>CDrawingManager::D rawGradientRing

绘制一圈, 并用颜色渐变填充它。

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
中指定渐变环边界的[CRect](../../atl-mfc-shared/reference/crect-class.md)参数。

*colorStart*<br/>
中渐变的第一种颜色。

*colorFinish*<br/>
中渐变的最后一种颜色。

*colorBorder*<br/>
中边框的颜色。

*nAngle*<br/>
中一个参数, 该参数指定初始渐变绘制角度。 此值应介于0到360之间。

*nWidth*<br/>
中圆圈的边框宽度。

*clrFace*<br/>
中环的内部的颜色。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

矩形定义的矩形的宽度必须至少为5个像素, 高度为5像素。

##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine, CDrawingManager::DrawLineA

绘制线条。

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
|*x1*|中行开始处的 x 坐标。|
|*y1*|中行开始处的 y 坐标。|
|*x2*|中行结束处的 x 坐标。|
|*y2*|中行结束处的 y 坐标。|
|*clrLine*|中线条的颜色。|

### <a name="remarks"></a>备注

如果*clrLine*等于-1, 则此方法将失败。

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

用提供的填充和边框颜色绘制矩形。

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>参数

*rect*<br/>
中矩形的边界。

*clrFill*<br/>
中此方法用来填充矩形的颜色。

*clrLine*<br/>
中此方法用于矩形边框的颜色。

### <a name="remarks"></a>备注

如果将任何颜色设置为-1, 则此方法返回而不绘制矩形。 如果矩形的任一维度为 0, 它也会返回。

##  <a name="drawshadow"></a>CDrawingManager::D rawShadow

绘制矩形区域的阴影。

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
中应用程序中的矩形区域。 绘图管理器将在此区域下绘制阴影。

*nDepth*<br/>
中阴影的宽度和高度。

*iMinBrightness*<br/>
中阴影的最小亮度。

*iMaxBrightness*<br/>
中阴影的最大亮度。

*pBmpSaveBottom*<br/>
中一个指针, 指向包含阴影下半部分的图像的位图。

*pBmpSaveRight*<br/>
中一个指针, 它指向一个位图, 该位图包含绘制在矩形右侧的阴影图像。

*clrBase*<br/>
中阴影的颜色。

*bRightShadow*<br/>
中指示如何绘制阴影的布尔型参数。 如果*bRightShadow*为`TRUE`, `DrawShadow`则在矩形右侧绘制阴影。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

可以使用参数*pBmpSaveBottom*和*pBmpSaveRight*为下阴影和右阴影提供两个有效的位图。 如果这些[CBitmap](../../mfc/reference/cbitmap-class.md)对象具有附加的 GDI 对象, `DrawShadow`则将使用这些位图作为阴影。 如果参数没有附加的 GDI 对象, `DrawShadow`则绘制阴影并将位图附加到参数。 `CBitmap` 在以后对的`DrawShadow`调用中, 您可以提供这些位图来加快绘制过程的速度。 有关`CBitmap`类和 GDI 对象的详细信息, 请参阅[图形对象](../../mfc/graphic-objects.md)。

如果其中一个参数为`NULL`, `DrawShadow`则将自动绘制阴影。

如果将*bRightShadow*设置为 FALSE, 则将在矩形区域的下方和左侧绘制阴影。

### <a name="example"></a>示例

下面的示例演示如何使用`DrawShadow` `CDrawingManager`类的方法。 此代码段是 "组件[表演示" 示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient

使用两个颜色渐变填充矩形区域。

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
中要填充的矩形。

*colorStart1*<br/>
中第一个颜色渐变的初始颜色。

*colorFinish1*<br/>
中第一个颜色渐变的最终颜色。

*colorStart2*<br/>
中第二个颜色渐变的初始颜色。

*colorFinish2*<br/>
中第二个颜色渐变的最终颜色。

*bHorz*<br/>
中布尔型参数, 指示`Fill4ColorsGradient`是水平渐变还是垂直渐变颜色。 TRUE 表示水平渐变。

*nPercentage*<br/>
中0-100 中的一个整数。 此值指示要用第一个颜色渐变填充的矩形的百分比。

### <a name="remarks"></a>备注

当用两种颜色渐变填充矩形时, 它们可能彼此位于彼此上方或相邻, 具体取决于*bHorz*的值。 每种颜色渐变都是独立于方法[CDrawingManager:: FillGradient](#fillgradient)来计算的。

如果*nPercentage*小于0或大于 100, 则此方法将生成断言失败。

##  <a name="fillgradient"></a>CDrawingManager::FillGradient

用指定的颜色渐变填充矩形区域。

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
中要填充的矩形区域。

*colorStart*<br/>
中渐变的第一种颜色。

*colorFinish*<br/>
中渐变的最终颜色。

*bHorz*<br/>
中一个布尔参数, 指定是否`FillGradient`应绘制水平或垂直渐变。

*nStartFlatPercentage*<br/>
中在开始渐变之前用`FillGradient` *colorStart*填充的矩形的百分比。

*nEndFlatPercentage*<br/>
中在完成渐变后用`FillGradient` *colorFinish*填充的矩形的百分比。

### <a name="example"></a>示例

下面的示例演示如何使用`FillGradient` `CDrawingManager`类的方法。 此代码片段是[MS Office 2007 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>CDrawingManager::FillGradient2

用指定的颜色渐变填充矩形区域。

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>参数

*rect*<br/>
中要填充的矩形区域。

*colorStart*<br/>
中渐变的第一种颜色。

*colorFinish*<br/>
中渐变的最后一种颜色。

*nAngle*<br/>
中介于0到360之间的整数。 此参数指定颜色渐变的方向。

### <a name="remarks"></a>备注

使用*nAngle*指定颜色渐变的方向。 指定颜色渐变的方向时, 还可以指定颜色渐变的起始位置。 如果*nAngle*的值为 0, 则表示渐变从矩形顶部开始。 随着*nAngle*的增加, 渐变的起始位置会根据角度以逆时针方向移动。

### <a name="example"></a>示例

下面的示例演示如何使用`FillGradient2` `CDrawingManager`类的方法。 此代码片段是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>CDrawingManager::GrayRect

用指定的灰色填充矩形。

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>参数

*rect*<br/>
中要填充的矩形区域。

*nPercentage*<br/>
中矩形中所需的灰色百分比。

*clrTransparent*<br/>
中透明颜色。

*clrDisabled*<br/>
中如果*nPercentage*设置为-1, 则此方法用于消除饱和度的颜色。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

对于参数*nPercentage*, 值越小表示颜色越暗。

*NPercentage*的最大值为200。 大于200的值不会更改矩形的外观。 如果值为-1, 则此方法使用*clrDisabled*来限制矩形的饱和度。

##  <a name="highlightrect"></a>CDrawingManager::HighlightRect

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

*rect*<br/>
中要突出显示的矩形区域。

*nPercentage*<br/>
中指示突出显示的透明度的百分比。

*clrTransparent*<br/>
中透明颜色。

*nTolerance*<br/>
中一个介于0到255之间的整数, 用于指示颜色容差。

*clrBlend*<br/>
中混合的基准颜色。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果*nPercentage*介于0到99之间, `HighlightRect`则使用 alpha 混合算法。 有关 alpha 混合的详细信息, 请参阅[Alpha 混合线条和填充](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)。 如果*nPercentage*为-1, 则此方法使用默认突出显示级别。 如果*nPercentage*为 100, 则此方法不执行任何操作并返回 TRUE。

方法使用参数*nTolerance*来确定是否突出显示矩形区域。 若要突出显示该矩形, 应用程序和*clrTransparent*的背景色之间的差异必须小于每个颜色组件中的*nTolerance* (红色、绿色和蓝色)。

##  <a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE

将颜色从 HLS 表示形式转换为 RGB 表示形式。

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>参数

*H*<br/>
中一个介于0和1之间的数字, 表示颜色的色调。

*L*<br/>
中一个介于0和1之间的数字, 表示颜色的发光度。

*S*<br/>
中一个介于0和1之间的数字, 表示颜色的饱和度。

### <a name="return-value"></a>返回值

提供的 HLS 颜色的 RGB 表示形式。

### <a name="remarks"></a>备注

颜色可以表示为 HSV (色相、饱和度和值)、HSL (色相、饱和度和亮度) 或 RGB (红色、绿色和蓝色)。 有关颜色不同表示形式的详细信息, 请参阅[颜色](/windows/win32/uxguide/vis-color)。

此方法和`CDrawingManager::HLStoRGB_TWO`方法执行相同的操作, 但需要为*H*参数提供不同的值。 在此方法中, *H*是圆圈的百分比。 在方法中, H 是0到360之间的度数值, 两者都表示红色。 `CDrawingManager::HLStoRGB_TWO` 例如, `HLStoRGB_ONE`对于, 对于*H* , 值为0.25 等效于`HLStoRGB_TWO`值 90, 值为。

##  <a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO

将颜色从 HLS 表示形式转换为 RGB 表示形式。

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>参数

*H*<br/>
中0到360之间的一个数字, 用于表示颜色的色调。

*L*<br/>
中一个介于0和1之间的数字, 表示颜色的发光度。

*S*<br/>
中一个介于0和1之间的数字, 表示颜色的饱和度。

### <a name="return-value"></a>返回值

提供的 HLS 颜色的 RGB 表示形式。

### <a name="remarks"></a>备注

颜色可以表示为 HSV (色相、饱和度和值)、HSL (色相、饱和度和亮度) 或 RGB (红色、绿色和蓝色)。 有关颜色不同表示形式的详细信息, 请参阅[颜色](/windows/win32/uxguide/vis-color)。

此方法和[CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one)方法执行相同的操作, 但需要为*H*参数提供不同的值。 在此方法中, *H*为介于0到360之间的度数值, 这两个值都表示红色。 在[CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one)方法中, *H*是圆圈的百分比。 例如, `HLStoRGB_ONE`对于, 对于*H* , 值为0.25 等效于`HLStoRGB_TWO`值 90, 值为。

##  <a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB

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
|参数|描述|
|*H*|中一个介于0到360之间的数字, 用于指示颜色的色调。|
|*S*|中一个介于0和1之间的数字, 表示颜色的饱和度。|
|*V*|中一个介于0和1之间的数字, 用于指示颜色的值。|

### <a name="return-value"></a>返回值

提供的 HSV 颜色的 RGB 表示形式。

### <a name="remarks"></a>备注

颜色可以表示为 HSV (色相、饱和度和值)、HSL (色相、饱和度和亮度) 或 RGB (红色、绿色和蓝色)。 有关颜色不同表示形式的详细信息, 请参阅[颜色](/windows/win32/uxguide/vis-color)。

##  <a name="huetorgb"></a>CDrawingManager::HuetoRGB

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
中请参阅 "备注"。

*m2*<br/>
中请参阅 "备注"。

*h*<br/>
中请参阅 "备注"。

*rm1*<br/>
中请参阅 "备注"。

*rm2*<br/>
中请参阅 "备注"。

*rh*<br/>
中请参阅 "备注"。

### <a name="return-value"></a>返回值

提供的色调的单个红色、绿色或蓝色分量。

### <a name="remarks"></a>备注

此方法是一种帮助器方法`CDrawingManager` , 该类使用它来计算 HSV 或 HSL 表示形式的颜色的单个红色、绿色和蓝色分量。 此方法不是由程序员直接调用的。 输入参数是依赖于转换算法的值。

若要将 HSV 或 HSL 颜色转换为 RGB 表示形式, 请调用以下方法之一:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>CDrawingManager::MirrorRect

翻转矩形区域。

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>参数

*rect*<br/>
中要翻转的区域的边框。

*bHorz*<br/>
中布尔型参数, 指示矩形是水平翻转还是垂直翻转。

### <a name="remarks"></a>备注

此方法可以反转此`CDrawingManager`类拥有的任何设备上下文区域。 如果*bHorz*设置为 TRUE, 则此方法水平翻转区域。 否则, 它会垂直翻转区域。

##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha

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
中像素的初始颜色。

*percent*<br/>
中介于0到100之间的一个数字, 表示透明度的百分比。 值100指示初始颜色完全透明。

*percentR*<br/>
中一个介于0和100之间的数字, 表示红色组件的透明度百分比。

*percentG*<br/>
中一个介于0和100之间的数字, 表示绿色组件的透明度百分比。

*percentB*<br/>
中一个介于0和100之间的数字, 表示蓝色分量的透明度百分比。

*dstPixel*<br/>
中像素的基准颜色。

### <a name="return-value"></a>返回值

半透明像素的最终颜色。

### <a name="remarks"></a>备注

这是一个帮助器类, 用于着色半透明位图, 而不是由程序员直接调用。

使用具有*dstPixel*的方法版本时, 最终颜色是*dstPixel*和*srcPixel*的组合。 *SrcPixel*颜色是*dstPixel*基本颜色上的部分透明颜色。

##  <a name="prepareshadowmask"></a>CDrawingManager::P repareShadowMask

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
中阴影的宽度和高度。

*clrBase*<br/>
中阴影的颜色。

*iMinBrightness*<br/>
中阴影的最小亮度。

*iMaxBrightness*<br/>
中阴影的最大亮度。

### <a name="return-value"></a>返回值

如果此方法成功, 则为所创建的位图的句柄;否则为 NULL。

### <a name="remarks"></a>备注

如果将*nDepth*设置为 0, 则此方法将退出并返回 NULL。 如果*nDepth*小于 3, 则阴影的宽度和高度将设置为3个像素。

##  <a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL

将颜色从红色、绿色和蓝色 (RGB) 表示形式转换为 "色调"、"饱和度" 和 "亮度" (HSL) 表示形式。

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
|*rgb*|中RGB 值中的颜色。|
|*H*|弄一个指针, 指向一种双精度型, 其中方法存储颜色的色调。|
|*S*|弄一个指针, 指向一种双精度型, 其中方法存储颜色的饱和度。|
|*L*|弄一个指针, 指向一种双精度型, 其中方法存储颜色的亮度。|

### <a name="remarks"></a>备注

颜色可以表示为 HSV (色相、饱和度和值)、HSL (色相、饱和度和亮度) 或 RGB (红色、绿色和蓝色)。 有关颜色不同表示形式的详细信息, 请参阅[颜色](/windows/win32/uxguide/vis-color)。

*H*返回的值表示为0和1之间的一个小部分, 其中0和1表示红色。 为*S*和*L*返回的值为介于0到1之间的数字。

##  <a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV

将颜色从 RGB 表示形式转换为 HSV 表示形式。

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>参数

*rgb*<br/>
中要在 RGB 表示形式中转换的颜色。

*H*<br/>
弄一个指向 double 的指针, 此方法用于存储颜色的结果色调。

*S*<br/>
弄一个指针, 指向一种双精度型, 其中此方法用于存储颜色的生成饱和度。

*V*<br/>
弄指向双精度值的指针, 此方法存储颜色的结果值。

### <a name="remarks"></a>备注

颜色可以表示为 HSV (色相、饱和度和值)、HSL (色相、饱和度和亮度) 或 RGB (红色、绿色和蓝色)。 有关颜色不同表示形式的详细信息, 请参阅[颜色](/windows/win32/uxguide/vis-color)。

*H*的返回值是0到360之间的一个数字, 其中0和360表示红色。 *S*和*V*的返回值为介于0到1之间的数字。

##  <a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel

在位图中为透明像素着色。

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
中指向位图位值的指针。

*rect*<br/>
中应用程序中的矩形区域。 绘图管理器将在此区域的下方和右侧绘制阴影。

*x*<br/>
中像素到颜色的水平坐标。

*y*<br/>
中像素到颜色的垂直坐标。

*percent*<br/>
中透明度百分比。

*iShadowSize*<br/>
中阴影的宽度和高度。

*clrBase*<br/>
中阴影的颜色。

*bIsRight*<br/>
中布尔参数, 用于指示要着色的像素。 有关详细信息，请参阅备注部分。

### <a name="remarks"></a>备注

此方法是[CDrawingManager::D rawshadow](#drawshadow)方法使用的帮助器方法。 如果要绘制阴影, 则建议改为调用`CDrawingManager::DrawShadow` 。

如果将*bIsRight*设置为 TRUE, 则从*矩形*的右边缘开始度量的像素为*x*像素。 如果该参数为 FALSE, 则将像素设置为从*矩形*左边缘开始算起的*x*像素。

##  <a name="setpixel"></a>CDrawingManager::SetPixel

将位图中的单个像素改为指定的颜色。

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
|*pBits*|中指向位图位值的指针。|
|*cx*|中位图的总宽度。|
|*cy*|中位图的总高度。|
|*x*|中要更改的位图中像素的 x 坐标。|
|*y*|中要更改的位图中像素的 y 坐标。|
|*color*|中由提供的坐标标识的像素的新颜色。|

##  <a name="smartmixcolors"></a>CDrawingManager::SmartMixColors

基于加权比率合并两种颜色。

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
|*color1*|中要混合的第一种颜色。|
|*color2*|中要混合的第二种颜色。|
|*dblLumRatio*|中新颜色发光度的比率。 `SmartMixColors`在确定最终颜色之前, 将混合颜色的发光度与此比率相乘。|
|*k1*|中第一种颜色的加权比例。|
|*k2*|中第二种颜色的加权比例。|

### <a name="return-value"></a>返回值

一种颜色, 表示所提供的颜色的加权组合。

### <a name="remarks"></a>备注

如果*版 k1*或*k2*小于零, 则此方法将失败并出现错误。 如果这两个参数均设置为 0, 则该方法`RGB(0, 0, 0)`返回。

加权比率的计算公式为: (color1 \*版 k1 + color2 \* k2)/(版 k1 + k2)。 确定了加权比率后, 方法将计算混合颜色的发光度。 然后, 它通过*dblLumRatio*将发光度相乘。 如果该值大于 1.0, 则方法将混合颜色的发光度设置为新值。 否则, 发光度设置为1.0。

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

将给定矩形内的源 DC 内容旋转90度。

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
TRUE 指示旋转 + 90 度;FALSE 指示旋转-90 度。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
