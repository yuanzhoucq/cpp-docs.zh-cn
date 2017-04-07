---
title: "CDrawingManager 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CDrawingManager class
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
caps.latest.revision: 30
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 53929fff6df57b4e5fe00572f8a7cec8a218c638
ms.lasthandoff: 02/24/2017

---
# <a name="cdrawingmanager-class"></a>CDrawingManager 类
`CDrawingManager`类实现复杂的绘图算法。  
  
## <a name="syntax"></a>语法  
  
```  
class CDrawingManager : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|构造 `CDrawingManager` 对象。|  
|`CDrawingManager::~CDrawingManager`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|创建应用程序可以直接写入一个 32 位与设备无关位图 (DIB)。|  
|[CDrawingManager::DrawAlpha](#drawalpha)|显示具有透明或半透明的像素的位图。|  
|[CDrawingManager::DrawRotated](#drawrotated)|旋转的源 DC 的 + /-90 度的给定矩形内的内容|  
|[CDrawingManager::DrawEllipse](#drawellipse)|绘制一个椭圆使用提供的填充和边框颜色。|  
|[CDrawingManager::DrawGradientRing](#drawgradientring)|绘制一个环，使用颜色渐变填充它。|  
|[CDrawingManager::DrawLine CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|将绘制直线。|  
|[CDrawingManager::DrawRect](#drawrect)|绘制一个具有提供的填充和边框颜色的矩形。|  
|[CDrawingManager::DrawShadow](#drawshadow)|绘制的矩形区域的阴影。|  
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|用两种颜色渐变填充的矩形区域。|  
|[CDrawingManager::FillGradient](#fillgradient)|用指定的颜色渐变填充的矩形区域。|  
|[CDrawingManager::FillGradient2](#fillgradient2)|用指定的颜色渐变填充的矩形区域。 此外指定渐变的颜色变化的方向。|  
|[CDrawingManager::GrayRect](#grayrect)|使用指定的灰颜色填充的矩形。|  
|[CDrawingManager::HighlightRect](#highlightrect)|突出显示的矩形区域。|  
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|将一种颜色从 HLS 表示形式转换为 RGB 表示形式。|  
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|将一种颜色从 HLS 表示形式转换为 RGB 表示形式。|  
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|将一种颜色从 HSV 表示形式转换为 RGB 表示形式。|  
|[CDrawingManager::HuetoRGB](#huetorgb)|将色调值转换为红色、 绿色还是蓝色组件的帮助器方法。|  
|[CDrawingManager::MirrorRect](#mirrorrect)|翻转的矩形区域。|  
|[CDrawingManager::PixelAlpha](#pixelalpha)|确定一个半透明的像素的最终颜色的帮助器方法。|  
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|创建可用作阴影的位图。|  
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|将一种颜色从 RGB 表示形式转换为 HSL 表示形式。|  
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|将一种颜色从 RGB 表示形式转换为 HSV 表示形式。|  
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|颜色部分透明像素位图中的帮助器方法。|  
|[CDrawingManager::SetPixel](#setpixel)|更改为指定的颜色的单像素位图中的帮助器方法。|  
|[CDrawingManager::SmartMixColors](#smartmixcolors)|合并两个颜色根据加权的比率。|  
  
## <a name="remarks"></a>备注  
 `CDrawingManager`类提供用于绘制阴影，颜色渐变和突出显示的矩形的函数。 它还执行 alpha 混合。 此类可用于直接更改应用程序的 UI。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
 `CDrawingManager`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdrawmanager.h  
  
##  <a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager  
 构造[CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)对象。  
  
```  
CDrawingManager(CDC& dc);
```  
  
### <a name="parameters"></a>参数  
 [in] `dc`  
 对设备上下文的引用。 `CDrawingManager`的绘图区域使用此上下文。  
  
##  <a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32  
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
|参数|说明|  
|[in] `size`|一个[CSize](../../atl-mfc-shared/reference/csize-class.md)参数可指示位图的大小。|  
|[out] `pBits`|指向接收 DIB 的位置的数据指针的指针位的值。|  
|`bitmap`|指向原始位图的句柄|  
|`clrTransparent`|一个指定原始位图透明颜色的 RGB 值。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则新创建的 DIB 位图句柄否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 有关如何创建 DIB 位图的详细信息，请参阅[CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183491)。  
  
##  <a name="drawalpha"></a>CDrawingManager::DrawAlpha  
 显示具有透明或半透明的像素的位图。  
  
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
 目标矩形中。  
  
 [in] `pSrcDC`  
 指向源的设备上下文的指针。  
  
 [in] `rectSrc`  
 源矩形中。  
  
### <a name="remarks"></a>备注  
 此方法执行 alpha 混合的两个位图。 Alpha 混合的详细信息，请参阅[AlphaBlend](http://msdn.microsoft.com/library/windows/desktop/dd183351) Windows SDK 中。  
  
##  <a name="drawellipse"></a>CDrawingManager::DrawEllipse  
 绘制一个椭圆使用提供的填充和边框颜色。  
  
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
 此方法用来填充椭圆颜色。  
  
 [in] `clrLine`  
 此方法使用为椭圆的边框颜色。  
  
### <a name="remarks"></a>备注  
 此方法返回不会绘制一个椭圆，如果任意一种颜色设置为-1。 它也会返回不会绘制一个椭圆的边框的任一维度为 0。  
  
##  <a name="drawgradientring"></a>CDrawingManager::DrawGradientRing  
 绘制一个环，使用颜色渐变填充它。  
  
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
 一个[CRect](../../atl-mfc-shared/reference/crect-class.md)参数，用于指定渐变环的边界。  
  
 [in] `colorStart`  
 第一种颜色的渐变。  
  
 [in] `colorFinish`  
 最后一种颜色的渐变。  
  
 [in] `colorBorder`  
 边框的颜色。  
  
 [in] `nAngle`  
 一个参数，指定初始渐变绘制的角度。 此值应介于 0 至 360 之间。  
  
 [in] `nWidth`  
 环的边框的宽度。  
  
 [in] `clrFace`  
 环内部的颜色。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 通过定义的矩形`rect`必须是至少 5 个像素宽和 5 像素高。  
  
##  <a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine CDrawingManager::DrawLineA  
 将绘制直线。  
  
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
|[in] `x1`|行开始的位置的 x 坐标。|  
|[in] `y1`|行开始的位置的 y 坐标。|  
|[in] `x2`|在行的结束位置的 x 坐标。|  
|[in] `y2`|在行的结束位置的 y 坐标。|  
|[in] `clrLine`|线条的颜色。|  
  
### <a name="remarks"></a>备注  
 如果此方法将失败`clrLine`等于-1。  
  
##  <a name="drawrect"></a>CDrawingManager::DrawRect  
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
 此方法用来填充矩形的颜色。  
  
 [in] `clrLine`  
 此方法使用该矩形的边框颜色。  
  
### <a name="remarks"></a>备注  
 此方法返回不会绘制一个矩形，如果任意一种颜色设置为-1。 它还返回的矩形的任一尺寸如果为 0。  
  
##  <a name="drawshadow"></a>CDrawingManager::DrawShadow  
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
 您的应用程序中的矩形区域。 绘制管理器将在此区域的下方绘制阴影。  
  
 [in] `nDepth`  
 宽度和高度的阴影。  
  
 [in] `iMinBrightness`  
 阴影的亮度最小值。  
  
 [in] `iMaxBrightness`  
 最大阴影的亮度。  
  
 [in] `pBmpSaveBottom`  
 一个指向包含此图像可查看阴影的下半部分的位图。  
  
 [in] `pBmpSaveRight`  
 一个指向包含此图像可查看该矩形右侧绘制阴影的位图。  
  
 [in] `clrBase`  
 阴影的颜色。  
  
 [in] `bRightShadow`  
 一个布尔型参数，该值指示如何绘制阴影。 如果`bRightShadow`是`TRUE`，`DrawShadow`矩形右侧绘制阴影。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 可以使用的参数为底端和右侧阴影提供两个有效位图`pBmpSaveBottom`和`pBmpSaveRight`。 如果这些[CBitmap](../../mfc/reference/cbitmap-class.md)对象具有附加的 GDI 对象，`DrawShadow`将使用这些位图作为阴影。 如果`CBitmap`参数没有附加的 GDI 对象，`DrawShadow`绘制阴影，并将这些位图附加到的参数。 在将来对调用`DrawShadow`，您可以提供这些位图来加速绘制过程。 有关详细信息`CBitmap`类和 GDI 对象，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
 如果上述这些参数是`NULL`，`DrawShadow`自动绘制阴影。  
  
 如果您设置`bRightShadow`到`FALSE`，将绘制阴影，下方和矩形区域的左侧。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`DrawShadow`方法`CDrawingManager`类。 此代码段属于[Prop 表演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_PropSheetDemo #&1;](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]  
  
##  <a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient  
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
 初始的第一个颜色渐变的颜色。  
  
 [in] `colorFinish1`  
 第一个颜色渐变的最终颜色。  
  
 [in] `colorStart2`  
 第二个颜色渐变的初始颜色。  
  
 [in] `colorFinish2`  
 第二个颜色渐变的最终颜色。  
  
 [in] `bHorz`  
 一个布尔型参数，该值指示是否`Fill4ColorsGradient`水平或垂直渐变的颜色。 `TRUE`表示水平渐变。  
  
 [in] `nPercentage`  
 从 0 到 100 的整数。 此值指示要使用的第一个颜色渐变填充的矩形的百分比。  
  
### <a name="remarks"></a>备注  
 如果使用两种颜色渐变填充矩形，他们就是上面彼此所在或到对方，具体取决于值的下一步`bHorz`。 使用方法单独计算每种颜色渐变[CDrawingManager::FillGradient](#fillgradient)。  
  
 如果此方法生成断言失败`nPercentage`小于 0 或大于 100。  
  
##  <a name="fillgradient"></a>CDrawingManager::FillGradient  
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
 一个布尔型参数，指定是否`FillGradient`应绘制水平或垂直渐变。  
  
 [in] `nStartFlatPercentage`  
 矩形的百分比，`FillGradient`填充`colorStart`启动渐变之前。  
  
 [in] `nEndFlatPercentage`  
 矩形的百分比，`FillGradient`填充`colorFinish`完成渐变后。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`FillGradient`方法`CDrawingManager`类。 此代码段属于[MS Office 2007 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&12;](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]  
  
##  <a name="fillgradient2"></a>CDrawingManager::FillGradient2  
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
 第一种颜色的渐变。  
  
 [in] `colorFinish`  
 将最后的渐变的颜色。  
  
 [in] `nAngle`  
 一个介于 0 至 360 之间的整数。 此参数指定的颜色渐变的方向。  
  
### <a name="remarks"></a>备注  
 使用`nAngle`指定的颜色渐变的方向。 当您指定的颜色渐变的方向时，您还指定的颜色渐变的开始位置。 值为 0，`nAngle`指示渐变开始按自上而下的矩形。 作为`nAngle`增加，起始位置为渐变会根据角度逆时针方向移动。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`FillGradient2`方法`CDrawingManager`类。 此代码段属于[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&37;](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]  
  
##  <a name="grayrect"></a>CDrawingManager::GrayRect  
 使用指定的灰颜色填充的矩形。  
  
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
 如果此方法使用的重复数据消除饱和度的颜色`nPercentage`设置为-1。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 为参数`nPercentage`，较低的值指示较深的颜色。  
  
 最大值`nPercentage`为 200。 200 个以上更大的值不会更改矩形的外观。 如果值为-1，则此方法使用`clrDisabled`来限制的矩形的饱和度。  
  
##  <a name="highlightrect"></a>CDrawingManager::HighlightRect  
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
 若要突出显示一个矩形区域。  
  
 [in] `nPercentage`  
 一个百分比，指示如何透明度应为突出显示。  
  
 [in] `clrTransparent`  
 透明的颜色。  
  
 [in] `nTolerance`  
 一个介于 0 和 255 之间的整数，指示颜色容差。  
  
 [in] `clrBlend`  
 用于混合基础颜色。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则此方法否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果`nPercentage`介于 0 和 99 之间`HighlightRect`使用 alpha 值混合处理算法。 Alpha 值混合处理的详细信息，请参阅[Alpha 混合线条和填充](http://msdn.microsoft.com/library/5440f48c-3ac9-44c3-b170-c1c110bdbab8)。 如果`nPercentage`为-1，此方法使用默认的突出显示级别。 如果`nPercentage`为 100，此方法不执行任何操作并返回`TRUE`。  
  
 该方法将使用该参数`nTolerance`来确定是否突出显示的矩形区域。 若要突出显示该矩形，您的应用程序的背景色之间的差异和`clrTransparent`必须小于`nTolerance`（红色、 绿色和蓝色） 每个颜色组件中。  
  
##  <a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE  
 将一种颜色从 HLS 表示形式转换为 RGB 表示形式。  
  
```  
static COLORREF __stdcall HLStoRGB_ONE(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>参数  
 [in] `H`  
 介于 0 和 1 之间的数字表示颜色的色调。  
  
 [in] `L`  
 介于 0 和 1 之间的数字表示颜色的亮度。  
  
 [in] `S`  
 介于 0 和 1 之间的数字表示颜色的饱和度。  
  
### <a name="return-value"></a>返回值  
 RGB 颜色的表示形式 HLS 提供。  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 （色调、 饱和度和亮度） 的 HSL 或 RGB （红色、 绿色和蓝色）。 有关的颜色不同的表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/linkid=119126)。  
  
 此方法与`CDrawingManager::HLStoRGB_TWO`方法执行相同的操作，但需要不同的值`H`参数。 在此方法，`H`是指圆的相对百分比。 在`CDrawingManager::HLStoRGB_TWO`方法，`H`是介于 0 至 360，这两个代表红色度数值。 例如，通过使用`HLStoRGB_ONE`，值为 0.25`H`等同于值为 90 与`HLStoRGB_TWO`。  
  
