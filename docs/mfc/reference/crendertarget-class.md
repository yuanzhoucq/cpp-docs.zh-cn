---
title: "CRenderTarget 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46ca0fbb4b076fe8cf9dab4d986da487b16cc976
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="crendertarget-class"></a>CRenderTarget 类
ID2D1RenderTarget 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CRenderTarget : public CObject;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CRenderTarget::CRenderTarget](#crendertarget)|构造 CRenderTarget 对象。|  
|[CRenderTarget:: ~ CRenderTarget](#crendertarget__~crendertarget)|析构函数。 当呈现器目标对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRenderTarget::Attach](#attach)|附加现有呈现器对对象的目标接口|  
|[CRenderTarget::BeginDraw](#begindraw)|在此呈现器目标上绘制会启动。|  
|[CRenderTarget::Clear](#clear)|清除为指定的颜色的绘图区域。|  
|[CRenderTarget::COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|将 GDI 颜色和 alpha 值转换为 D2D1_COLOR_F 对象。|  
|[CRenderTarget::CreateCompatibleRenderTarget](#createcompatiblerendertarget)|创建与当前的呈现器目标兼容的中间屏幕外绘制期间使用新位图呈现器目标。|  
|[CRenderTarget::Destroy](#destroy)|删除一个或多个资源|  
|[CRenderTarget::Detach](#detach)|分离呈现器目标接口从该对象|  
|[CRenderTarget::DrawBitmap](#drawbitmap)|绘制由指定的 IDWriteTextLayout 对象描述的格式化的文本。|  
|[CRenderTarget::DrawEllipse](#drawellipse)|绘制指定的椭圆使用指定的笔画样式的大纲。|  
|[CRenderTarget::DrawGeometry](#drawgeometry)|绘制指定的几何图形使用指定的笔画样式的大纲。|  
|[CRenderTarget::DrawGlyphRun](#drawglyphrun)|绘制指定的标志符号。|  
|[CRenderTarget::DrawLine](#drawline)|使用指定的笔画样式指定点之间绘制一条线。|  
|[CRenderTarget::DrawRectangle](#drawrectangle)|绘制一个具有指定的维度和描边样式矩形的边框。|  
|[CRenderTarget::DrawRoundedRectangle](#drawroundedrectangle)|绘制指定圆角矩形，使用指定的笔画样式的大纲。|  
|[CRenderTarget::DrawText](#drawtext)|绘制指定的文本使用由 IDWriteTextFormat 对象提供的格式信息。|  
|[CRenderTarget::DrawTextLayout](#drawtextlayout)|绘制由指定的 IDWriteTextLayout 对象描述的格式化的文本。|  
|[CRenderTarget::EndDraw](#enddraw)|结束在呈现目标的绘制操作并指示当前错误状态和关联的标记。|  
|[CRenderTarget::FillEllipse](#fillellipse)|绘制指定的椭圆的内部。|  
|[CRenderTarget::FillGeometry](#fillgeometry)|绘制指定的几何图形的内部。|  
|[CRenderTarget::FillMesh](#fillmesh)|绘制指定的网格的内部。|  
|[CRenderTarget::FillOpacityMask](#fillopacitymask)|适用描述为画笔指定位图的不透明蒙板，并使用该画笔绘制呈现器目标的区域。|  
|[CRenderTarget::FillRectangle](#fillrectangle)|绘制指定矩形的内部。|  
|[CRenderTarget::FillRoundedRectangle](#fillroundedrectangle)|绘制指定圆角矩形的内部。|  
|[CRenderTarget::Flush](#flush)|执行所有挂起的绘图命令。|  
|[CRenderTarget::GetAntialiasMode](#getantialiasmode)|检索用于非文本绘图操作的当前抗锯齿模式。|  
|[CRenderTarget::GetDpi](#getdpi)|返回该呈现器目标的每英寸点数 (DPI)|  
|[CRenderTarget::GetMaximumBitmapSize](#getmaximumbitmapsize)|获取依赖于设备的单位 （像素） 的支持的呈现器目标的任何一个位图维度中的最大大小，|  
|[CRenderTarget::GetPixelFormat](#getpixelformat)|检索呈现器目标的像素格式和字母模式|  
|[CRenderTarget::GetPixelSize](#getpixelsize)|以设备像素为单位返回呈现器目标的大小|  
|[CRenderTarget::GetRenderTarget](#getrendertarget)|返回 ID2D1RenderTarget 接口|  
|[CRenderTarget::GetSize](#getsize)|以独立于设备的像素为单位返回呈现器目标的大小|  
|[CRenderTarget::GetTags](#gettags)|获取用于后续绘图操作标签。|  
|[CRenderTarget::GetTextAntialiasMode](#gettextantialiasmode)|文本和绘制操作的标志符号时，获取当前的抗锯齿模式。|  
|[CRenderTarget::GetTextRenderingParams](#gettextrenderingparams)|检索呈现器目标的当前文本呈现选项。|  
|[CRenderTarget::GetTransform](#gettransform)|适用于呈现器目标，替换现有转换指定的转换。 所有后续绘图操作发生在转换后的空间中。|  
|[CRenderTarget::IsSupported](#issupported)|指示呈现器目标是否支持指定的属性|  
|[CRenderTarget::IsValid](#isvalid)|检查资源有效性|  
|[CRenderTarget::PopAxisAlignedClip](#popaxisalignedclip)|从呈现器目标中删除最后一个的轴对齐剪辑。 调用此方法后，剪辑不再适用于后续绘图操作。|  
|[CRenderTarget::PopLayer](#poplayer)|停止将绘制操作重定向到指定的最后一个 PushLayer 层调用。|  
|[CRenderTarget::PushAxisAlignedClip](#pushaxisalignedclip)|从呈现器目标中删除最后一个的轴对齐剪辑。 调用此方法后，剪辑不再适用于后续绘图操作。|  
|[CRenderTarget::PushLayer](#pushlayer)|将指定的层添加到该呈现器目标，以便它接收所有后续的绘制操作，直到 poplayer。|  
|[CRenderTarget::RestoreDrawingState](#restoredrawingstate)|呈现器目标绘制状态设置为指定 ID2D1DrawingStateBlock 的。|  
|[CRenderTarget::SaveDrawingState](#savedrawingstate)|将当前绘图状态保存到指定 ID2D1DrawingStateBlock。|  
|[CRenderTarget::SetAntialiasMode](#setantialiasmode)|设置呈现器目标的抗锯齿模式。 抗锯齿模式适用于所有后续的绘制操作，不包括文本和绘制操作的标志符号。|  
|[CRenderTarget::SetDpi](#setdpi)|设置每英寸点数 (DPI) 呈现器目标。|  
|[CRenderTarget::SetTags](#settags)|指定用于后续绘图操作的标签。|  
|[CRenderTarget::SetTextAntialiasMode](#settextantialiasmode)|指定要用于后续的文本和标志符号的绘制操作的抗锯齿模式。|  
|[CRenderTarget::SetTextRenderingParams](#settextrenderingparams)|指定要应用于所有后续的文本和绘制操作的标志符号的文本呈现选项。|  
|[CRenderTarget::SetTransform](#settransform)|已重载。 适用于呈现器目标，替换现有转换指定的转换。 所有后续绘图操作发生在转换后的空间中。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRenderTarget::VerifyResource](#verifyresource)|验证 CD2DResource 对象有效性;如果它尚不存在，则创建的对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CRenderTarget::operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|返回 ID2D1RenderTarget 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CRenderTarget::m_lstResources](#m_lstresources)|指向 CD2DResource 对象的指针的列表。|  
|[CRenderTarget::m_pRenderTarget](#m_prendertarget)|指向 ID2D1RenderTarget 对象的指针。|  
|[CRenderTarget::m_pTextFormatDefault](#m_ptextformatdefault)|指向包含默认文本格式的 CD2DTextFormat 对象的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxrendertarget.h  
  
##  <a name="_dtorcrendertarget"></a>CRenderTarget:: ~ CRenderTarget  
 析构函数。 当呈现器目标对象被销毁时调用。  
  
```  
virtual ~CRenderTarget();
```  
  
##  <a name="attach"></a>CRenderTarget::Attach  
 附加现有呈现器对对象的目标接口  
  
```  
void Attach(ID2D1RenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>参数  
 `pRenderTarget`  
 现有呈现器目标接口。 不能为 NULL  
  
##  <a name="begindraw"></a>CRenderTarget::BeginDraw  
 在此呈现器目标上绘制会启动。  
  
```  
void BeginDraw();
```  
  
##  <a name="clear"></a>CRenderTarget::Clear  
 清除为指定的颜色的绘图区域。  
  
```  
void Clear(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>参数  
 `color`  
 向其清除的绘图区域的颜色。  
  
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
 创建与当前的呈现器目标兼容的中间屏幕外绘制期间使用新位图呈现器目标。  
  
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
 新的呈现器目标以是否应将其不同于原始独立于设备的像素为单位的所需的大小呈现器目标，则为 NULL。 有关详细信息，请参阅“备注”部分。  
  
 `sizePixelDesired`  
 以像素为单位是否应将其不同于原始新的呈现器目标所需的大小呈现器目标，则为 NULL。 有关详细信息，请参阅“备注”部分。  
  
 `desiredFormat`  
 所需的像素格式和新的 alpha 模式呈现器目标，则为 NULL。 如果像素格式设置为 DXGI_FORMAT_UNKNOWN 或者如果此参数为 null，新的呈现器目标将使用相同的像素格式，作为原始呈现器目标。 如果 alpha 模式 D2D1_ALPHA_MODE_UNKNOWN 或此参数为 NULL，则新的呈现器目标的 alpha 模式将默认为 D2D1_ALPHA_MODE_PREMULTIPLIED。 有关受支持的像素格式的信息，请参阅受支持像素格式和 Alpha 模式。  
  
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
 如果 bDeleteResources 为 TRUE，则将自动销毁位于 m_lstResources 中的所有资源。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE  
  
##  <a name="detach"></a>CRenderTarget::Detach  
 分离呈现器目标接口从该对象  
  
```  
ID2D1RenderTarget* Detach ();
```  
  
### <a name="return-value"></a>返回值  
 指向分离呈现器目标接口。  
  
##  <a name="drawbitmap"></a>CRenderTarget::DrawBitmap  
 绘制由指定的 IDWriteTextLayout 对象描述的格式化的文本。  
  
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
 大小和位置，以呈现器目标的坐标空间的位图绘制到的区域中的独立于设备的像素为单位。 如果在该矩形不秩序井然，不绘制任何内容，但该呈现器目标不会进入错误状态。  
  
 `fOpacity`  
 介于 0.0 f 和 1.0 f （含)，指定要应用于位图; 不透明度值此值乘以位图的内容的 alpha 值。  
  
 `interpolationMode`  
 要使用如果位图进行缩放或旋转的绘制操作的内插模式。  
  
 `pRectSrc`  
 大小和位置，以独立于设备的像素为单位的位图的坐标空间内要绘制的位图区域的位置。  
  
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
 位置和要绘制，以独立于设备的像素为单位的椭圆的半径。  
  
 `pBrush`  
 用于绘制椭圆的边框的画笔。  
  
 `fStrokeWidth`  
 椭圆的笔划的粗细。 笔画边框上居中的椭圆。  
  
 `strokeStyle`  
 要应用于椭圆的大纲或为 NULL 以绘制实心笔画的笔划的样式。  
  
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
 用于绘制几何图形的笔划画笔。  
  
 `fStrokeWidth`  
 该几何图形的笔划的粗细。 笔画边框上居中的几何图形。  
  
 `strokeStyle`  
 要应用的几何图形的大纲，或者为 NULL 以绘制实心笔画笔画样式。  
  
##  <a name="drawglyphrun"></a>CRenderTarget::DrawGlyphRun  
 绘制指定的标志符号。  
  
```  
void DrawGlyphRun(
    const CD2DPointF& ptBaseLineOrigin,  
    const DWRITE_GLYPH_RUN& glyphRun,  
    CD2DBrush* pForegroundBrush,  
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```  
  
### <a name="parameters"></a>参数  
 `ptBaseLineOrigin`  
 以独立于设备的像素为单位中的标志符号的基线的原点。  
  
 `glyphRun`  
 要呈现的标志符号。  
  
 `pForegroundBrush`  
 用于绘制指定的标志符号的画笔。  
  
 `measuringMode`  
 一个值，该值指示如何使用标志符号度量值来测量文本格式时。 默认值为 DWRITE_MEASURING_MODE_NATURAL。  
  
##  <a name="drawline"></a>CRenderTarget::DrawLine  
 使用指定的笔画样式指定点之间绘制一条线。  
  
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
 行，以独立于设备的像素为单位的起点。  
  
 `ptTo`  
 行，以独立于设备的像素为单位的终结点。  
  
 `pBrush`  
 用于绘制线条的描边的画笔。  
  
 `fStrokeWidth`  
 一个值大于或等于 0.0 f 的指定的笔划的宽度。 如果未指定此参数，则它默认为 1.0 f。 笔划居中在行上显示。  
  
 `strokeStyle`  
 绘制，或者为 NULL 以绘制一条实线的笔划的样式。  
  
##  <a name="drawrectangle"></a>CRenderTarget::DrawRectangle  
 绘制一个具有指定的维度和描边样式矩形的边框。  
  
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
 用于绘制矩形的笔划画笔  
  
 `fStrokeWidth`  
 大于或等于 0.0 f 的指定矩形的描边宽度的值。 笔画边框上居中的矩形。  
  
 `strokeStyle`  
 绘制，或者为 NULL 以绘制实心笔画的笔划的样式。  
  
##  <a name="drawroundedrectangle"></a>CRenderTarget::DrawRoundedRectangle  
 绘制指定圆角矩形，使用指定的笔画样式的大纲。  
  
```  
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush,  
    FLOAT fStrokeWidth = 1.0,  
    ID2D1StrokeStyle* strokeStyle = NULL);
```  
  
### <a name="parameters"></a>参数  
 `rectRounded`  
 要绘制，以独立于设备的像素为单位的圆角矩形的尺寸。  
  
 `pBrush`  
 用于绘制圆角的矩形的边框的画笔。  
  
 `fStrokeWidth`  
 圆角的矩形描边宽度。 笔划圆角的矩形轮廓上居中。 默认值为 1.0 f。  
  
 `strokeStyle`  
 圆角的矩形描边，或者为 NULL 以绘制实心笔画样式。 默认值为 NULL。  
  
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
 对象用于描述格式的要绘制的文本，如字体、 字号和流方向的详细信息。  
  
 `options`  
 一个值，该值指示是否应该与像素边界对齐文本和文本是否应剪裁到布局矩形。 默认值为 D2D1_DRAW_TEXT_OPTIONS_NONE，表示应该与像素边界对齐文本，它不应剪切到布局矩形。  
  
 `measuringMode`  
 一个值，该值指示如何使用标志符号度量值来测量文本格式时。 默认值为 DWRITE_MEASURING_MODE_NATURAL。  
  
##  <a name="drawtextlayout"></a>CRenderTarget::DrawTextLayout  
 绘制由指定的 IDWriteTextLayout 对象描述的格式化的文本。  
  
```  
void DrawTextLayout(
    const CD2DPointF& ptOrigin,  
    CD2DTextLayout* textLayout,  
    CD2DBrush* pBrushForeground,  
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```  
  
### <a name="parameters"></a>参数  
 `ptOrigin`  
 描述以独立于设备的像素为单位，在其中绘制 textLayout 所描述的文本的左上角点。  
  
 `textLayout`  
 要绘制的带格式的文本。 不继承 ID2D1Resource 任何绘制效果都被忽略。 如果有绘制继承 ID2D1Resource 不画笔效果，此方法失败，并且该呈现器目标将处于错误状态。  
  
 `pBrushForeground`  
 用于绘制中尚不包含作为绘制效果 （由 IDWriteTextLayout::SetDrawingEffect 方法指定） 与之关联的画笔的 textLayout 的任何文本的画笔。  
  
 `options`  
 一个值，该值指示是否应该与像素边界对齐文本和文本是否应剪裁到布局矩形。 默认值为 D2D1_DRAW_TEXT_OPTIONS_NONE，表示应该与像素边界对齐文本，它不应剪切到布局矩形。  
  
##  <a name="enddraw"></a>CRenderTarget::EndDraw  
 结束在呈现目标的绘制操作并指示当前错误状态和关联的标记。  
  
```  
HRESULT EndDraw();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
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
 要应用于该几何图形; 透明蒙板不是透明蒙板的为 NULL。 如果指定不透明蒙板 （opacityBrush 参数），则画笔必须已设置为 D2D1_EXTEND_MODE_CLAMP 其 x 和 y 扩展模式 ID2D1BitmapBrush。 有关详细信息，请参阅“备注”部分。  
  
##  <a name="fillmesh"></a>CRenderTarget::FillMesh  
 绘制指定的网格的内部。  
  
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
 适用描述为画笔指定位图的不透明蒙板，并使用该画笔绘制呈现器目标的区域。  
  
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
 包含的内容不透明蒙版的类型。 值用于确定在其中混合不透明蒙版的色彩空间。  
  
 `rectDest`  
 呈现器目标来绘制，以独立于设备的像素为单位的区域。  
  
 `rectSrc`  
 要用作透明蒙板，以独立于设备的像素为单位的位图的区域。  
  
##  <a name="fillrectangle"></a>CRenderTarget::FillRectangle  
 绘制指定矩形的内部。  
  
```  
void FillRectangle(
    const CD2DRectF& rect,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 若要绘制，以独立于设备的像素为单位的矩形的尺寸。  
  
 `pBrush`  
 用于绘制矩形的画笔的内部。  
  
##  <a name="fillroundedrectangle"></a>CRenderTarget::FillRoundedRectangle  
 绘制指定圆角矩形的内部。  
  
```  
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,  
    CD2DBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `rectRounded`  
 要绘制，以设备独立像素为单位的圆角矩形的尺寸。  
  
 `pBrush`  
 用于绘制圆角矩形的内部的画笔。  
  
##  <a name="flush"></a>CRenderTarget::Flush  
 执行所有挂起的绘图命令。  
  
```  
void Flush(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL);
```  
  
### <a name="parameters"></a>参数  
 `tag1`  
 包含绘制操作导致错误或 0，如果没有发生错误的标记。 此参数未经初始化即被传递。  
  
 `tag2`  
 包含绘制操作导致错误或 0，如果没有发生错误的标记。 此参数未经初始化即被传递。  
  
##  <a name="getantialiasmode"></a>CRenderTarget::GetAntialiasMode  
 检索用于非文本绘图操作的当前抗锯齿模式。  
  
```  
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 非文本绘图操作的当前抗锯齿模式。  
  
##  <a name="getdpi"></a>CRenderTarget::GetDpi  
 返回该呈现器目标的每英寸点数 (DPI)  
  
```  
CD2DSizeF GetDpi() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现器目标的每英寸点数 (DPI)。  
  
##  <a name="getmaximumbitmapsize"></a>CRenderTarget::GetMaximumBitmapSize  
 获取依赖于设备的单位 （像素） 的支持的呈现器目标的任何一个位图维度中的最大大小，  
  
```  
UINT32 GetMaximumBitmapSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 最大大小，以像素为单位，支持的呈现器目标的任何一个位图维度  
  
##  <a name="getpixelformat"></a>CRenderTarget::GetPixelFormat  
 检索呈现器目标的像素格式和字母模式  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>返回值  
 呈现器目标像素格式和字母模式  
  
##  <a name="getpixelsize"></a>CRenderTarget::GetPixelSize  
 以设备像素为单位返回呈现器目标的大小  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 以设备像素为单位的呈现器目标的大小  
  
##  <a name="getrendertarget"></a>CRenderTarget::GetRenderTarget  
 返回 ID2D1RenderTarget 接口  
  
```  
ID2D1RenderTarget* GetRenderTarget();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1RenderTarget 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="getsize"></a>CRenderTarget::GetSize  
 以独立于设备的像素为单位返回呈现器目标的大小  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 以独立于设备的像素为单位的呈现器目标的当前大小  
  
##  <a name="gettags"></a>CRenderTarget::GetTags  
 获取用于后续绘图操作标签。  
  
```  
void GetTags(
    D2D1_TAG* tag1 = NULL,  
    D2D1_TAG* tag2 = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 `tag1`  
 包含用于后续绘图操作的第一个标签。 此参数未经初始化即被传递。 如果指定 NULL，则将为此参数中不检索任何值。  
  
 `tag2`  
 包含用于后续的绘制操作的第二个标签。 此参数未经初始化即被传递。 如果指定 NULL，则将为此参数中不检索任何值。  
  
##  <a name="gettextantialiasmode"></a>CRenderTarget::GetTextAntialiasMode  
 文本和绘制操作的标志符号时，获取当前的抗锯齿模式。  
  
```  
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 文本和绘制操作的标志符号的当前抗锯齿模式。  
  
##  <a name="gettextrenderingparams"></a>CRenderTarget::GetTextRenderingParams  
 检索呈现器目标的当前文本呈现选项。  
  
```  
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```  
  
### <a name="parameters"></a>参数  
 `textRenderingParams`  
 此方法返回时，textRenderingParamscontains 呈现器目标的指针的地址的当前文本呈现选项。  
  
##  <a name="gettransform"></a>CRenderTarget::GetTransform  
 适用于呈现器目标，替换现有转换指定的转换。 所有后续绘图操作发生在转换后的空间中。  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>参数  
 `transform`  
 要应用到呈现目标的转换。  
  
##  <a name="issupported"></a>CRenderTarget::IsSupported  
 指示呈现器目标是否支持指定的属性  
  
```  
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;  
```  
  
### <a name="parameters"></a>参数  
 `renderTargetProperties`  
 要测试的呈现器目标属性  
  
### <a name="return-value"></a>返回值  
 如果此呈现器目标; 支持指定的呈现器目标属性为 TRUE否则为 FALSE  
  
##  <a name="isvalid"></a>CRenderTarget::IsValid  
 检查资源有效性  
  
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
 指向包含默认文本格式的 CD2DTextFormat 对象的指针。  
  
```  
CD2DTextFormat* m_pTextFormatDefault;  
```  
  
##  <a name="operator_id2d1rendertarget_star"></a>CRenderTarget::operator ID2D1RenderTarget *  
 返回 ID2D1RenderTarget 接口  
  
```  
operator ID2D1RenderTarget*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1RenderTarget 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="popaxisalignedclip"></a>CRenderTarget::PopAxisAlignedClip  
 从呈现器目标中删除最后一个的轴对齐剪辑。 调用此方法后，剪辑不再适用于后续绘图操作。  
  
```  
void PopAxisAlignedClip();
```  
  
##  <a name="poplayer"></a>CRenderTarget::PopLayer  
 停止将绘制操作重定向到指定的最后一个 PushLayer 层调用。  
  
```  
void PopLayer();
```  
  
##  <a name="pushaxisalignedclip"></a>CRenderTarget::PushAxisAlignedClip  
 从呈现器目标中删除最后一个的轴对齐剪辑。 调用此方法后，剪辑不再适用于后续绘图操作。  
  
```  
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,  
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```  
  
### <a name="parameters"></a>参数  
 `rectClip`  
 大小和位置的剪辑区域中，以独立于设备的像素为单位。  
  
 `mode`  
 用于绘制具有子像素边界的剪辑矩形的边缘并混合的场景内容剪辑抗锯齿模式。 当调用，并不适用于在层内的每个基元 PopAxisAlignedClip 方法后，执行的混合。  
  
##  <a name="pushlayer"></a>CRenderTarget::PushLayer  
 将指定的层添加到该呈现器目标，以便它接收所有后续的绘制操作，直到 poplayer。  
  
```  
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,  
    CD2DLayer& layer);
```  
  
### <a name="parameters"></a>参数  
 `layerParameters`  
 内容的边界、 几何掩码、 不透明度、 不透明蒙板和层的抗锯齿选项中。  
  
 `layer`  
 接收后续绘图操作层。  
  
##  <a name="restoredrawingstate"></a>CRenderTarget::RestoreDrawingState  
 呈现器目标绘制状态设置为指定 ID2D1DrawingStateBlock 的。  
  
```  
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```  
  
### <a name="parameters"></a>参数  
 `drawingStateBlock`  
 呈现器目标的绘制新状态。  
  
##  <a name="savedrawingstate"></a>CRenderTarget::SaveDrawingState  
 将当前绘图状态保存到指定 ID2D1DrawingStateBlock。  
  
```  
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;  
```  
  
### <a name="parameters"></a>参数  
 `drawingStateBlock`  
 此方法返回时，包含呈现器目标的当前绘图状态。 必须将其传递到方法之前初始化此参数。  
  
##  <a name="setantialiasmode"></a>CRenderTarget::SetAntialiasMode  
 设置呈现器目标的抗锯齿模式。 抗锯齿模式适用于所有后续的绘制操作，不包括文本和绘制操作的标志符号。  
  
```  
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```  
  
### <a name="parameters"></a>参数  
 `antialiasMode`  
 将来的绘制操作抗锯齿模式。  
  
##  <a name="setdpi"></a>CRenderTarget::SetDpi  
 设置每英寸点数 (DPI) 呈现器目标。  
  
```  
void SetDpi(const CD2DSizeF& sizeDPI);
```  
  
### <a name="parameters"></a>参数  
 `sizeDPI`  
 大于或等于指定的呈现器目标水平/垂直 Dpi 的零的值。  
  
##  <a name="settags"></a>CRenderTarget::SetTags  
 指定用于后续绘图操作的标签。  
  
```  
void SetTags(
    D2D1_TAG tag1,  
    D2D1_TAG tag2);
```  
  
### <a name="parameters"></a>参数  
 `tag1`  
 标签以应用于后续绘图操作。  
  
 `tag2`  
 标签以应用于后续绘图操作。  
  
##  <a name="settextantialiasmode"></a>CRenderTarget::SetTextAntialiasMode  
 指定要用于后续的文本和标志符号的绘制操作的抗锯齿模式。  
  
```  
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```  
  
### <a name="parameters"></a>参数  
 `textAntialiasMode`  
 要用于后续的文本和绘制操作的标志符号的抗锯齿模式。  
  
##  <a name="settextrenderingparams"></a>CRenderTarget::SetTextRenderingParams  
 指定要应用于所有后续的文本和绘制操作的标志符号的文本呈现选项。  
  
```  
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```  
  
### <a name="parameters"></a>参数  
 `textRenderingParams`  
 要应用于所有后续的文本和绘制操作; 的标志符号的文本呈现选项为 NULL 以清除当前文本呈现选项。  
  
##  <a name="settransform"></a>CRenderTarget::SetTransform  
 适用于呈现器目标，替换现有转换指定的转换。 所有后续绘图操作发生在转换后的空间中。  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);  
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```  
  
### <a name="parameters"></a>参数  
 `transform`  
 要应用到呈现目标的转换。  
  
##  <a name="verifyresource"></a>CRenderTarget::VerifyResource  
 验证 CD2DResource 对象有效性;如果它尚不存在，则创建的对象。  
  
```  
BOOL VerifyResource(CD2DResource* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 指向 CD2DResource 对象的指针。  
  
### <a name="return-value"></a>返回值  
 TRUE 是对象如果有效，则为否则为 FALSE。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)
