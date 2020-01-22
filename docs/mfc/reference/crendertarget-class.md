---
title: CRenderTarget 类
ms.date: 03/27/2019
f1_keywords:
- CRenderTarget
- AFXRENDERTARGET/CRenderTarget
- AFXRENDERTARGET/CRenderTarget::CRenderTarget
- AFXRENDERTARGET/CRenderTarget::Attach
- AFXRENDERTARGET/CRenderTarget::BeginDraw
- AFXRENDERTARGET/CRenderTarget::Clear
- AFXRENDERTARGET/CRenderTarget::COLORREF_TO_D2DCOLOR
- AFXRENDERTARGET/CRenderTarget::CreateCompatibleRenderTarget
- AFXRENDERTARGET/CRenderTarget::Destroy
- AFXRENDERTARGET/CRenderTarget::Detach
- AFXRENDERTARGET/CRenderTarget::DrawBitmap
- AFXRENDERTARGET/CRenderTarget::DrawEllipse
- AFXRENDERTARGET/CRenderTarget::DrawGeometry
- AFXRENDERTARGET/CRenderTarget::DrawGlyphRun
- AFXRENDERTARGET/CRenderTarget::DrawLine
- AFXRENDERTARGET/CRenderTarget::DrawRectangle
- AFXRENDERTARGET/CRenderTarget::DrawRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::DrawText
- AFXRENDERTARGET/CRenderTarget::DrawTextLayout
- AFXRENDERTARGET/CRenderTarget::EndDraw
- AFXRENDERTARGET/CRenderTarget::FillEllipse
- AFXRENDERTARGET/CRenderTarget::FillGeometry
- AFXRENDERTARGET/CRenderTarget::FillMesh
- AFXRENDERTARGET/CRenderTarget::FillOpacityMask
- AFXRENDERTARGET/CRenderTarget::FillRectangle
- AFXRENDERTARGET/CRenderTarget::FillRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::Flush
- AFXRENDERTARGET/CRenderTarget::GetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetDpi
- AFXRENDERTARGET/CRenderTarget::GetMaximumBitmapSize
- AFXRENDERTARGET/CRenderTarget::GetPixelFormat
- AFXRENDERTARGET/CRenderTarget::GetPixelSize
- AFXRENDERTARGET/CRenderTarget::GetRenderTarget
- AFXRENDERTARGET/CRenderTarget::GetSize
- AFXRENDERTARGET/CRenderTarget::GetTags
- AFXRENDERTARGET/CRenderTarget::GetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::GetTransform
- AFXRENDERTARGET/CRenderTarget::IsSupported
- AFXRENDERTARGET/CRenderTarget::IsValid
- AFXRENDERTARGET/CRenderTarget::PopAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PopLayer
- AFXRENDERTARGET/CRenderTarget::PushAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PushLayer
- AFXRENDERTARGET/CRenderTarget::RestoreDrawingState
- AFXRENDERTARGET/CRenderTarget::SaveDrawingState
- AFXRENDERTARGET/CRenderTarget::SetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetDpi
- AFXRENDERTARGET/CRenderTarget::SetTags
- AFXRENDERTARGET/CRenderTarget::SetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::SetTransform
- AFXRENDERTARGET/CRenderTarget::VerifyResource
- AFXRENDERTARGET/CRenderTarget::m_lstResources
- AFXRENDERTARGET/CRenderTarget::m_pRenderTarget
- AFXRENDERTARGET/CRenderTarget::m_pTextFormatDefault
helpviewer_keywords:
- CRenderTarget [MFC], CRenderTarget
- CRenderTarget [MFC], Attach
- CRenderTarget [MFC], BeginDraw
- CRenderTarget [MFC], Clear
- CRenderTarget [MFC], COLORREF_TO_D2DCOLOR
- CRenderTarget [MFC], CreateCompatibleRenderTarget
- CRenderTarget [MFC], Destroy
- CRenderTarget [MFC], Detach
- CRenderTarget [MFC], DrawBitmap
- CRenderTarget [MFC], DrawEllipse
- CRenderTarget [MFC], DrawGeometry
- CRenderTarget [MFC], DrawGlyphRun
- CRenderTarget [MFC], DrawLine
- CRenderTarget [MFC], DrawRectangle
- CRenderTarget [MFC], DrawRoundedRectangle
- CRenderTarget [MFC], DrawText
- CRenderTarget [MFC], DrawTextLayout
- CRenderTarget [MFC], EndDraw
- CRenderTarget [MFC], FillEllipse
- CRenderTarget [MFC], FillGeometry
- CRenderTarget [MFC], FillMesh
- CRenderTarget [MFC], FillOpacityMask
- CRenderTarget [MFC], FillRectangle
- CRenderTarget [MFC], FillRoundedRectangle
- CRenderTarget [MFC], Flush
- CRenderTarget [MFC], GetAntialiasMode
- CRenderTarget [MFC], GetDpi
- CRenderTarget [MFC], GetMaximumBitmapSize
- CRenderTarget [MFC], GetPixelFormat
- CRenderTarget [MFC], GetPixelSize
- CRenderTarget [MFC], GetRenderTarget
- CRenderTarget [MFC], GetSize
- CRenderTarget [MFC], GetTags
- CRenderTarget [MFC], GetTextAntialiasMode
- CRenderTarget [MFC], GetTextRenderingParams
- CRenderTarget [MFC], GetTransform
- CRenderTarget [MFC], IsSupported
- CRenderTarget [MFC], IsValid
- CRenderTarget [MFC], PopAxisAlignedClip
- CRenderTarget [MFC], PopLayer
- CRenderTarget [MFC], PushAxisAlignedClip
- CRenderTarget [MFC], PushLayer
- CRenderTarget [MFC], RestoreDrawingState
- CRenderTarget [MFC], SaveDrawingState
- CRenderTarget [MFC], SetAntialiasMode
- CRenderTarget [MFC], SetDpi
- CRenderTarget [MFC], SetTags
- CRenderTarget [MFC], SetTextAntialiasMode
- CRenderTarget [MFC], SetTextRenderingParams
- CRenderTarget [MFC], SetTransform
- CRenderTarget [MFC], VerifyResource
- CRenderTarget [MFC], m_lstResources
- CRenderTarget [MFC], m_pRenderTarget
- CRenderTarget [MFC], m_pTextFormatDefault
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
ms.openlocfilehash: 08d01132927ca0a5f452703b14d0eb5fae2f58ba
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518440"
---
# <a name="crendertarget-class"></a>CRenderTarget 类