##  <a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO  
 将一种颜色从 HLS 表示形式转换为 RGB 表示形式。  
  
```  
static COLORREF __stdcall HLStoRGB_TWO(
    double H,  
    double L,  
    double S);
```  
  
### <a name="parameters"></a>参数  
 [in] `H`  
 一个介于 0 至 360 之间的数字表示颜色的色调。  
  
 [in] `L`  
 介于 0 和 1 之间的数字表示颜色的亮度。  
  
 [in] `S`  
 介于 0 和 1 之间的数字表示颜色的饱和度。  
  
### <a name="return-value"></a>返回值  
 RGB 颜色的表示形式 HLS 提供。  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 （色调、 饱和度和亮度） 的 HSL 或 RGB （红色、 绿色和蓝色）。 有关的颜色不同的表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/linkid=119126)。  
  
 此方法与[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法执行相同的操作，但需要不同的值`H`参数。 在此方法，`H`是介于 0 至 360，这两个代表红色度数值。 在[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)方法，`H`是指圆的相对百分比。 例如，通过使用`HLStoRGB_ONE`，值为 0.25`H`等同于值为 90 与`HLStoRGB_TWO`。  
  
##  <a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB  
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
|参数|说明|  
|[in] `H`|指示颜色色调介于 0 至 360 数字。|  
|[in] `S`|介于 0 和 1 之间的数字表示颜色的饱和度。|  
|[in] `V`|介于 0 和 1 之间的数字表示颜色的值。|  
  
### <a name="return-value"></a>返回值  
 RGB 颜色的表示形式 HSV 提供。  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 （色调、 饱和度和亮度） 的 HSL 或 RGB （红色、 绿色和蓝色）。 有关的颜色不同的表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/linkid=119126)。  
  
