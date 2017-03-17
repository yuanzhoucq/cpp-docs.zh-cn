---
title: "CRenderTarget 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CRenderTarget class
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
caps.latest.revision: 17
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6f77d482e7ee3bf0798ad488067893b3712aac62
ms.lasthandoff: 02/24/2017

---
# <a name="crendertarget-class"></a>CRenderTarget 类
ID2D1RenderTarget 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CRenderTarget : public CObject;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CRenderTarget::CRenderTarget](#crendertarget)|构造 CRenderTarget 对象。|  
|[CRenderTarget:: ~ CRenderTarget](#crendertarget__~crendertarget)|析构函数。 当呈现器目标对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CRenderTarget::Attach](#attach)|附加现有的呈现器目标接口的对象|  
|[CRenderTarget::BeginDraw](#begindraw)|在此呈现器目标上进行绘制的初始化。|  
|[CRenderTarget::Clear](#clear)|清除指定的颜色的绘图区域。|  
|[CRenderTarget::COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|将 GDI 颜色和 alpha 值转换为 D2D1_COLOR_F 对象。|  
|[CRenderTarget::CreateCompatibleRenderTarget](#createcompatiblerendertarget)|在当前的呈现器目标与兼容的中间屏幕外绘制过程中创建用于新的位图呈现器目标。|  
|[CRenderTarget::Destroy](#destroy)|删除一个或多个资源|  
|[CRenderTarget::Detach](#detach)|分离对象中的呈现器目标接口|  
|[CRenderTarget::DrawBitmap](#drawbitmap)|绘制由指定的 IDWriteTextLayout 对象所描述的格式化的文本。|  
|[CRenderTarget::DrawEllipse](#drawellipse)|绘制指定的椭圆使用指定的笔画样式的大纲。|  
|[CRenderTarget::DrawGeometry](#drawgeometry)|绘制指定的几何图形使用指定的笔画样式的大纲。|  
|[CRenderTarget::DrawGlyphRun](#drawglyphrun)|绘制指定的字形。|  
|[CRenderTarget::DrawLine](#drawline)|使用指定的笔画样式指定点之间绘制的直线。|  
|[CRenderTarget::DrawRectangle](#drawrectangle)|绘制一个具有指定的尺寸和笔画样式矩形边框。|  
|[CRenderTarget::DrawRoundedRectangle](#drawroundedrectangle)|绘制指定圆角矩形使用指定的笔画样式的大纲。|  
|[CRenderTarget::DrawText](#drawtext)|绘制指定的文本使用由 IDWriteTextFormat 对象提供的格式信息。|  
|[CRenderTarget::DrawTextLayout](#drawtextlayout)|绘制由指定的 IDWriteTextLayout 对象所描述的格式化的文本。|  
|[CRenderTarget::EndDraw](#enddraw)|结束在呈现器目标的绘制操作，并指示当前错误状态和关联的标记。|  
|[CRenderTarget::FillEllipse](#fillellipse)|绘制指定的椭圆的内部。|  
|[CRenderTarget::FillGeometry](#fillgeometry)|绘制指定的几何图形的内部。|  
|[CRenderTarget::FillMesh](#fillmesh)|绘制指定的网格中的内部。|  
|[CRenderTarget::FillOpacityMask](#fillopacitymask)|应用不透明蒙板由指定为画笔的位图所述，然后使用该画笔绘制呈现器目标的区域。|  
|[CRenderTarget::FillRectangle](#fillrectangle)|绘制指定矩形的内部。|  
|[CRenderTarget::FillRoundedRectangle](#fillroundedrectangle)|绘制指定圆角矩形的内部。|  
|[CRenderTarget::Flush](#flush)|执行所有挂起的绘制命令。|  
|[CRenderTarget::GetAntialiasMode](#getantialiasmode)|检索非文本绘制操作的当前抗锯齿模式。|  
|[CRenderTarget::GetDpi](#getdpi)|返回该呈现器目标的每英寸点数 (DPI)|  
|[CRenderTarget::GetMaximumBitmapSize](#getmaximumbitmapsize)|获取最大大小，以支持该呈现器目标的任意一个位图尺寸为依赖于设备的单位 （像素）|  
|[CRenderTarget::GetPixelFormat](#getpixelformat)|检索该呈现器目标的像素格式和 alpha 模式|  
|[CRenderTarget::GetPixelSize](#getpixelsize)|返回呈现器目标的大小以设备像素为单位|  
|[CRenderTarget::GetRenderTarget](#getrendertarget)|返回 ID2D1RenderTarget 接口|  
|[CRenderTarget::GetSize](#getsize)|以独立于设备的像素为单位返回该呈现器目标的大小|  
|[CRenderTarget::GetTags](#gettags)|获取用于后续绘图操作的标签。|  
|[CRenderTarget::GetTextAntialiasMode](#gettextantialiasmode)|文本和字形绘图操作获取当前的抗锯齿模式。|  
|[CRenderTarget::GetTextRenderingParams](#gettextrenderingparams)|检索呈现器目标的当前文本呈现选项。|  
|[CRenderTarget::GetTransform](#gettransform)|适用于呈现器目标，替换现有转换指定的转换。 所有后续的绘图操作将在转换后的空间。|  
|[CRenderTarget::IsSupported](#issupported)|该值指示该呈现器目标是否支持指定的属性|  
|[CRenderTarget::IsValid](#isvalid)|检查资源的有效性|  
|[CRenderTarget::PopAxisAlignedClip](#popaxisalignedclip)|从呈现器目标中删除轴对齐的最后一个剪辑。 调用此方法后，该剪辑不再应用于后续绘图操作。|  
|[CRenderTarget::PopLayer](#poplayer)|停止将绘制操作重定向到指定的最后一个 PushLayer 层调用。|  
|[CRenderTarget::PushAxisAlignedClip](#pushaxisalignedclip)|从呈现器目标中删除轴对齐的最后一个剪辑。 调用此方法后，该剪辑不再应用于后续绘图操作。|  
|[CRenderTarget::PushLayer](#pushlayer)|将指定的层添加到该呈现器目标中，以使其接收的所有后续绘制操作，直到 poplayer。|  
|[CRenderTarget::RestoreDrawingState](#restoredrawingstate)|与指定 ID2D1DrawingStateBlock 设置呈现器目标的绘图状态。|  
|[CRenderTarget::SaveDrawingState](#savedrawingstate)|将绘图的当前状态保存到指定 ID2D1DrawingStateBlock。|  
|[CRenderTarget::SetAntialiasMode](#setantialiasmode)|设置该呈现器目标的抗锯齿模式。 抗锯齿模式适用于所有后续的绘制操作，不包括文本和字形绘图操作。|  
|[CRenderTarget::SetDpi](#setdpi)|设置每英寸点数 (DPI) 呈现器目标。|  
|[CRenderTarget::SetTags](#settags)|指定用于后续绘图操作的标签。|  
|[CRenderTarget::SetTextAntialiasMode](#settextantialiasmode)|指定要用于后续的文本和标志符号的绘制操作的抗锯齿模式。|  
|[CRenderTarget::SetTextRenderingParams](#settextrenderingparams)|指定要应用于所有后续的文本和绘图操作的标志符号的文本呈现选项。|  
|[CRenderTarget::SetTransform](#settransform)|已重载。 适用于呈现器目标，替换现有转换指定的转换。 所有后续的绘图操作将在转换后的空间。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRenderTarget::VerifyResource](#verifyresource)|验证 CD2DResource 对象有效性;如果它尚不存在，则创建的对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CRenderTarget::operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|返回 ID2D1RenderTarget 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CRenderTarget::m_lstResources](#m_lstresources)|指向 CD2DResource 对象的指针的列表。|  
|[CRenderTarget::m_pRenderTarget](#m_prendertarget)|指向 ID2D1RenderTarget 对象的指针。|  
|[CRenderTarget::m_pTextFormatDefault](#m_ptextformatdefault)|指向包含默认的文本格式的 CD2DTextFormat 对象的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="_dtorcrendertarget"></a>CRenderTarget:: ~ CRenderTarget  
 析构函数。 当呈现器目标对象被销毁时调用。  
  
```  
virtual ~CRenderTarget();
```  
  
##  <a name="attach"></a>CRenderTarget::Attach  
 附加现有的呈现器目标接口的对象  
  
```  
void Attach(ID2D1RenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>参数  
 `pRenderTarget`  
 现有的呈现器目标接口。 不能为 NULL  
  
##  <a name="begindraw"></a>CRenderTarget::BeginDraw  
 在此呈现器目标上进行绘制的初始化。  
  
```  
void BeginDraw();
```  
  
##  <a name="clear"></a>CRenderTarget::Clear  
 清除指定的颜色的绘图区域。  
  
```  
void Clear(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>参数  
 `color`  
 向其清除绘图区域的颜色。  
  
##  <a name="colorref_to_d2dcolor"></a>CRenderTarget::COLORREF_TO_D2DCOLOR  
 将 GDI 颜色和 alpha 值转换为 D2D1_COLOR_F 对象。  
  
```  
static D2D1_COLOR_F COLORREF_TO_D2DCOLOR(
    COLORREF color,  
    int nAlpha = 255);
```  
  
### <a name="parameters"></a>参数  
 `color`  
 RGB 值。  
  
 `nAlpha`  
  
### <a name="return-value"></a>返回值  
 D2D1_COLOR_F 值。  
  
##  <a name="createcompatiblerendertarget"></a>CRenderTarget::CreateCompatibleRenderTarget  
 在当前的呈现器目标与兼容的中间屏幕外绘制过程中创建用于新的位图呈现器目标。  
  
```  
BOOL CreateCompatibleRenderTarget(
    CBitmapRenderTarget& bitmapTarget,  
    CD2DSizeF sizeDesired = CD2DSizeF(0., 0.), 
    CD2DSizeU sizePixelDesired = CD2DSizeU(0, 0), 
    D2D1_PIXEL_FORMAT* desiredFormat = NULL,  
    D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS options = D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>参数  
 `bitmapTarget`  
 此方法返回时，包含指向新的位图呈现器目标的指针的地址。 此参数未经初始化即被传递。  
  
 `sizeDesired`  
 新的呈现器目标，如果应不同于原始独立于设备的像素为单位的所需的大小呈现器目标，则为 NULL。 有关详细信息，请参阅“备注”部分。  
  
 `sizePixelDesired`  
 以像素为单位如果应不同于原始新的呈现器目标所需的大小呈现器目标，则为 NULL。 有关详细信息，请参阅“备注”部分。  
  
 `desiredFormat`  
 所需的像素格式和 alpha 模式，新的呈现器目标，则为 NULL。 如果像素格式设置为 DXGI_FORMAT_UNKNOWN 或此参数为 null，则新的呈现器目标使用相同的像素格式作为原始呈现器目标。 如果 alpha 模式 D2D1_ALPHA_MODE_UNKNOWN 或此参数为 NULL，则新的呈现器目标的 alpha 模式将默认为 D2D1_ALPHA_MODE_PREMULTIPLIED。 有关支持的像素格式信息，请参阅支持的像素格式和 Alpha 模式。  
  
 `options`  
 一个值，指定新的呈现器目标是否必须与 GDI 兼容。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE。  
  
##  <a name="crendertarget"></a>CRenderTarget::CRenderTarget  
 构造 CRenderTarget 对象。  
  
```  
CRenderTarget();
```  
  
##  <a name="destroy"></a>CRenderTarget::Destroy  
 删除一个或多个资源  
  
```  
BOOL Destroy(BOOL bDeleteResources = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bDeleteResources`  
 如果 bDeleteResources 为 TRUE 时，所有资源放在 m_lstResources 中将自动被都销毁。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE  
  
##  <a name="detach"></a>CRenderTarget::Detach  
 分离对象中的呈现器目标接口  
  
```  
ID2D1RenderTarget* Detach ();
```  
  
### <a name="return-value"></a>返回值  
 指向分离呈现器目标接口。  
  
##  <a name="drawbitmap"></a>CRenderTarget::DrawBitmap  
 绘制由指定的 IDWriteTextLayout 对象所描述的格式化的文本。  
  
```  
void DrawBitmap(
    CD2DBitmap* pBitmap,  
    const CD2DRectF& rectDest,  
    float fOpacity = 1.0,  
    D2D1_BITMAP_INTERPOLATION_MODE interpolationMode = D2D1_BITMAP_INTERPOLATION_MODE_LINEAR,  
    const CD2DRectF* pRectSrc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pBitmap`  
 要呈现的位图。  
  
 `rectDest`  
 大小和位置，以呈现器目标坐标空间向其绘制出位图的区域中的独立于设备的像素为单位。 如果该矩形不秩序井然，不绘制任何内容，但该呈现器目标不会进入错误状态。  
  
 `fOpacity`  
 指定要应用于位图; 的不透明度值 0.0 f 和 1.0 f （含)，之间的值此值乘以位图的内容的 alpha 值。  
  
 `interpolationMode`  
 如果位图进行缩放或旋转通过绘图操作，请使用插值模式。  
  
 `pRectSrc`  
 大小和位置，以与设备无关位图的坐标空间，位图中要绘制的区域中的像素为单位。  
  
##  <a name="drawellipse"></a>CRenderTarget::DrawEllipse  
 绘制指定的椭圆使用指定的笔画样式的大纲。  
  
```  
void DrawEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>参数  
 `ellipse`  
 位置和要在独立于设备的像素为单位中绘制的椭圆的半径。  
  
 `pBrush`  
 用于绘制椭圆的边框的画笔。  
  
 `fStrokeWidth`  
 椭圆的笔画的粗细。 笔划椭圆的边框上居中显示。  
  
 `strokeStyle`  
 要将应用于椭圆的概述或为 NULL 以绘制实心笔画笔画样式。  
  
##  <a name="drawgeometry"></a>CRenderTarget::DrawGeometry  
 绘制指定的几何图形使用指定的笔画样式的大纲。  
  
```  
void DrawGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pGeometry`  
 要绘制的几何图形。  
  
 `pBrush`  
 用于绘制几何图形的笔画的画笔。  
  
 `fStrokeWidth`  
 几何图形的笔画粗细。 笔划的几何轮廓上居中显示。  
  
 `strokeStyle`  
 要将应用于几何图形的概述或为 NULL 以绘制实心笔画笔画样式。  
  
##  <a name="drawglyphrun"></a>CRenderTarget::DrawGlyphRun  
 绘制指定的字形。  
  
```  
void DrawGlyphRun(
    const CD2DPointF& ptBaseLineOrigin,  
    const DWRITE_GLYPH_RUN& glyphRun,  
    CD2DBrush* pForegroundBrush,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>参数  
 `ptBaseLineOrigin`  
 独立于设备的像素为单位的标志符号的基线中的起点。  
  
 `glyphRun`  
 要呈现的标志符号。  
  
 `pForegroundBrush`  
 用于绘制指定的标志符号的画笔。  
  
 `measuringMode`  
 一个值，指示如何使用标志符号度量标准来格式化时测量的文本。 默认值为 DWRITE_MEASURING_MODE_NATURAL。  
  
##  <a name="drawline"></a>CRenderTarget::DrawLine  
 使用指定的笔画样式指定点之间绘制的直线。  
  
```  
void DrawLine(
    const CD2DPointF& ptFrom,  
    const CD2DPointF& ptTo,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>参数  
 `ptFrom`  
 行以独立于设备的像素为单位的起点。  
  
 `ptTo`  
 行以独立于设备的像素为单位的终点。  
  
 `pBrush`  
 用于绘制线条的笔画的画笔。  
  
 `fStrokeWidth`  
 大于或等于 0.0 f 的指定笔划宽度的值。 如果未指定此参数，则它默认为 1.0 f。 笔划线条上居中显示。  
  
 `strokeStyle`  
 笔画画图或为 NULL 以绘制一条实线样式。  
  
##  <a name="drawrectangle"></a>CRenderTarget::DrawRectangle  
 绘制一个具有指定的尺寸和笔画样式矩形边框。  
  
```  
void DrawRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 若要绘制，以独立于设备的像素为单位的矩形的尺寸  
  
 `pBrush`  
 用于绘制矩形的笔画的画笔  
  
 `fStrokeWidth`  
 大于或等于 0.0 f 的指定矩形的笔画宽度的值。 笔划的矩形轮廓上居中显示。  
  
 `strokeStyle`  
 画图，或者为 NULL 以绘制实心笔画笔划的样式。  
  
##  <a name="drawroundedrectangle"></a>CRenderTarget::DrawRoundedRectangle  
 绘制指定圆角矩形使用指定的笔画样式的大纲。  
  
```  
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>参数  
 `rectRounded`  
 若要绘制，以独立于设备的像素为单位的圆角矩形的尺寸。  
  
 `pBrush`  
 用于绘制圆角的矩形的边框的画笔。  
  
 `fStrokeWidth`  
 圆角的矩形的描边宽度。 笔划圆角的矩形轮廓上居中显示。 默认值为 1.0 f。  
  
 `strokeStyle`  
 圆角的矩形的笔画，或为 NULL 以绘制实心笔画样式。 默认值为 NULL。  
  
##  <a name="drawtext"></a>CRenderTarget::DrawText  
 绘制指定的文本使用由 IDWriteTextFormat 对象提供的格式信息。  
  
```  
void DrawText(
    const CString& strText,  
    const CD2DRectF& rect,  
    CD2DBrush* pForegroundBrush,  
    CD2DTextFormat* textFormat = NULL,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>参数  
 `strText`  
 指向要绘制的 Unicode 字符数组的指针。  
  
 `rect`  
 大小和在其中绘制文本区域的位置。  
  
 `pForegroundBrush`  
 用于绘制文本的画笔。  
  
 `textFormat`  
 一个对象，描述格式的要绘制的文本，如字体、 字体大小和流方向的详细信息。  
  
 `options`  
 一个值，该值指示是否应该与像素边界对齐文本和文本是否应剪切到布局矩形。 默认值为 D2D1_DRAW_TEXT_OPTIONS_NONE，表示应该与像素边界对齐文本，它不应剪辑到的布局矩形。  
  
 `measuringMode`  
 一个值，指示如何使用标志符号度量标准来格式化时测量的文本。 默认值为 DWRITE_MEASURING_MODE_NATURAL。  
  
##  <a name="drawtextlayout"></a>CRenderTarget::DrawTextLayout  
 绘制由指定的 IDWriteTextLayout 对象所描述的格式化的文本。  
  
```  
void DrawTextLayout(
    const CD2DPointF& ptOrigin,  
    CD2DTextLayout* textLayout,  
    CD2DBrush* pBrushForeground,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>参数  
 `ptOrigin`  
 描述以独立于设备的像素为单位，从该处绘制 textLayout 所描述的文本的左上角点。  
  
 `textLayout`  
 要绘制的格式化的文本。 不从 ID2D1Resource 继承任何绘制效果将被忽略。 如果有绘制从 ID2D1Resource 继承不是画笔效果，此方法将失败，并且该呈现器目标将处于错误状态。  
  
 `pBrushForeground`  
 用于绘制中尚没有方式绘制效果 （由 IDWriteTextLayout::SetDrawingEffect 方法指定） 与之相关联的画笔的 textLayout 的任何文本的画笔。  
  
 `options`  
 一个值，该值指示是否应该与像素边界对齐文本和文本是否应剪切到布局矩形。 默认值为 D2D1_DRAW_TEXT_OPTIONS_NONE，表示应该与像素边界对齐文本，它不应剪辑到的布局矩形。  
  
##  <a name="enddraw"></a>CRenderTarget::EndDraw  
 结束在呈现器目标的绘制操作，并指示当前错误状态和关联的标记。  
  
```  
HRESULT EndDraw();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="fillellipse"></a>CRenderTarget::FillEllipse  
 绘制指定的椭圆的内部。  
  
```  
void FillEllipse(
    const CD2DEllipse& ellipse,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `ellipse`  
 位置和半径，以独立于设备的像素为单位，要绘制的椭圆。  
  
 `pBrush`  
 用于绘制椭圆的内部的画笔。  
  
##  <a name="fillgeometry"></a>CRenderTarget::FillGeometry  
 绘制指定的几何图形的内部。  
  
```  
void FillGeometry(
    CD2DGeometry* pGeometry,  
    CD2DBrush* pBrush,  
    CD2DBrush* pOpacityBrush = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pGeometry`  
 要绘制的几何图形。  
  
 `pBrush`  
 用于绘制几何图形的画笔的内部。  
  
 `pOpacityBrush`  
 要应用于几何图形; 透明蒙板不是透明蒙板的为空。 如果指定不透明蒙板 （opacityBrush 参数），则画笔必须具有设置为 D2D1_EXTEND_MODE_CLAMP 其 x 和 y 扩展模式 ID2D1BitmapBrush。 有关详细信息，请参阅“备注”部分。  
  
##  <a name="fillmesh"></a>CRenderTarget::FillMesh  
 绘制指定的网格中的内部。  
  
```  
void FillMesh(
    CD2DMesh* pMesh,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `pMesh`  
 要绘制的网格。  
  
 `pBrush`  
 用于绘制网格的画笔。  
  
##  <a name="fillopacitymask"></a>CRenderTarget::FillOpacityMask  
 应用不透明蒙板由指定为画笔的位图所述，然后使用该画笔绘制呈现器目标的区域。  
  
```  
void FillOpacityMask(
    CD2DBitmap* pOpacityMask,  
    CD2DBrush* pBrush,  
    D2D1_OPACITY_MASK_CONTENT content,  
    const CD2DRectF& rectDest,  
    const CD2DRectF& rectSrc);
```  
  
### <a name="parameters"></a>参数  
 `pOpacityMask`  
 位置和半径，以独立于设备的像素为单位，要绘制的椭圆。  
  
 `pBrush`  
 用于绘制指定的目标的呈现器目标的区域的画笔。  
  
 `content`  
 包含的内容不透明蒙版的类型。 该值用于确定混合了不透明蒙版的色彩空间。  
  
 `rectDest`  
 若要绘图，以独立于设备的像素为单位的呈现器目标区域。  
  
 `rectSrc`  
 位图以用作透明蒙板，以独立于设备的像素为单位的区域。  
  
##  <a name="fillrectangle"></a>CRenderTarget::FillRectangle  
 绘制指定矩形的内部。  
  
```  
void FillRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 若要绘图，以独立于设备的像素为单位的矩形的尺寸。  
  
 `pBrush`  
 用于绘制矩形画笔的内部。  
  
##  <a name="fillroundedrectangle"></a>CRenderTarget::FillRoundedRectangle  
 绘制指定圆角矩形的内部。  
  
```  
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `rectRounded`  
 若要绘图，设备无关的像素的圆角矩形的尺寸。  
  
 `pBrush`  
 用于绘制圆角矩形的内部的画笔。  
  
##  <a name="flush"></a>CRenderTarget::Flush  
 执行所有挂起的绘制命令。  
  
```  
void Flush(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL);
```  
  
### <a name="parameters"></a>参数  
 `tag1`  
 包含绘图操作导致错误或 0，如果没有发生错误的标记。 此参数未经初始化即被传递。  
  
 `tag2`  
 包含绘图操作导致错误或 0，如果没有发生错误的标记。 此参数未经初始化即被传递。  
  
##  <a name="getantialiasmode"></a>CRenderTarget::GetAntialiasMode  
 检索非文本绘制操作的当前抗锯齿模式。  
  
```  
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前绘图操作的非文本的抗锯齿模式。  
  
##  <a name="getdpi"></a>CRenderTarget::GetDpi  
 返回该呈现器目标的每英寸点数 (DPI)  
  
```  
CD2DSizeF GetDpi() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现器目标的每英寸点数 (DPI)。  
  
##  <a name="getmaximumbitmapsize"></a>CRenderTarget::GetMaximumBitmapSize  
 获取最大大小，以支持该呈现器目标的任意一个位图尺寸为依赖于设备的单位 （像素）  
  
```  
UINT32 GetMaximumBitmapSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 最大大小，以像素为单位的呈现器目标受支持的任何一个位图维度  
  
##  <a name="getpixelformat"></a>CRenderTarget::GetPixelFormat  
 检索该呈现器目标的像素格式和 alpha 模式  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现器目标的像素格式和 alpha 模式  
  
##  <a name="getpixelsize"></a>CRenderTarget::GetPixelSize  
 返回呈现器目标的大小以设备像素为单位  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 该呈现器目标以设备像素为单位的大小  
  
##  <a name="getrendertarget"></a>CRenderTarget::GetRenderTarget  
 返回 ID2D1RenderTarget 接口  
  
```  
ID2D1RenderTarget* GetRenderTarget();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1RenderTarget 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="getsize"></a>CRenderTarget::GetSize  
 以独立于设备的像素为单位返回该呈现器目标的大小  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 以独立于设备的像素为单位呈现器目标的当前大小  
  
##  <a name="gettags"></a>CRenderTarget::GetTags  
 获取用于后续绘图操作的标签。  
  
```  
void GetTags(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 `tag1`  
 包含用于后续绘图操作的第一个标签。 此参数未经初始化即被传递。 如果指定 NULL，则此参数不检索任何值。  
  
 `tag2`  
 包含用于后续绘图操作的第二个标签。 此参数未经初始化即被传递。 如果指定 NULL，则此参数不检索任何值。  
  
##  <a name="gettextantialiasmode"></a>CRenderTarget::GetTextAntialiasMode  
 文本和字形绘图操作获取当前的抗锯齿模式。  
  
```  
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 文本和字形绘图操作的当前抗锯齿模式。  
  
##  <a name="gettextrenderingparams"></a>CRenderTarget::GetTextRenderingParams  
 检索呈现器目标的当前文本呈现选项。  
  
```  
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```  
  
### <a name="parameters"></a>参数  
 `textRenderingParams`  
 此方法返回时，textRenderingParamscontains 的地址的指针的呈现器目标的当前文本呈现选项。  
  
##  <a name="gettransform"></a>CRenderTarget::GetTransform  
 适用于呈现器目标，替换现有转换指定的转换。 所有后续的绘图操作将在转换后的空间。  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>参数  
 `transform`  
 要将应用于呈现器目标的转换。  
  
##  <a name="issupported"></a>CRenderTarget::IsSupported  
 该值指示该呈现器目标是否支持指定的属性  
  
```  
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;  
```  
  
### <a name="parameters"></a>参数  
 `renderTargetProperties`  
 要测试的呈现器目标属性  
  
### <a name="return-value"></a>返回值  
 如果指定的呈现器目标属性支持此呈现器目标; 则为 TRUE否则为 FALSE  
  
##  <a name="isvalid"></a>CRenderTarget::IsValid  
 检查资源的有效性  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果资源是有效，则为，TRUE否则为 FALSE。  
  
##  <a name="m_lstresources"></a>CRenderTarget::m_lstResources  
 指向 CD2DResource 对象的指针的列表。  
  
```  
CObList m_lstResources;  
```  
  
##  <a name="m_prendertarget"></a>CRenderTarget::m_pRenderTarget  
 指向 ID2D1RenderTarget 对象的指针。  
  
```  
ID2D1RenderTarget* m_pRenderTarget;  
```  
  
##  <a name="m_ptextformatdefault"></a>CRenderTarget::m_pTextFormatDefault  
 指向包含默认的文本格式的 CD2DTextFormat 对象的指针。  
  
```  
CD2DTextFormat* m_pTextFormatDefault;  
```  
  
##  <a name="operator_id2d1rendertarget_star"></a>CRenderTarget::operator ID2D1RenderTarget *  
 返回 ID2D1RenderTarget 接口  
  
```  
operator ID2D1RenderTarget*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1RenderTarget 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="popaxisalignedclip"></a>CRenderTarget::PopAxisAlignedClip  
 从呈现器目标中删除轴对齐的最后一个剪辑。 调用此方法后，该剪辑不再应用于后续绘图操作。  
  
```  
void PopAxisAlignedClip();
```  
  
##  <a name="poplayer"></a>CRenderTarget::PopLayer  
 停止将绘制操作重定向到指定的最后一个 PushLayer 层调用。  
  
```  
void PopLayer();
```  
  
##  <a name="pushaxisalignedclip"></a>CRenderTarget::PushAxisAlignedClip  
 从呈现器目标中删除轴对齐的最后一个剪辑。 调用此方法后，该剪辑不再应用于后续绘图操作。  
  
```  
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,  
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```  
  
### <a name="parameters"></a>参数  
 `rectClip`  
 大小和位置的剪辑区域中，以独立于设备的像素为单位。  
  
 `mode`  
 用于绘制具有子像素边界的剪辑矩形的边缘并进行混合与场景内容剪辑抗锯齿模式。 调用时，并不适用于在层内的每个基元 PopAxisAlignedClip 方法后，执行的混合。  
  
##  <a name="pushlayer"></a>CRenderTarget::PushLayer  
 将指定的层添加到该呈现器目标中，以使其接收的所有后续绘制操作，直到 poplayer。  
  
```  
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,  
    CD2DLayer& layer);
```  
  
### <a name="parameters"></a>参数  
 `layerParameters`  
 内容边界、 几何掩模、 不透明度、 不透明蒙板和层级的抗锯齿选项中。  
  
 `layer`  
 接收后续绘图操作层。  
  
##  <a name="restoredrawingstate"></a>CRenderTarget::RestoreDrawingState  
 与指定 ID2D1DrawingStateBlock 设置呈现器目标的绘图状态。  
  
```  
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```  
  
### <a name="parameters"></a>参数  
 `drawingStateBlock`  
 呈现器目标的新绘图的状态。  
  
##  <a name="savedrawingstate"></a>CRenderTarget::SaveDrawingState  
 将绘图的当前状态保存到指定 ID2D1DrawingStateBlock。  
  
```  
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;  
```  
  
### <a name="parameters"></a>参数  
 `drawingStateBlock`  
 此方法返回时，包含该呈现器目标的当前绘图状态。 此参数必须传递到该方法之前进行初始化。  
  
##  <a name="setantialiasmode"></a>CRenderTarget::SetAntialiasMode  
 设置该呈现器目标的抗锯齿模式。 抗锯齿模式适用于所有后续的绘制操作，不包括文本和字形绘图操作。  
  
```  
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```  
  
### <a name="parameters"></a>参数  
 `antialiasMode`  
 将来的绘图操作抗锯齿模式。  
  
##  <a name="setdpi"></a>CRenderTarget::SetDpi  
 设置每英寸点数 (DPI) 呈现器目标。  
  
```  
void SetDpi(const CD2DSizeF& sizeDPI);
```  
  
### <a name="parameters"></a>参数  
 `sizeDPI`  
 一个值大于或等于零，指定该呈现器目标水平/垂直 Dpi。  
  
##  <a name="settags"></a>CRenderTarget::SetTags  
 指定用于后续绘图操作的标签。  
  
```  
void SetTags(
    D2D1_TAG tag1,  
    D2D1_TAG tag2);
```  
  
### <a name="parameters"></a>参数  
 `tag1`  
 要应用于后续绘图操作的标签。  
  
 `tag2`  
 要应用于后续绘图操作的标签。  
  
##  <a name="settextantialiasmode"></a>CRenderTarget::SetTextAntialiasMode  
 指定要用于后续的文本和标志符号的绘制操作的抗锯齿模式。  
  
```  
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```  
  
### <a name="parameters"></a>参数  
 `textAntialiasMode`  
 要用于后续的文本和字形绘图操作抗锯齿模式。  
  
##  <a name="settextrenderingparams"></a>CRenderTarget::SetTextRenderingParams  
 指定要应用于所有后续的文本和绘图操作的标志符号的文本呈现选项。  
  
```  
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```  
  
### <a name="parameters"></a>参数  
 `textRenderingParams`  
 文本呈现选项应用于所有后续的文本和字形绘图操作;若要清除当前文本呈现选项则为 NULL。  
  
##  <a name="settransform"></a>CRenderTarget::SetTransform  
 适用于呈现器目标，替换现有转换指定的转换。 所有后续的绘图操作将在转换后的空间。  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);  
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```  
  
### <a name="parameters"></a>参数  
 `transform`  
 要将应用于呈现器目标的转换。  
  
##  <a name="verifyresource"></a>CRenderTarget::VerifyResource  
 验证 CD2DResource 对象有效性;如果它尚不存在，则创建的对象。  
  
```  
BOOL VerifyResource(CD2DResource* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 指向 CD2DResource 对象指针。  
  
### <a name="return-value"></a>返回值  
 TRUE 是如果有效，则为对象否则为 FALSE。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