ID2D1RenderTarget 的包装器。

## <a name="syntax"></a>语法

```
class CRenderTarget : public CObject;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CRenderTarget::CRenderTarget](#crendertarget)|构造 CRenderTarget 对象。|
|[CRenderTarget::~CRenderTarget](#_dtorcrendertarget)|析构函数。 在呈现器目标对象被销毁时调用。|

### <a name="public-methods"></a>公共方法

|Name|描述|
|----------|-----------------|
|[CRenderTarget::Attach](#attach)|将现有呈现器目标接口附加到对象|
|[CRenderTarget::BeginDraw](#begindraw)|启动此呈现器目标上的绘图。|
|[CRenderTarget::Clear](#clear)|清除指定颜色的绘图区域。|
|[CRenderTarget::COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|将 GDI 颜色和 alpha 值转换为 D2D1_COLOR_F 的对象。|
|[CRenderTarget::CreateCompatibleRenderTarget](#createcompatiblerendertarget)|创建一个新的位图呈现器目标，以便在与当前呈现器目标兼容的中间屏幕外绘制期间使用。|
|[CRenderTarget::Destroy](#destroy)|删除一个或多个资源|
|[CRenderTarget::Detach](#detach)|从对象分离呈现目标接口|
|[CRenderTarget::DrawBitmap](#drawbitmap)|绘制由指定的 IDWriteTextLayout 对象描述的格式化文本。|
|[CRenderTarget::DrawEllipse](#drawellipse)|使用指定的笔划样式绘制指定椭圆的轮廓。|
|[CRenderTarget::DrawGeometry](#drawgeometry)|使用指定的笔划样式绘制指定几何图形的轮廓。|
|[CRenderTarget::DrawGlyphRun](#drawglyphrun)|绘制指定的字形。|
|[CRenderTarget::DrawLine](#drawline)|使用指定的笔划样式在指定点之间绘制一条线。|
|[CRenderTarget::DrawRectangle](#drawrectangle)|绘制具有指定尺寸和描边样式的矩形的轮廓。|
|[CRenderTarget::DrawRoundedRectangle](#drawroundedrectangle)|使用指定的笔划样式绘制指定圆角矩形的轮廓。|
|[CRenderTarget::DrawText](#drawtext)|使用 IDWriteTextFormat 对象提供的格式信息绘制指定的文本。|
|[CRenderTarget::DrawTextLayout](#drawtextlayout)|绘制由指定的 IDWriteTextLayout 对象描述的格式化文本。|
|[CRenderTarget::EndDraw](#enddraw)|结束呈现器目标上的绘图操作并指示当前错误状态和关联的标记。|
|[CRenderTarget::FillEllipse](#fillellipse)|绘制指定椭圆的内部。|
|[CRenderTarget::FillGeometry](#fillgeometry)|绘制指定几何图形的内部。|
|[CRenderTarget::FillMesh](#fillmesh)|绘制指定网格的内部。|
|[CRenderTarget::FillOpacityMask](#fillopacitymask)|将指定位图描述的不透明蒙板应用于画笔，并使用该画笔绘制呈现器目标的区域。|
|[CRenderTarget::FillRectangle](#fillrectangle)|绘制指定矩形的内部。|
|[CRenderTarget::FillRoundedRectangle](#fillroundedrectangle)|绘制指定圆角矩形的内部。|
|[CRenderTarget::Flush](#flush)|执行所有挂起的绘图命令。|
|[CRenderTarget::GetAntialiasMode](#getantialiasmode)|检索非文本绘图操作的当前抗锯齿模式。|
|[CRenderTarget::GetDpi](#getdpi)|返回呈现器目标的每英寸点数（DPI）|
|[CRenderTarget::GetMaximumBitmapSize](#getmaximumbitmapsize)|获取呈现器目标支持的任何一个位图维度的最大大小（以设备相关单位（像素）为单位）|
|[CRenderTarget::GetPixelFormat](#getpixelformat)|检索呈现器目标的像素格式和 alpha 模式|
|[CRenderTarget::GetPixelSize](#getpixelsize)|返回呈现器目标的大小（以设备像素为单位）|
|[CRenderTarget::GetRenderTarget](#getrendertarget)|返回 ID2D1RenderTarget 接口|
|[CRenderTarget::GetSize](#getsize)|返回呈现器目标的大小，以与设备无关的像素为单位|
|[CRenderTarget::GetTags](#gettags)|获取用于后续绘图操作的标签。|
|[CRenderTarget::GetTextAntialiasMode](#gettextantialiasmode)|获取文本和字形绘制操作的当前抗锯齿模式。|
|[CRenderTarget::GetTextRenderingParams](#gettextrenderingparams)|检索呈现器目标的当前文本呈现选项。|
|[CRenderTarget::GetTransform](#gettransform)|将指定的转换应用于呈现器目标，并替换现有转换。 所有后续绘图操作都在转换后的空间中发生。|
|[CRenderTarget::IsSupported](#issupported)|指示呈现器目标是否支持指定的属性|
|[CRenderTarget::IsValid](#isvalid)|检查资源有效性|
|[CRenderTarget::PopAxisAlignedClip](#popaxisalignedclip)|从呈现器目标中移除最后一个轴对齐的剪辑。 调用此方法后，剪辑将不再应用于后续的绘图操作。|
|[CRenderTarget::PopLayer](#poplayer)|停止将绘图操作重定向到由上一个 PushLayer 调用指定的层。|
|[CRenderTarget::PushAxisAlignedClip](#pushaxisalignedclip)|从呈现器目标中移除最后一个轴对齐的剪辑。 调用此方法后，剪辑将不再应用于后续的绘图操作。|
|[CRenderTarget::PushLayer](#pushlayer)|将指定层添加到呈现器目标，以便在调用 PopLayer 之前接收所有后续绘图操作。|
|[CRenderTarget::RestoreDrawingState](#restoredrawingstate)|将呈现器目标的绘图状态设置为指定的 ID2D1DrawingStateBlock 的状态。|
|[CRenderTarget::SaveDrawingState](#savedrawingstate)|将当前绘图状态保存到指定的 ID2D1DrawingStateBlock。|
|[CRenderTarget::SetAntialiasMode](#setantialiasmode)|设置呈现器目标的抗锯齿模式。 消除锯齿模式适用于所有后续绘图操作，不包括文本和字形绘制操作。|
|[CRenderTarget::SetDpi](#setdpi)|设置呈现器目标的每英寸点数（DPI）。|
|[CRenderTarget::SetTags](#settags)|为后续绘图操作指定标签。|
|[CRenderTarget::SetTextAntialiasMode](#settextantialiasmode)|指定用于后续文本和字形绘制操作的抗锯齿模式。|
|[CRenderTarget::SetTextRenderingParams](#settextrenderingparams)|指定要应用于所有后续文本和字形绘制操作的文本呈现选项。|
|[CRenderTarget::SetTransform](#settransform)|已重载。 将指定的转换应用于呈现器目标，并替换现有转换。 所有后续绘图操作都在转换后的空间中发生。|

### <a name="protected-methods"></a>受保護的方法

|Name|描述|
|----------|-----------------|
|[CRenderTarget::VerifyResource](#verifyresource)|验证 CD2DResource 对象有效性;如果该对象尚不存在，则创建它。|

### <a name="public-operators"></a>公用運算子

|Name|描述|
|----------|-----------------|
|[CRenderTarget：： operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|返回 ID2D1RenderTarget 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|Name|描述|
|----------|-----------------|
|[CRenderTarget::m_lstResources](#m_lstresources)|指向 CD2DResource 对象的指针的列表。|
|[CRenderTarget::m_pRenderTarget](#m_prendertarget)|指向 ID2D1RenderTarget 对象的指针。|
|[CRenderTarget::m_pTextFormatDefault](#m_ptextformatdefault)|指向 CD2DTextFormat 对象的指针，该对象包含默认文本格式。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

## <a name="requirements"></a>需求

**标头：** afxrendertarget

##  <a name="_dtorcrendertarget"></a>CRenderTarget：： ~ CRenderTarget

析构函数。 在呈现器目标对象被销毁时调用。

```
virtual ~CRenderTarget();
```

##  <a name="attach"></a>CRenderTarget：： Attach

将现有呈现器目标接口附加到对象

```
void Attach(ID2D1RenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRenderTarget*<br/>
现有的呈现器目标接口。 不能为 NULL

##  <a name="begindraw"></a>  CRenderTarget::BeginDraw

启动此呈现器目标上的绘图。

```
void BeginDraw();
```

##  <a name="clear"></a>  CRenderTarget::Clear

清除指定颜色的绘图区域。

```
void Clear(D2D1_COLOR_F color);
```

### <a name="parameters"></a>参数

*color*<br/>
向其中清除绘图区域的颜色。

##  <a name="colorref_to_d2dcolor"></a>CRenderTarget：： COLORREF_TO_D2DCOLOR

将 GDI 颜色和 alpha 值转换为 D2D1_COLOR_F 的对象。

```
static D2D1_COLOR_F COLORREF_TO_D2DCOLOR(
    COLORREF color,
    int nAlpha = 255);
```

### <a name="parameters"></a>参数

*color*<br/>
RGB 值。

*nAlpha*

### <a name="return-value"></a>返回值

D2D1_COLOR_F 值。

##  <a name="createcompatiblerendertarget"></a>  CRenderTarget::CreateCompatibleRenderTarget

创建一个新的位图呈现器目标，以便在与当前呈现器目标兼容的中间屏幕外绘制期间使用。

```
BOOL CreateCompatibleRenderTarget(
    CBitmapRenderTarget& bitmapTarget,
    CD2DSizeF sizeDesired = CD2DSizeF(0., 0.),
    CD2DSizeU sizePixelDesired = CD2DSizeU(0, 0),
    D2D1_PIXEL_FORMAT* desiredFormat = NULL,
    D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS options = D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS_NONE);
```

### <a name="parameters"></a>参数

*bitmapTarget*<br/>
此方法返回时，包含指向新位图呈现器目标的指针的地址。 此参数未经初始化即被传递。

*sizeDesired*<br/>
如果新呈现器目标的大小应与原始呈现器目标不同，则为其所需的大小; 如果不是，则为 NULL。 有关详细信息，请参阅“备注”部分。

*sizePixelDesired*<br/>
如果新呈现器目标的大小应与原始呈现器目标不同，则为所需的大小; 如果为 NULL，则为 NULL。 有关详细信息，请参阅“备注”部分。

*desiredFormat*<br/>
新呈现器目标的所需像素格式和 alpha 模式，或为 NULL。 如果像素格式设置为 DXGI_FORMAT_UNKNOWN 或此参数为 null，则新的呈现器目标将使用与原始呈现器目标相同的像素格式。 如果 alpha 模式为 D2D1_ALPHA_MODE_UNKNOWN 或此参数为 NULL，则新呈现器目标的 alpha 模式默认为 D2D1_ALPHA_MODE_PREMULTIPLIED。 有关支持的像素格式的信息，请参阅支持的像素格式和 Alpha 模式。

*options*<br/>
一个值，该值指定新的呈现器目标是否必须与 GDI 兼容。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，返回 FALSE。

##  <a name="crendertarget"></a>CRenderTarget：： CRenderTarget

构造 CRenderTarget 对象。

```
CRenderTarget();
```

##  <a name="destroy"></a>  CRenderTarget::Destroy

删除一个或多个资源

```
BOOL Destroy(BOOL bDeleteResources = TRUE);
```

### <a name="parameters"></a>参数

*bDeleteResources*<br/>
如果 bDeleteResources 为 TRUE，则将自动销毁位于 m_lstResources 中的所有资源。

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，返回 FALSE

##  <a name="detach"></a>  CRenderTarget::Detach

从对象分离呈现目标接口

```
ID2D1RenderTarget* Detach ();
```

### <a name="return-value"></a>返回值

指向分离的呈现器目标接口的指针。

##  <a name="drawbitmap"></a>  CRenderTarget::DrawBitmap

绘制由指定的 IDWriteTextLayout 对象描述的格式化文本。

```
void DrawBitmap(
    CD2DBitmap* pBitmap,
    const CD2DRectF& rectDest,
    float fOpacity = 1.0,
    D2D1_BITMAP_INTERPOLATION_MODE interpolationMode = D2D1_BITMAP_INTERPOLATION_MODE_LINEAR,
    const CD2DRectF* pRectSrc = NULL);
```

### <a name="parameters"></a>参数

*pBitmap*<br/>
要呈现的位图。

*rectDest*<br/>
绘制位图的区域的大小和位置（以与设备无关的像素为单位）。 如果该矩形的顺序不正确，则不绘制任何内容，但呈现目标不会进入错误状态。

*fOpacity*<br/>
一个介于 0.0 f 和 1.0 f （含）之间的值，该值指定要应用于位图的不透明度值;此值与位图内容的 alpha 值相乘。

*interpolationMode*<br/>
如果由绘图操作缩放或旋转位图，则使用内插模式。

*pRectSrc*<br/>
位图中要绘制的区域的大小和位置（以与设备无关的像素为单位）。

##  <a name="drawellipse"></a>  CRenderTarget::DrawEllipse

使用指定的笔划样式绘制指定椭圆的轮廓。

```
void DrawEllipse(
    const CD2DEllipse& ellipse,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>参数

*ellipse*<br/>
要绘制的椭圆的位置和半径，以与设备无关的像素为单位。

*pBrush*<br/>
用于绘制椭圆轮廓的画笔。

*fStrokeWidth*<br/>
椭圆笔画的粗细。 笔划在椭圆的轮廓上居中。

*strokeStyle*<br/>
要应用于椭圆轮廓的笔划样式，或为 NULL 以绘制实心笔画。

##  <a name="drawgeometry"></a>  CRenderTarget::DrawGeometry

使用指定的笔划样式绘制指定几何图形的轮廓。

```
void DrawGeometry(
    CD2DGeometry* pGeometry,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>参数

*pGeometry*<br/>
要绘制的几何图形。

*pBrush*<br/>
用于绘制几何图形笔划的画笔。

*fStrokeWidth*<br/>
几何图形笔划的粗细。 笔划在几何图形的轮廓上居中。

*strokeStyle*<br/>
要应用于几何图形轮廓的笔划样式; 如果为 NULL，则绘制实心笔画。

##  <a name="drawglyphrun"></a>  CRenderTarget::DrawGlyphRun

绘制指定的字形。

```
void DrawGlyphRun(
    const CD2DPointF& ptBaseLineOrigin,
    const DWRITE_GLYPH_RUN& glyphRun,
    CD2DBrush* pForegroundBrush,
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```

### <a name="parameters"></a>参数

*ptBaseLineOrigin*<br/>
标志符号基线的原点（以与设备无关的像素为单位）。

*glyphRun*<br/>
要呈现的标志符号。

*pForegroundBrush*<br/>
用于绘制指定标志符号的画笔。

*measuringMode*<br/>
一个值，该值指示在设置格式时如何使用字形度量来度量文本。 默认值为 DWRITE_MEASURING_MODE_NATURAL。

##  <a name="drawline"></a>  CRenderTarget::DrawLine

使用指定的笔划样式在指定点之间绘制一条线。

```
void DrawLine(
    const CD2DPointF& ptFrom,
    const CD2DPointF& ptTo,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>参数

*ptFrom*<br/>
线条的起点，以与设备无关的像素为单位。

*ptTo*<br/>
线条的终点，以与设备无关的像素为单位。

*pBrush*<br/>
用于绘制线条笔画的画笔。

*fStrokeWidth*<br/>
一个大于或等于 0.0 f 的值，该值指定笔划的宽度。 如果未指定此参数，则默认为 1.0 f。 笔划在线条上居中。

*strokeStyle*<br/>
要绘制的笔划样式，或为 NULL 以绘制实线。

##  <a name="drawrectangle"></a>  CRenderTarget::DrawRectangle

绘制具有指定尺寸和描边样式的矩形的轮廓。

```
void DrawRectangle(
    const CD2DRectF& rectangle,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>参数

*rectangle*<br/>
要绘制的矩形的尺寸（以与设备无关的像素为单位）

*pBrush*<br/>
用于绘制矩形笔画的画笔

*fStrokeWidth*<br/>
一个大于或等于 0.0 f 的值，该值指定矩形笔画的宽度。 笔划在矩形的轮廓上居中。

*strokeStyle*<br/>
要绘制的笔划的样式，或为 NULL 以绘制实心笔画。

##  <a name="drawroundedrectangle"></a>  CRenderTarget::DrawRoundedRectangle

使用指定的笔划样式绘制指定圆角矩形的轮廓。

```
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>参数

*rectRounded*<br/>
要绘制的圆角矩形的尺寸，以与设备无关的像素为单位。

*pBrush*<br/>
用于绘制圆角矩形边框的画笔。

*fStrokeWidth*<br/>
圆角矩形笔画的宽度。 笔划在圆角矩形的轮廓上居中。 默认值为 1.0 f。

*strokeStyle*<br/>
圆角矩形笔画的样式; 如果为 NULL，则绘制实心笔画。 默认值为 NULL。

##  <a name="drawtext"></a>  CRenderTarget::DrawText

使用 IDWriteTextFormat 对象提供的格式信息绘制指定的文本。

```
void DrawText(
    const CString& strText,
    const CD2DRectF& rectangle,
    CD2DBrush* pForegroundBrush,
    CD2DTextFormat* textFormat = NULL,
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE,
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```

### <a name="parameters"></a>参数

*strText*<br/>
指向要绘制的 Unicode 字符数组的指针。

*rectangle*<br/>
在其中绘制文本的区域的大小和位置。

*pForegroundBrush*<br/>
用于绘制文本的画笔。

*textFormat*<br/>
一个对象，该对象描述要绘制的文本的格式设置详细信息，如字体、字号和流方向。

*options*<br/>
一个值，该值指示文本是否应与像素边界对齐，以及文本是否应剪裁到布局矩形。 默认值为 "D2D1_DRAW_TEXT_OPTIONS_NONE"，指示应将文本对齐到像素边界，而不应将其剪裁到布局矩形。

*measuringMode*<br/>
一个值，该值指示在设置格式时如何使用字形度量来度量文本。 默认值为 DWRITE_MEASURING_MODE_NATURAL。

##  <a name="drawtextlayout"></a>  CRenderTarget::DrawTextLayout

绘制由指定的 IDWriteTextLayout 对象描述的格式化文本。

```
void DrawTextLayout(
    const CD2DPointF& ptOrigin,
    CD2DTextLayout* textLayout,
    CD2DBrush* pBrushForeground,
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```

### <a name="parameters"></a>参数

*ptOrigin*<br/>
绘制 textLayout 描述的文本的左上角的点，以与设备无关的像素为单位。

*textLayout*<br/>
要绘制的格式化文本。 不从 ID2D1Resource 继承的任何绘制效果都将被忽略。 如果存在从非画笔的 ID2D1Resource 继承的绘制效果，此方法将失败，并且呈现目标将处于错误状态。

*pBrushForeground*<br/>
用于绘制 textLayout 中的任何文本的画笔，这些文本还没有与绘图效果关联的画笔（由 IDWriteTextLayout：： SetDrawingEffect 方法指定）。

*options*<br/>
一个值，该值指示文本是否应与像素边界对齐，以及文本是否应剪裁到布局矩形。 默认值为 "D2D1_DRAW_TEXT_OPTIONS_NONE"，指示应将文本对齐到像素边界，而不应将其剪裁到布局矩形。

##  <a name="enddraw"></a>CRenderTarget：： EndDraw

结束呈现器目标上的绘图操作并指示当前错误状态和关联的标记。

```
HRESULT EndDraw();
```

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回 HRESULT 错误代码。

##  <a name="fillellipse"></a>  CRenderTarget::FillEllipse

绘制指定椭圆的内部。

```
void FillEllipse(
    const CD2DEllipse& ellipse,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>参数

*ellipse*<br/>
要绘制的椭圆的位置和半径，以与设备无关的像素为单位。

*pBrush*<br/>
用于绘制椭圆内部的画笔。

##  <a name="fillgeometry"></a>CRenderTarget：： FillGeometry

绘制指定几何图形的内部。

```
void FillGeometry(
    CD2DGeometry* pGeometry,
    CD2DBrush* pBrush,
    CD2DBrush* pOpacityBrush = NULL);
```

### <a name="parameters"></a>参数

*pGeometry*<br/>
要绘制的几何图形。

*pBrush*<br/>
用于绘制几何图形内部的画笔。

*pOpacityBrush*<br/>
要应用于几何图形的不透明蒙板;如果没有不透明蒙板，则为 NULL。 如果指定了不透明蒙板（opacityBrush 参数），则画笔必须是其 x 和 y 扩展模式设置为 D2D1_EXTEND_MODE_CLAMP 的 ID2D1BitmapBrush。 有关详细信息，请参阅“备注”部分。

##  <a name="fillmesh"></a>  CRenderTarget::FillMesh

绘制指定网格的内部。

```
void FillMesh(
    CD2DMesh* pMesh,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>参数

*pMesh*<br/>
要绘制的网格。

*pBrush*<br/>
用于绘制网格的画笔。

##  <a name="fillopacitymask"></a>  CRenderTarget::FillOpacityMask

将指定位图描述的不透明蒙板应用于画笔，并使用该画笔绘制呈现器目标的区域。

```
void FillOpacityMask(
    CD2DBitmap* pOpacityMask,
    CD2DBrush* pBrush,
    D2D1_OPACITY_MASK_CONTENT content,
    const CD2DRectF& rectDest,
    const CD2DRectF& rectSrc);
```

### <a name="parameters"></a>参数

*pOpacityMask*<br/>
要绘制的椭圆的位置和半径，以与设备无关的像素为单位。

*pBrush*<br/>
用于绘制由 destinationRectangle 指定的呈现器目标区域的画笔。

*content*<br/>
不透明蒙板包含的内容的类型。 该值用于确定不透明蒙板混合的颜色空间。

*rectDest*<br/>
要绘制的呈现器目标的区域，以与设备无关的像素为单位。

*rectSrc*<br/>
要用作不透明蒙板的位图区域，以与设备无关的像素为单位。

##  <a name="fillrectangle"></a>  CRenderTarget::FillRectangle

绘制指定矩形的内部。

```
void FillRectangle(
    const CD2DRectF& rectangle,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>参数

*rectangle*<br/>
要绘制的矩形的维度，以与设备无关的像素为单位。

*pBrush*<br/>
用于绘制矩形的内部的画笔。

##  <a name="fillroundedrectangle"></a>  CRenderTarget::FillRoundedRectangle

绘制指定圆角矩形的内部。

```
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>参数

*rectRounded*<br/>
要绘制的圆角矩形的尺寸，以与设备无关的像素为单位。

*pBrush*<br/>
用于绘制圆角矩形内部的画笔。

##  <a name="flush"></a>  CRenderTarget::Flush

执行所有挂起的绘图命令。

```
void Flush(
    D2D1_TAG* tag1 = NULL,
    D2D1_TAG* tag2 = NULL);
```

### <a name="parameters"></a>参数

*tag1*<br/>
包含导致错误的绘制操作的标记，如果没有错误，则为0。 此参数未经初始化即被传递。

*tag2*<br/>
包含导致错误的绘制操作的标记，如果没有错误，则为0。 此参数未经初始化即被传递。

##  <a name="getantialiasmode"></a>CRenderTarget：： GetAntialiasMode

检索非文本绘图操作的当前抗锯齿模式。

```
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;
```

### <a name="return-value"></a>返回值

非文本绘图操作的当前抗锯齿模式。

##  <a name="getdpi"></a>  CRenderTarget::GetDpi

返回呈现器目标的每英寸点数（DPI）

```
CD2DSizeF GetDpi() const;
```

### <a name="return-value"></a>返回值

呈现器目标的每英寸点数（DPI）。

##  <a name="getmaximumbitmapsize"></a>  CRenderTarget::GetMaximumBitmapSize

获取呈现器目标支持的任何一个位图维度的最大大小（以设备相关单位（像素）为单位）

```
UINT32 GetMaximumBitmapSize() const;
```

### <a name="return-value"></a>返回值

呈现器目标支持的任何一个位图维度的最大大小（以像素为单位）

##  <a name="getpixelformat"></a>CRenderTarget：： GetPixelFormat

检索呈现器目标的像素格式和 alpha 模式

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>返回值

呈现器目标的像素格式和 alpha 模式

##  <a name="getpixelsize"></a>  CRenderTarget::GetPixelSize

返回呈现器目标的大小（以设备像素为单位）

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>返回值

呈现器目标的大小（以设备像素为单位）

##  <a name="getrendertarget"></a>  CRenderTarget::GetRenderTarget

返回 ID2D1RenderTarget 接口

```
ID2D1RenderTarget* GetRenderTarget();
```

### <a name="return-value"></a>返回值

指向 ID2D1RenderTarget 接口的指针; 如果对象尚未初始化，则为 NULL。

##  <a name="getsize"></a>  CRenderTarget::GetSize

返回呈现器目标的大小，以与设备无关的像素为单位

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>返回值

呈现器目标的当前大小（以与设备无关的像素为单位）

##  <a name="gettags"></a>  CRenderTarget::GetTags

获取用于后续绘图操作的标签。

```
void GetTags(
    D2D1_TAG* tag1 = NULL,
    D2D1_TAG* tag2 = NULL) const;
```

### <a name="parameters"></a>参数

*tag1*<br/>
包含用于后续绘图操作的第一个标签。 此参数未经初始化即被传递。 如果指定 NULL，则不会检索此参数的值。

*tag2*<br/>
包含用于后续绘图操作的第二个标签。 此参数未经初始化即被传递。 如果指定 NULL，则不会检索此参数的值。

##  <a name="gettextantialiasmode"></a>  CRenderTarget::GetTextAntialiasMode

获取文本和字形绘制操作的当前抗锯齿模式。

```
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;
```

### <a name="return-value"></a>返回值

文本和字形绘制操作的当前抗锯齿模式。

##  <a name="gettextrenderingparams"></a>  CRenderTarget::GetTextRenderingParams

检索呈现器目标的当前文本呈现选项。

```
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```

### <a name="parameters"></a>参数

*textRenderingParams*<br/>
此方法返回时，将 textRenderingParamscontains 指针的地址，该指针指向呈现器目标的当前文本呈现选项。

##  <a name="gettransform"></a>CRenderTarget：： GetTransform

获取呈现器目标的当前转换。

```
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>参数

*transform*<br/>
当此返回时，包含呈现器目标的当前转换。 此参数未经初始化即被传递。

##  <a name="issupported"></a>CRenderTarget：： IsSupported

指示呈现器目标是否支持指定的属性

```
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;
```

### <a name="parameters"></a>参数

*renderTargetProperties*<br/>
要测试的呈现器目标属性

### <a name="return-value"></a>返回值

如果此呈现器目标支持指定的呈现器目标属性，则为 TRUE;否则为 FALSE

##  <a name="isvalid"></a>  CRenderTarget::IsValid

检查资源有效性

```
BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源有效，则为 TRUE;否则为 FALSE。

##  <a name="m_lstresources"></a>CRenderTarget：： m_lstResources

指向 CD2DResource 对象的指针的列表。

```
CObList m_lstResources;
```

##  <a name="m_prendertarget"></a>  CRenderTarget::m_pRenderTarget

指向 ID2D1RenderTarget 对象的指针。

```
ID2D1RenderTarget* m_pRenderTarget;
```

##  <a name="m_ptextformatdefault"></a>  CRenderTarget::m_pTextFormatDefault

指向 CD2DTextFormat 对象的指针，该对象包含默认文本格式。

```
CD2DTextFormat* m_pTextFormatDefault;
```

##  <a name="operator_id2d1rendertarget_star"></a>CRenderTarget：： operator ID2D1RenderTarget *

返回 ID2D1RenderTarget 接口

```
operator ID2D1RenderTarget*();
```

### <a name="return-value"></a>返回值

指向 ID2D1RenderTarget 接口的指针; 如果对象尚未初始化，则为 NULL。

##  <a name="popaxisalignedclip"></a>  CRenderTarget::PopAxisAlignedClip

从呈现器目标中移除最后一个轴对齐的剪辑。 调用此方法后，剪辑将不再应用于后续的绘图操作。

```
void PopAxisAlignedClip();
```

##  <a name="poplayer"></a>  CRenderTarget::PopLayer

停止将绘图操作重定向到由上一个 PushLayer 调用指定的层。

```
void PopLayer();
```

##  <a name="pushaxisalignedclip"></a>  CRenderTarget::PushAxisAlignedClip

从呈现器目标中移除最后一个轴对齐的剪辑。 调用此方法后，剪辑将不再应用于后续的绘图操作。

```
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```

### <a name="parameters"></a>参数

*rectClip*<br/>
剪辑区域的大小和位置（以与设备无关的像素为单位）。

*模式*<br/>
用于绘制具有子像素边界的剪辑矩形边缘的抗锯齿模式，并使用场景内容来混合剪辑。 当调用 PopAxisAlignedClip 方法时，将执行混合，而不会应用于层中的每个基元。

##  <a name="pushlayer"></a>  CRenderTarget::PushLayer

将指定层添加到呈现器目标，以便在调用 PopLayer 之前接收所有后续绘图操作。

```
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,
    CD2DLayer& layer);
```

### <a name="parameters"></a>参数

*layerParameters*<br/>
该层的内容边界、几何掩码、不透明度、不透明蒙板和消除锯齿选项。

*layer*<br/>
接收后续绘图操作的层。

##  <a name="restoredrawingstate"></a>  CRenderTarget::RestoreDrawingState

将呈现器目标的绘图状态设置为指定的 ID2D1DrawingStateBlock 的状态。

```
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```

### <a name="parameters"></a>参数

*drawingStateBlock*<br/>
呈现器目标的新绘制状态。

##  <a name="savedrawingstate"></a>  CRenderTarget::SaveDrawingState

将当前绘图状态保存到指定的 ID2D1DrawingStateBlock。

```
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;
```

### <a name="parameters"></a>参数

*drawingStateBlock*<br/>
此方法返回时，包含呈现器目标的当前绘图状态。 在将此参数传递给方法之前，必须先对其进行初始化。

##  <a name="setantialiasmode"></a>  CRenderTarget::SetAntialiasMode

设置呈现器目标的抗锯齿模式。 消除锯齿模式适用于所有后续绘图操作，不包括文本和字形绘制操作。

```
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```

### <a name="parameters"></a>参数

*antialiasMode*<br/>
用于将来的绘图操作的抗锯齿模式。

##  <a name="setdpi"></a>  CRenderTarget::SetDpi

设置呈现器目标的每英寸点数（DPI）。

```
void SetDpi(const CD2DSizeF& sizeDPI);
```

### <a name="parameters"></a>参数

*sizeDPI*<br/>
一个大于或等于零的值，该值指定呈现器目标的水平/verticalDPI。

##  <a name="settags"></a>  CRenderTarget::SetTags

为后续绘图操作指定标签。

```
void SetTags(
    D2D1_TAG tag1,
    D2D1_TAG tag2);
```

### <a name="parameters"></a>参数

*tag1*<br/>
要应用于后续绘图操作的标签。

*tag2*<br/>
要应用于后续绘图操作的标签。

##  <a name="settextantialiasmode"></a>  CRenderTarget::SetTextAntialiasMode

指定用于后续文本和字形绘制操作的抗锯齿模式。

```
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```

### <a name="parameters"></a>参数

*textAntialiasMode*<br/>
用于后续文本和字形绘制操作的抗锯齿模式。

##  <a name="settextrenderingparams"></a>  CRenderTarget::SetTextRenderingParams

指定要应用于所有后续文本和字形绘制操作的文本呈现选项。

```
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```

### <a name="parameters"></a>参数

*textRenderingParams*<br/>
要应用于所有后续文本和字形绘制操作的文本呈现选项;若要清除当前文本呈现选项，则为 NULL。

##  <a name="settransform"></a>CRenderTarget：： SetTransform

将指定的转换应用于呈现器目标，并替换现有转换。 所有后续绘图操作都在转换后的空间中发生。

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```

### <a name="parameters"></a>参数

*transform*<br/>
要应用于呈现器目标的转换。

##  <a name="verifyresource"></a>  CRenderTarget::VerifyResource

验证 CD2DResource 对象有效性;如果该对象尚不存在，则创建它。

```
BOOL VerifyResource(CD2DResource* pResource);
```

### <a name="parameters"></a>参数

*pResource*<br/>
指向 CD2DResource 对象的指针。

### <a name="return-value"></a>返回值

如果有效，则为 TRUE;否则为 FALSE。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