##  <a name="huetorgb"></a>CDrawingManager::HuetoRGB  
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
 提供的色调个别红色、 绿色还是蓝色组件。  
  
### <a name="remarks"></a>备注  
 此方法是一个帮助器方法，`CDrawingManager`类用来计算颜色 HSV 或 HSL 表示形式中的各个红色、 绿色和蓝色组件。 此方法不用于由程序员直接调用。 输入的参数是依赖于转换算法的值。  
  
 若要为 RGB 表示形式转换 HSV 或 HSL 颜色，请调用以下方法之一︰  
  
- [CDrawingManager::HSVtoRGB](#hsvtorgb)  
  
- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)  
  
- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)  
  
##  <a name="mirrorrect"></a>CDrawingManager::MirrorRect  
 翻转的矩形区域。  
  
```  
void MirrorRect(
    CRect rect,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 要反转的区域的边框。  
  
 [in] `bHorz`  
 一个布尔型参数，该值指示该矩形翻转水平或垂直。  
  
### <a name="remarks"></a>备注  
 此方法可反转拥有的设备任何的上下文区域`CDrawingManager`类。 如果`bHorz`设置为`TRUE`，此方法将水平翻转区域。 否则，它垂直翻转区域。  
  
##  <a name="pixelalpha"></a>CDrawingManager::PixelAlpha  
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
 初始像素的颜色。  
  
 [in] `percent`  
 一个介于 0 和 100 之间的数字表示的透明度百分比。 值为 100 指示初始颜色是完全透明。  
  
 [in] `percentR`  
 一个介于 0 和 100 之间的数字表示的红色组件的透明度百分比。  
  
 [in] `percentG`  
 一个介于 0 和 100 之间的数字表示的绿色组件的透明度百分比。  
  
 [in] `percentB`  
 一个介于 0 和 100 之间的数字表示为蓝色成分的透明度百分比。  
  
 [in] `dstPixel`  
 基像素的颜色。  
  
### <a name="return-value"></a>返回值  
 半透明的像素最终颜色。  
  
### <a name="remarks"></a>备注  
 这是用于着色半透明位图的帮助器类，并不设计用于由程序员直接调用。  
  
 如果你使用的方法的具有版本`dstPixel`，最终颜色既有`dstPixel`和`srcPixel`。 `srcPixel`颜色将部分透明的颜色高于基础颜色的`dstPixel`。  
  
##  <a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask  
 创建可用作阴影的位图。  
  
```  
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,  
    COLORREF clrBase,  
    int iMinBrightness = 0,  
    int iMaxBrightness = 100);
