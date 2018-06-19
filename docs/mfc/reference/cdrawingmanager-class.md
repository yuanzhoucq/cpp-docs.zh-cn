---
title: CDrawingManager 类 |Microsoft 文档
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
ms.openlocfilehash: b9a0255bae48ad61f140bdc8aa8a6091cf10bc77
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376001"
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
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|创建应用程序可以直接写入一个 32 位独立于设备的位图 (DIB)。|  
|[CDrawingManager::DrawAlpha](#drawalpha)|显示具有透明或半透明的像素为单位的位图。|  
|[CDrawingManager::DrawRotated](#drawrotated)|旋转的源 DC 的 + /-90 度，在给定矩形内的内容|  
|[CDrawingManager::DrawEllipse](#drawellipse)|绘制一个具有提供的填充和边框颜色。|  
|[CDrawingManager::DrawGradientRing](#drawgradientring)|绘制一个环并使用颜色渐变填充它。|  
|[CDrawingManager::DrawLine CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|绘制一条线。|  
|[CDrawingManager::DrawRect](#drawrect)|绘制一个具有提供的填充和边框颜色的矩形。|  
|[CDrawingManager::DrawShadow](#drawshadow)|绘制的矩形区域的阴影。|  
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|用两种颜色渐变填充的矩形区域。|  
|[CDrawingManager::FillGradient](#fillgradient)|用指定的颜色渐变填充的矩形区域。|  
|[CDrawingManager::FillGradient2](#fillgradient2)|用指定的颜色渐变填充的矩形区域。 此外指定的渐变的颜色更改方向。|  
|[CDrawingManager::GrayRect](#grayrect)|使用指定的灰色颜色填充的矩形。|  
|[CDrawingManager::HighlightRect](#highlightrect)|突出显示的矩形区域。|  
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|将一种颜色从 HLS 表示形式转换为 RGB 表示形式。|  
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|将一种颜色从 HLS 表示形式转换为 RGB 表示形式。|  
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|将一种颜色从 HSV 表示形式转换为 RGB 表示形式。|  
|[CDrawingManager::HuetoRGB](#huetorgb)|将一个色调值转换为红色、 绿色还是蓝色组件的帮助器方法。|  
|[CDrawingManager::MirrorRect](#mirrorrect)|翻转的矩形区域。|  
|[CDrawingManager::PixelAlpha](#pixelalpha)|确定半透明的像素的最终颜色的帮助器方法。|  
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|创建一个可以用作阴影的位图。|  
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|将一种颜色从 RGB 表示形式转换为 HSL 表示形式。|  
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|将一种颜色从 RGB 表示形式转换为 HSV 表示形式。|  
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|颜色位图中的部分透明像素的帮助器方法。|  
|[CDrawingManager::SetPixel](#setpixel)|更改为指定的颜色的位图中的单一像素的帮助器方法。|  
|[CDrawingManager::SmartMixColors](#smartmixcolors)|合并两个颜色根据加权的比率。|  
  
## <a name="remarks"></a>备注  
 `CDrawingManager`类提供了用于绘制阴影、 颜色渐变和突出显示的矩形的函数。 它还执行 alpha 混合。 此类可用于直接更改你的应用程序 UI。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
 `CDrawingManager`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdrawmanager.h  
  
##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager  
 构造[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)对象。  
  
```  
CDrawingManager(CDC& dc);
```  
  
### <a name="parameters"></a>参数  
 [in] `dc`  
 对设备上下文的引用。 `CDrawingManager`使用此上下文的绘图区域。  
  
##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32  
 创建应用程序可以直接写入一个 32 位独立于设备的位图 (DIB)。  
  
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
|[in] `size`|A [CSize](../../atl-mfc-shared/reference/csize-class.md)参数可指示位图的大小。|  
|[out] `pBits`|指向接收 DIB 的位置的数据指针的位值。|  
|`bitmap`|指向的原始位图的句柄|  
|`clrTransparent`|指定的原始位图的透明颜色的 RGB 值。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则新创建的 DIB 位图句柄否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 有关如何创建 DIB 位图的详细信息，请参阅[CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183491)。  
  
##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha  
 显示具有透明或半透明的像素为单位的位图。  
  
```  
void DrawAlpha(
    CDC* pDstDC,  
    const CRect& rectDst,  
    CDC* pSrcDC,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDstDC`  
 指向目标的设备上下文的指针。  
  
 [in] `rectDst`  
 目标矩形。  
  
 [in] `pSrcDC`  
 指向源设备上下文的指针。  
  
 [in] `rectSrc`  
 源矩形中。  
  
### <a name="remarks"></a>备注  
 此方法执行两个位图的 alpha 混合。 Alpha 混合的详细信息，请参阅[AlphaBlend](http://msdn.microsoft.com/library/windows/desktop/dd183351) Windows SDK 中。  
  
##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse  
 绘制一个具有提供的填充和边框颜色。  
  
```  
void DrawEllipse(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 椭圆的边框。  
  
 [in] `clrFill`  
 此方法用于填充椭圆颜色。  
  
 [in] `clrLine`  
 此方法使用作为椭圆的边框颜色。  
  
### <a name="remarks"></a>备注  
 此方法返回不会绘制一个椭圆，如果任意一种颜色设置为-1。 它还返回不会绘制一个椭圆，如果边界矩形任一维度为 0。  
  
##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing  
 绘制一个环并使用颜色渐变填充它。  
  
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
 [in] `rect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md)指定渐变环的边界的参数。  
  
 [in] `colorStart`  
 第一种颜色的渐变。  
  
 [in] `colorFinish`  
 最后一种颜色的渐变。  
  
 [in] `colorBorder`  
 边框的颜色。  
  
 [in] `nAngle`  
 一个参数，指定的初始渐变绘制的角度。 此值应介于 0 至 360 之间。  
  
 [in] `nWidth`  
 环的边框的宽度。  
  
 [in] `clrFace`  
 环的内部的颜色。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 由定义的矩形`rect`必须至少 5 个像素宽和 5 像素高。  
  
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
|[in] `x1`|行的开始位置 x 坐标。|  
|[in] `y1`|Y 坐标的一行开始。|  
|[in] `x2`|行的结束位置的 x 坐标。|  
|[in] `y2`|行的结束位置的 y 坐标。|  
|[in] `clrLine`|线条的颜色。|  
  
### <a name="remarks"></a>备注  
 如果此方法将失败`clrLine`等于-1。  
  
##  <a name="drawrect"></a>  CDrawingManager::DrawRect  
 绘制一个具有提供的填充和边框颜色的矩形。  
  
```  
void DrawRect(
    const CRect& rect,  
    COLORREF clrFill,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 矩形的边界。  
  
 [in] `clrFill`  
 此方法使用以填充矩形的颜色。  
  
 [in] `clrLine`  
 此方法使用矩形的边框颜色。  
  
### <a name="remarks"></a>备注  
 此方法返回不会绘制一个矩形，如果任意一种颜色设置为-1。 它还返回如果任一的矩形的尺寸为 0。  
  
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
 [in] `rect`  
 你的应用程序中的矩形区域。 绘制管理器将绘制阴影，在此区域的下方。  
  
 [in] `nDepth`  
 阴影的高度和宽度。  
  
 [in] `iMinBrightness`  
 最小阴影的亮度。  
  
 [in] `iMaxBrightness`  
 最大阴影的亮度。  
  
 [in] `pBmpSaveBottom`  
 指向包含阴影的底部部分的图像的位图的指针。  
  
 [in] `pBmpSaveRight`  
 指向包含矩形右侧绘制阴影的图像的位图的指针。  
  
 [in] `clrBase`  
 阴影的颜色。  
  
 [in] `bRightShadow`  
 一个布尔型参数，该值指示如何绘制阴影。 如果`bRightShadow`是`TRUE`，`DrawShadow`矩形右侧绘制阴影。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 你也可以使用参数的底部和右侧阴影提供两个有效的位图`pBmpSaveBottom`和`pBmpSaveRight`。 如果这些[CBitmap](../../mfc/reference/cbitmap-class.md)对象具有附加的 GDI 对象，`DrawShadow`将使用这些位图作为阴影。 如果`CBitmap`参数根本没有附加的 GDI 对象，`DrawShadow`绘制阴影，并将位图附加到的参数。 在将来调用`DrawShadow`，你可以提供这些位图位图，以加速绘制过程。 有关详细信息`CBitmap`类和 GDI 对象，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
 如果这些参数任一`NULL`，`DrawShadow`自动绘制阴影。  
  
 如果你设置`bRightShadow`到`FALSE`，将绘制阴影，下方和矩形区域的左侧。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`DrawShadow`方法`CDrawingManager`类。 此代码片段属于[Prop 表演示示例](../../visual-cpp-samples.md)。  
  
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
 [in] `rect`  
 要填充的矩形。  
  
 [in] `colorStart1`  
 第一个颜色渐变的初始颜色。  
  
 [in] `colorFinish1`  
 第一个颜色渐变的最终颜色。  
  
 [in] `colorStart2`  
 第二个颜色渐变的初始颜色。  
  
 [in] `colorFinish2`  
 第二个颜色渐变的最终颜色。  
  
 [in] `bHorz`  
 一个布尔型参数，该值指示是否`Fill4ColorsGradient`水平或垂直渐变的颜色。 `TRUE` 指示水平渐变。  
  
 [in] `nPercentage`  
 从 0-100 的整数。 此值指示要使用的第一个颜色渐变填充的矩形的百分比。  
  
### <a name="remarks"></a>备注  
 如果两种颜色渐变填充的矩形，他们就是所在上面相互或到对方，具体取决于值的下一步`bHorz`。 使用方法单独计算每个颜色渐变[CDrawingManager::FillGradient](#fillgradient)。  
  
 如果此方法将生成断言失败`nPercentage`小于 0 或大于 100。  
  
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
 [in] `rect`  
 要填充的矩形区域。  
  
 [in] `colorStart`  
 第一种颜色的渐变。  
  
 [in] `colorFinish`  
 最终的渐变颜色。  
  
 [in] `bHorz`  
 指定一个布尔型参数是否`FillGradient`应绘制水平或垂直渐变。  
  
 [in] `nStartFlatPercentage`  
 矩形所占的`FillGradient`填入`colorStart`启动渐变之前。  
  
 [in] `nEndFlatPercentage`  
 矩形所占的`FillGradient`填入`colorFinish`它完成渐变后。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`FillGradient`方法`CDrawingManager`类。 此代码片段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。  
  
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
 [in] `rect`  
 要填充的矩形区域。  
  
 [in] `colorStart`  
 第一种渐变的颜色。  
  
 [in] `colorFinish`  
 渐变的最后一个颜色。  
  
 [in] `nAngle`  
 介于 0 至 360 之间的整数。 此参数指定的颜色渐变的方向。  
  
### <a name="remarks"></a>备注  
 使用`nAngle`指定的颜色渐变的方向。 当你指定的颜色渐变的方向时，你还指定的颜色渐变的开始位置。 值为 0，`nAngle`指示渐变开始按自上而下的矩形。 作为`nAngle`增加，起始位置的渐变会基于角度逆时针方向移动。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`FillGradient2`方法`CDrawingManager`类。 此代码片段属于[新控件示例](../../visual-cpp-samples.md)。  
  
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
 [in] `rect`  
 要填充的矩形区域。  
  
 [in] `nPercentage`  
 您希望在矩形中的灰色的百分比。  
  
 [in] `clrTransparent`  
 透明的颜色。  
  
 [in] `clrDisabled`  
 如果此方法使用的反饱和度的颜色`nPercentage`设置为-1。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 为参数`nPercentage`，较低的值指示较深的颜色。  
  
 最大值`nPercentage`为 200。 大于 200 的值不会更改矩形的外观。 如果值为-1，则此方法使用`clrDisabled`来限制饱和度的矩形。  
  
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
 [in] `rect`  
 以突出显示矩形区域。  
  
 [in] `nPercentage`  
 一个百分比，它指示突出显示应如何透明。  
  
 [in] `clrTransparent`  
 透明的颜色。  
  
 [in] `nTolerance`  
 一个介于 0 和 255 之间的整数，指示颜色容差。  
  
 [in] `clrBlend`  
 用于混合基础颜色。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果`nPercentage`介于 0 和 99 之间，之间`HighlightRect`使用 alpha 混合算法。 Alpha 混合的详细信息，请参阅[Alpha 混合线条和填充](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)。 如果`nPercentage`为-1，此方法使用默认突出显示级别。 如果`nPercentage`为 100，此方法不执行任何操作并返回`TRUE`。  
  
 该方法使用参数`nTolerance`以确定是否要突出显示的矩形区域。 以突出显示的矩形，你的应用程序的背景色之间的差异和`clrTransparent`必须小于`nTolerance`中每个颜色组件 （红色、 绿色和蓝色）。  
  
##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE  
 将一种颜色从 HLS 表示形式转换为 RGB 表示形式。  
  
```  
static COLORREF __stdcall HLStoRGB_ONE(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>参数  
 [in] `H`  
 介于 0 和 1 之间的数字表示颜色色调。  
  
 [in] `L`  
 介于 0 和 1 之间的数字表示颜色亮度。  
  
 [in] `S`  
 介于 0 和 1 之间的数字表示的颜色饱和度。  
  
### <a name="return-value"></a>返回值  
 RGB 颜色的表示形式 HLS 提供。  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关不同的表示形式的颜色的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
 此方法与`CDrawingManager::HLStoRGB_TWO`方法执行相同的操作，但需要不同的值`H`参数。 在此方法，`H`是圆的百分比。 在`CDrawingManager::HLStoRGB_TWO`方法，`H`是介于 0 至 360，这两者都代表红色度值。 例如，对于`HLStoRGB_ONE`，0.25 的一个值`H`等效于值为 90 与`HLStoRGB_TWO`。  
  
##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO  
 将一种颜色从 HLS 表示形式转换为 RGB 表示形式。  
  
```  
static COLORREF __stdcall HLStoRGB_TWO(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>参数  
 [in] `H`  
 表示颜色色调介于 0 至 360 数字。  
  
 [in] `L`  
 介于 0 和 1 之间的数字表示颜色亮度。  
  
 [in] `S`  
 介于 0 和 1 之间的数字表示的颜色饱和度。  
  
### <a name="return-value"></a>返回值  
 RGB 颜色的表示形式 HLS 提供。  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关不同的表示形式的颜色的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
 此方法与[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法执行相同的操作，但需要不同的值`H`参数。 在此方法，`H`是介于 0 至 360，这两者都代表红色度值。 在[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法，`H`是圆的百分比。 例如，对于`HLStoRGB_ONE`，0.25 的一个值`H`等效于值为 90 与`HLStoRGB_TWO`。  
  
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
|[in] `H`|0 至 360 之间的数字，指示颜色色调。|  
|[in] `S`|介于 0 和 1 之间的数字表示的颜色饱和度。|  
|[in] `V`|介于 0 和 1 之间的数字表示颜色的值。|  
  
### <a name="return-value"></a>返回值  
 RGB 颜色的表示形式 HSV 提供。  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关不同的表示形式的颜色的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB  
 将一个色调值转换为红色、 绿色还是蓝色组件。  
  
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
 [in] `m1`  
 请参阅“备注”。  
  
 [in] `m2`  
 请参阅“备注”。  
  
 [in] `h`  
 请参阅“备注”。  
  
 [in] `rm1`  
 请参阅“备注”。  
  
 [in] `rm2`  
 请参阅“备注”。  
  
 [in] `rh`  
 请参阅“备注”。  
  
### <a name="return-value"></a>返回值  
 提供的色调单个红色、 绿色还是蓝色组件。  
  
### <a name="remarks"></a>备注  
 此方法是一个帮助器方法，`CDrawingManager`类用来计算的一种颜色的 HSV 或 HSL 表示各个的红色、 绿色和蓝色组件。 此方法不是直接由程序员调用。 输入的参数为依赖于转换算法的值。  
  
 若要转换到的 RGB 表示 HSV 或 HSL 颜色，请调用以下方法之一：  
  
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
 [in] `rect`  
 翻转的区域边界的矩形。  
  
 [in] `bHorz`  
 一个布尔型参数，该值指示在该矩形翻转水平或垂直。  
  
### <a name="remarks"></a>备注  
 此方法可反转拥有的设备任何的上下文区域`CDrawingManager`类。 如果`bHorz`设置为`TRUE`，此方法水平翻转区域。 否则，它应当垂直翻转区域。  
  
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
 [in] `srcPixel`  
 像素初始颜色。  
  
 [in] `percent`  
 0 到 100 之间的数字表示透明度的百分比。 100 的值指示的初始颜色是完全透明。  
  
 [in] `percentR`  
 0 到 100 之间的数字表示的红色组件透明度的百分比。  
  
 [in] `percentG`  
 0 到 100 之间的数字表示的绿色组件透明度的百分比。  
  
 [in] `percentB`  
 0 到 100 之间的数字表示的蓝色组件透明度的百分比。  
  
 [in] `dstPixel`  
 像素基础颜色。  
  
### <a name="return-value"></a>返回值  
 半透明的像素最终颜色。  
  
### <a name="remarks"></a>备注  
 这是用于着色半透明的位图的帮助器类，并不旨在直接由程序员调用。  
  
 如果你使用具有方法版本`dstPixel`，最终颜色是的组合`dstPixel`和`srcPixel`。 `srcPixel`颜色是通过基础颜色的部分透明颜色`dstPixel`。  
  
##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask  
 创建一个可以用作阴影的位图。  
  
```  
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,  
    COLORREF clrBase,  
    int iMinBrightness = 0,  
    int iMaxBrightness = 100);
```  
  
### <a name="parameters"></a>参数  
 [in] `nDepth`  
 阴影的高度和宽度。  
  
 [in] `clrBase`  
 阴影的颜色。  
  
 [in] `iMinBrightness`  
 最小阴影的亮度。  
  
 [in] `iMaxBrightness`  
 最大阴影的亮度。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则创建的位图句柄否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 如果`nDepth`是设置为 0，此方法退出并返回`NULL`。 如果`nDepth`为小于 3、 宽度和高度阴影被设置为 3 个像素。  
  
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
|[in] `rgb`|RGB 值中的颜色。|  
|[out] `H`|指向一个双精度值，该方法将颜色色调在其中存储的指针。|  
|[out] `S`|指向一个双精度值，该方法将颜色饱和度在其中存储的指针。|  
|[out] `L`|指向一个双精度值，该方法将颜色亮度在其中存储的指针。|  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关不同的表示形式的颜色的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
 返回的值为`H`表示为介于 0 和 1 其中 0 和 1 代表红色之间的小数部分。 返回的值`S`和`L`是介于 0 和 1 之间的数字。  
  
##  <a name="rgbtohsv"></a>  CDrawingManager::RGBtoHSV  
 将一种颜色从 RGB 表示形式转换为 HSV 表示形式。  
  
```  
static void __stdcall RGBtoHSV(
    COLORREF rgb,  
    double* H,  
    double* S,  
    double* V);
```  
  
### <a name="parameters"></a>参数  
 [in] `rgb`  
 要转换 RGB 表示形式中的颜色。  
  
 [out] `H`  
 指向一个双精度值，此方法将生成的颜色色调在其中存储的指针。  
  
 [out] `S`  
 指向一个双精度值，此方法将生成的颜色饱和度在其中存储的指针。  
  
 [out] `V`  
 指向此方法将生成的颜色的值存储的其中一个双精度值的指针。  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 HSL （色调、 饱和度和亮度） 或 RGB （红色、 绿色和蓝色）。 有关不同的表示形式的颜色的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/p/?linkid=119126)。  
  
 返回的值为`H`是 0 至 360 之间的数字 0 至 360 其中指示红色。 返回值为`S`和`V`是介于 0 和 1 之间的数字。  
  
##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel  
 颜色位图中的透明像素。  
  
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
 [in] `pBits`  
 指向位图的位值的指针。  
  
 [in] `rect`  
 你的应用程序中的矩形区域。 绘制 manager 绘制阴影下方和右侧的此区域。  
  
 [in] `x`  
 为颜色像素水平坐标。  
  
 [in] `y`  
 为颜色像素垂直坐标。  
  
 [in] `percent`  
 透明度的百分比。  
  
 [in] `iShadowSize`  
 阴影的高度和宽度。  
  
 [in] `clrBase`  
 阴影的颜色。  
  
 [in] `bIsRight`  
 一个布尔型参数，该值指示为颜色的像素。 有关详细信息，请参阅备注部分。  
  
### <a name="remarks"></a>备注  
 此方法是使用一个帮助器方法[CDrawingManager::DrawShadow](#drawshadow)方法。 我们建议，如果你想要绘制阴影，请调用`CDrawingManager::DrawShadow`相反。  
  
 如果`bIsRight`设置为`TRUE`，颜色的像素为单位`x`像素的右边缘从`rect`。 如果它是`FALSE`，颜色的像素为单位`x`像素，距左边缘`rect`。  
  
##  <a name="setpixel"></a>  CDrawingManager::SetPixel  
 更改为指定颜色位图中的单一像素。  
  
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
|[in] `pBits`|指向位图的位值的指针。|  
|[in] `cx`|总位图的宽度。|  
|[in] `cy`|总位图的高度。|  
|[in] `x`|要更改的位图的像素 x 坐标。|  
|[in] `y`|要更改的位图的像素 y 坐标。|  
|[in] `color`|由提供的坐标的像素新颜色。|  
  
##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors  
 合并两个颜色根据加权的比率。  
  
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
|[in] `color1`|要组合的第一个颜色。|  
|[in] `color2`|要组合的第二个颜色。|  
|[in] `dblLumRatio`|新颜色亮度率。 `SmartMixColors` 在确定最终颜色之前乘以此比率的混合颜色亮度。|  
|[in] `k1`|第一种颜色加权的比率。|  
|[in] `k2`|第二个颜色加权的比率。|  
  
### <a name="return-value"></a>返回值  
 表示提供颜色的加权的混合的颜色。  
  
### <a name="remarks"></a>备注  
 如果此方法失败并出现错误`k1`或`k2`小于零。 如果这些参数将设置为 0，则该方法返回`RGB(0, 0, 0)`。  
  
 加权的比率使用以下公式计算: (color1 * k1 + color2 \* k2) /(k1 + k2)。 加权的比决定后，该方法计算混合的颜色亮度。 它然后乘以通过亮度`dblLumRatio`。 如果值大于 1.0，方法将设置为新值的混合颜色亮度。 否则，亮度是设置为 1.0。  
  
##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated  
 将源给定矩形内的 DC 内容旋转 90 度。  
  
```  
void DrawRotated(
    CRect rectDest,  
    CDC& dcSrc,  
    BOOL bClockWise);
```  
  
### <a name="parameters"></a>参数  
 `rectDest`  
 目标矩形。  
  
 `dcSrc`  
 源设备上下文。  
  
 `bClockWise`  
 `TRUE` 指示旋转 + 90 度;`FALSE`指示旋转-90 度。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