```  
  
### <a name="parameters"></a>参数  
 [in] `nDepth`  
 宽度和高度的阴影。  
  
 [in] `clrBase`  
 阴影的颜色。  
  
 [in] `iMinBrightness`  
 阴影的亮度最小值。  
  
 [in] `iMaxBrightness`  
 最大阴影的亮度。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则创建的位图句柄否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 如果`nDepth`是设置为 0，此方法退出并返回`NULL`。 如果`nDepth`小于 3 的宽度和高度的阴影将设置为 3 个像素。  
  
##  <a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL  
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
|参数|说明|  
|[in] `rgb`|RGB 值中的颜色。|  
|[out] `H`|指向一个双精度值，该方法存储颜色色调的位置的指针。|  
|[out] `S`|指向一个双精度值，该方法存储颜色饱和度的位置的指针。|  
|[out] `L`|指向一个双精度值，该方法存储颜色亮度的位置的指针。|  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 （色调、 饱和度和亮度） 的 HSL 或 RGB （红色、 绿色和蓝色）。 有关的颜色不同的表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/linkid=119126)。  
  
 返回的值为`H`表示为介于 0 和 1 其中 0 和 1 表示红色之间的一小部分。 返回的值`S`和`L`是介于 0 和 1 之间的数字。  
  
##  <a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV  
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
 要将 RGB 表示形式中转换的颜色。  
  
 [out] `H`  
 此方法将生成的颜色色调存储的其中一个双精度值指向的指针。  
  
 [out] `S`  
 指向一个双精度值，此方法存储生成的颜色饱和度的位置的指针。  
  
 [out] `V`  
 指向一个双精度值，此方法存储生成的值的颜色的位置的指针。  
  
### <a name="remarks"></a>备注  
 一种颜色可以表示为 HSV （色调、 饱和度和值）、 （色调、 饱和度和亮度） 的 HSL 或 RGB （红色、 绿色和蓝色）。 有关的颜色不同的表示形式的详细信息，请参阅[颜色](http://go.microsoft.com/fwlink/linkid=119126)。  
  
 返回的值为`H`是介于 0 至 360 之间的数字 0 至 360 在这里指明红色。 返回值`S`和`V`是介于 0 和 1 之间的数字。  
  
##  <a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel  
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
 [in] `pBits`  
 指向位图的位值的指针。  
  
 [in] `rect`  
 您的应用程序中的矩形区域。 绘制 manager 绘制阴影，下方和右侧的此区域。  
  
 [in] `x`  
 水平坐标的像素颜色。  
  
 [in] `y`  
 垂直坐标的像素颜色。  
  
 [in] `percent`  
 透明度百分比。  
  
 [in] `iShadowSize`  
 宽度和高度的阴影。  
  
 [in] `clrBase`  
 阴影的颜色。  
  
 [in] `bIsRight`  
 一个布尔型参数，该值指示对颜色的像素。 有关详细信息，请参阅备注部分。  
  
### <a name="remarks"></a>备注  
 此方法是使用一个帮助器方法[CDrawingManager::DrawShadow](#drawshadow)方法。 我们建议，如果您想要的位置绘制阴影，调用`CDrawingManager::DrawShadow`相反。  
  
 如果`bIsRight`设置为`TRUE`，为颜色的像素为单位`x`的右边缘的像素`rect`。 如果它是`FALSE`，为颜色的像素为单位`x`像素从左边缘`rect`。  
  
##  <a name="setpixel"></a>CDrawingManager::SetPixel  
 为指定的颜色更改位图中的单一像素。  
  
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
|[in] `pBits`|指向位图的位值的指针。|  
|[in] `cx`|位图的总宽度。|  
|[in] `cy`|位图的总高度。|  
|[in] `x`|要更改的位图的像素 x 坐标。|  
|[in] `y`|要更改的位图的像素 y 坐标。|  
|[in] `color`|标识由坐标的像素新颜色。|  
  
##  <a name="smartmixcolors"></a>CDrawingManager::SmartMixColors  
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
|参数|说明|  
|[in] `color1`|第一种颜色混合。|  
|[in] `color2`|要组合的第二个颜色。|  
|[in] `dblLumRatio`|新颜色的亮度率。 `SmartMixColors`在确定最终颜色之前乘以此比率的混合颜色的亮度。|  
|[in] `k1`|第一种颜色的加权的率。|  
|[in] `k2`|第二种颜色的加权的率。|  
  
### <a name="return-value"></a>返回值  
 表示为加权的混合提供色的颜色。  
  
### <a name="remarks"></a>备注  
 此方法将失败并出现错误，如果任一`k1`或`k2`也不可小于零。 如果上述这些参数将设置为 0，该方法返回`RGB(0, 0, 0)`。  
  
 加权的比率使用以下公式计算: (color1 * 版 k1 + color2 \* k2) /(k1 + k2)。 加权的比决定之后，该方法计算混合的颜色的亮度。 然后将相乘的亮度`dblLumRatio`。 如果值大于 1.0，方法将设置为新值的混合颜色的亮度。 否则，亮度设置为 1.0。  
  
##  <a name="drawrotated"></a>CDrawingManager::DrawRotated  
 源 DC 在给定的矩形内的内容旋转 90 度。  
  
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
 `TRUE`指示旋转 +&90; 度。`FALSE`指示旋转-90 度。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

