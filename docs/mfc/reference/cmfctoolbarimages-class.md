---
title: "CMFCToolBarImages 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarImages
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarImages class
ms.assetid: d4e50518-9ffc-406f-9996-f79e5cd38155
caps.latest.revision: 31
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
ms.openlocfilehash: ff94497108033b17d52b79594fdbe30e8ed7da03
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarimages-class"></a>CMFCToolBarImages 类
在工具栏上的图像。 `CMFCToolBarImages`类管理从应用程序资源或从文件加载的工具栏图像。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarImages : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarImages::CMFCToolBarImages](#cmfctoolbarimages)|构造 `CMFCToolBarImages` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarImages::AdaptColors](#adaptcolors)||  
|[CMFCToolBarImages::AddIcon](#addicon)|将图标添加到工具栏图像。|  
|[CMFCToolBarImages::AddImage](#addimage)|将位图添加到工具栏图像。|  
|[CMFCToolBarImages::CleanUp](#cleanup)||  
|[CMFCToolBarImages::Clear](#clear)|释放已分配给此对象的系统资源。|  
|[CMFCToolBarImages::ConvertTo32Bits](#convertto32bits)|转换为它添加下划线为 32 bpp 图像的位图。|  
|[CMFCToolBarImages::CopyImageToClipboard](#copyimagetoclipboard)||  
|[CMFCToolBarImages::CopyTo](#copyto)||  
|[CMFCToolBarImages::CreateFromImageList](#createfromimagelist)|初始化从图像列表的工具栏图像 ( [CImageList 类](../../mfc/reference/cimagelist-class.md))。|  
|[CMFCToolBarImages::CreateRegionFromImage](#createregionfromimage)||  
|[CMFCToolBarImages::DeleteImage](#deleteimage)|删除已从工具栏图像的指定的索引，如果此集的工具栏图像包含用户定义的图像的图像。|  
|[CMFCToolBarImages::Draw](#draw)|绘制一个工具栏上的图像 （按钮）。|  
|[CMFCToolBarImages::DrawEx](#drawex)||  
|[CMFCToolBarImages::EnableRTL](#enablertl)||  
|[CMFCToolBarImages::EndDrawImage](#enddrawimage)|在绘制的工具栏图像之后可释放系统资源。|  
|[CMFCToolBarImages::ExtractIcon](#extracticon)|返回具有指定的图像索引从工具栏图像的图标。|  
|[CMFCToolBarImages::FillDitheredRect](#fillditheredrect)|通过使用具有工具栏背景色的画笔填充的矩形。|  
|[CMFCToolBarImages::GetAlwaysLight](#getalwayslight)||  
|[CMFCToolBarImages::GetBitsPerPixel](#getbitsperpixel)|返回当前分辨率的带下划线的映像。|  
|[CMFCToolBarImages::GetCount](#getcount)|返回在工具栏上的映像数量。|  
|[CMFCToolBarImages::GetDisabledImageAlpha](#getdisabledimagealpha)|返回用于禁用图像的 alpha 通道值。|  
|[CMFCToolBarImages::GetFadedImageAlpha](#getfadedimagealpha)||  
|[CMFCToolBarImages::GetImageSize](#getimagesize)|检索存储在内存 （源大小） 中的工具栏图像的大小或在 （目标大小） 屏幕绘制的工具栏图像的大小。|  
|[CMFCToolBarImages::GetImageWell](#getimagewell)|返回包含所有的工具栏图像的位图句柄。|  
|[CMFCToolBarImages::GetImageWellLight](#getimagewelllight)||  
|[CMFCToolBarImages::GetLastImageRect](#getlastimagerect)||  
|[CMFCToolBarImages::GetLightPercentage](#getlightpercentage)||  
|[CMFCToolBarImages::GetMapTo3DColors](#getmapto3dcolors)||  
|[CMFCToolBarImages::GetMask](#getmask)||  
|[CMFCToolBarImages::GetResourceOffset](#getresourceoffset)|返回指定的资源 id 的图像索引|  
|[CMFCToolBarImages::GetScale](#getscale)|返回当前的缩放比率的带下划线的映像。|  
|[CMFCToolBarImages::GetTransparentColor](#gettransparentcolor)||  
|[CMFCToolBarImages::GrayImages](#grayimages)|用灰色工具栏图像，使其看起来已禁用。|  
|[CMFCToolBarImages::Is32BitTransparencySupported](#is32bittransparencysupported)|确定操作系统是否支持 32 位 alpha 值混合处理。|  
|[CMFCToolBarImages::IsPreMultiplyAutoCheck](#ispremultiplyautocheck)||  
|[CMFCToolBarImages::IsRTL](#isrtl)|确定是否启用从右到左 (RTL) 支持。|  
|[CMFCToolBarImages::IsReadOnly](#isreadonly)|确定工具栏图像都是只读的。|  
|[CMFCToolBarImages::IsScaled](#isscaled)|指示是否对带下划线的图像缩放。|  
|[CMFCToolBarImages::IsUserImagesList](#isuserimageslist)|确定此集的工具栏图像是否包含用户定义的图像。|  
|[CMFCToolBarImages::IsValid](#isvalid)|确定此集的工具栏图像是否包含有效的工具栏图像。|  
|[CMFCToolBarImages::Load](#load)|与系统资源或从文件加载的工具栏图像。|  
|[CMFCToolBarImages::LoadStr](#loadstr)||  
|[CMFCToolBarImages::MapFromSysColor](#mapfromsyscolor)||  
|[CMFCToolBarImages::MapTo3dColors](#mapto3dcolors)||  
|[CMFCToolBarImages::MapToSysColor](#maptosyscolor)||  
|[CMFCToolBarImages::MapToSysColorAlpha](#maptosyscoloralpha)||  
|[CMFCToolBarImages::Mirror](#mirror)|水平反映所有的工具栏图像。|  
|[CMFCToolBarImages::MirrorBitmap](#mirrorbitmap)|水平镜像位图。|  
|[CMFCToolBarImages::MirrorBitmapVert](#mirrorbitmapvert)||  
|[CMFCToolBarImages::MirrorVert](#mirrorvert)||  
|[CMFCToolBarImages::OnSysColorChange](#onsyscolorchange)||  
|[CMFCToolBarImages::PrepareDrawImage](#preparedrawimage)|分配指定大小绘制的工具栏图像所需的资源。|  
|[CMFCToolBarImages::Save](#save)|将工具栏图像存储在文件中，如果此集的工具栏图像包含用户定义的图像。|  
|[CMFCToolBarImages::SetAlwaysLight](#setalwayslight)||  
|[CMFCToolBarImages::SetDisabledImageAlpha](#setdisabledimagealpha)|设置用于禁用图像的 alpha 通道值。|  
|[CMFCToolBarImages::SetFadedImageAlpha](#setfadedimagealpha)||  
|[CMFCToolBarImages::SetImageSize](#setimagesize)|设置的工具栏图像 （源大小） 的大小。|  
|[CMFCToolBarImages::SetLightPercentage](#setlightpercentage)||  
|[CMFCToolBarImages::SetMapTo3DColors](#setmapto3dcolors)||  
|[CMFCToolBarImages::SetPreMultiplyAutoCheck](#setpremultiplyautocheck)||  
|[CMFCToolBarImages::SetSingleImage](#setsingleimage)||  
|[CMFCToolBarImages::SetTransparentColor](#settransparentcolor)|设置的工具栏图像的透明色。|  
|[CMFCToolBarImages::SmoothResize](#smoothresize)|顺利地调整带下划线的图像的大小。|  
|[CMFCToolBarImages::UpdateImage](#updateimage)|更新从位图的用户定义的工具栏图像。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarImages::PreMultiplyAlpha](#premultiplyalpha)||  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarImages::m_bDisableTrueColorAlpha](#m_bdisabletruecoloralpha)|`TRUE`如果禁用了真彩色 alpha 值混合处理 （32 位颜色）。|  
  
## <a name="remarks"></a>备注  
 由管理的工具栏图像的完整位图`CMFCToolbarImages`包含，它具有固定大小的一个或多个小型的工具栏图像 （按钮）。  
  
## <a name="example"></a>示例  
 下面的示例演示如何配置`CMFCToolBarImages`使用中的各种方法的对象`CMFCToolBarImages`类。 该示例演示如何设置的工具栏图像大小，加载图像，并设置图像的透明色。 此代码段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&32;](../../mfc/codesnippet/cpp/cmfctoolbarimages-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo 第&33;](../../mfc/codesnippet/cpp/cmfctoolbarimages-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCToolBarImages`   
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbarimages.h  
  
##  <a name="a-nameadaptcolorsa--cmfctoolbarimagesadaptcolors"></a><a name="adaptcolors"></a>CMFCToolBarImages::AdaptColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AdaptColors(
    COLORREF clrBase,  
    COLORREF clrTone);
```  
  
### <a name="parameters"></a>参数  
 [in] `clrBase`  
 [in] `clrTone`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddicona--cmfctoolbarimagesaddicon"></a><a name="addicon"></a>CMFCToolBarImages::AddIcon  
 将图标添加到列表中的工具栏图像。  
  
```  
int AddIcon(
    HICON hIcon,  
    BOOL bAlphaBlend=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `hIcon`  
 指向要添加的图标的句柄。  
  
 [in] `bAlphaBlend`  
 `TRUE`如果使用 alpha 值混合处理; 使用此图标否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则已添加的工具栏图像的从零开始的索引否则为-1。  
  
##  <a name="a-nameaddimagea--cmfctoolbarimagesaddimage"></a><a name="addimage"></a>CMFCToolBarImages::AddImage  
 将位图添加到工具栏图像。  
  
```  
int AddImage(
    HBITMAP hbmp,  
    BOOL bSetBitPerPixel=FALSE);

int AddImage(
    const CMFCToolBarImages& imageList,  
    int nIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `hbmp`  
 要添加的位图句柄。  
  
 [in] `bSetBitPerPixel`  
 `TRUE`如果`CMFCToolBarImages`对象使用的新映像; 的颜色深度 （位 / 像素）`FALSE`如果`CMFCToolbarImages`对象会保留当前的颜色深度。  
  
 [in] `imageList`  
 对引用`CMFCToolbarImages`对象，其中包含要添加的图像。  
  
 [in] `nIndex`  
 源中的索引`CMFCToolbarImages`对象要添加的图像。  
  
### <a name="return-value"></a>返回值  
 许多 toolbar 映像`CMFCToolBarImages`对象维护成功，则添加新位图后如果操作失败，则为-1。  
  
##  <a name="a-namecleanupa--cmfctoolbarimagescleanup"></a><a name="cleanup"></a>CMFCToolBarImages::CleanUp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall CleanUp();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namecleara--cmfctoolbarimagesclear"></a><a name="clear"></a>CMFCToolBarImages::Clear  
 释放系统资源， [CMFCToolbarImages](../../mfc/reference/cmfctoolbarimages-class.md)分配的对象。  
  
```  
void Clear();
```  
  
##  <a name="a-namecmfctoolbarimagesa--cmfctoolbarimagescmfctoolbarimages"></a><a name="cmfctoolbarimages"></a>CMFCToolBarImages::CMFCToolBarImages  
 构造 `CMFCToolBarImages` 对象。  
  
```  
CMFCToolBarImages();
```  
  
### <a name="remarks"></a>备注  
 构造`CMFCToolBarImages`对象，初始化它呈现引擎并将图像大小设置为其默认值 16 x 15 像素。 使用[CMFCToolBarImages::SetImageSize](#setimagesize)若要更改的图像的大小，然后添加图像。  
  
##  <a name="a-namecopyimagetoclipboarda--cmfctoolbarimagescopyimagetoclipboard"></a><a name="copyimagetoclipboard"></a>CMFCToolBarImages::CopyImageToClipboard  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyImageToClipboard(int iImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `iImage`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namecopytoa--cmfctoolbarimagescopyto"></a><a name="copyto"></a>CMFCToolBarImages::CopyTo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyTo(CMFCToolBarImages& imageList);
```  
  
### <a name="parameters"></a>参数  
 [in] `imageList`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namecreatefromimagelista--cmfctoolbarimagescreatefromimagelist"></a><a name="createfromimagelist"></a>CMFCToolBarImages::CreateFromImageList  
 初始化中的工具栏图像[CImageList 类](../../mfc/reference/cimagelist-class.md)对象。  
  
```  
BOOL CreateFromImageList(const CImageList& imageList);
```  
  
### <a name="parameters"></a>参数  
 [in] `imageList`  
 要用作源的工具栏图像的图像列表。  
  
### <a name="return-value"></a>返回值  
 始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 使用此函数来快速初始化外部图像列表中的工具栏图像列表。  
  
##  <a name="a-namecreateregionfromimagea--cmfctoolbarimagescreateregionfromimage"></a><a name="createregionfromimage"></a>CMFCToolBarImages::CreateRegionFromImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static HRGN __stdcall CreateRegionFromImage(
    HBITMAP bmp,  
    COLORREF clrTransparent);
```  
  
### <a name="parameters"></a>参数  
 [in] `bmp`  
 [in] `clrTransparent`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namedeleteimagea--cmfctoolbarimagesdeleteimage"></a><a name="deleteimage"></a>CMFCToolBarImages::DeleteImage  
 删除具有指定的索引的工具栏图像的用户定义的图像。  
  
```  
BOOL DeleteImage(int iImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `iImage`  
 指定要删除的图像的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果映像已成功，则删除`FALSE`的图像索引是无效的如果`CMFCToolbarImages`对象是临时的`CMFCToolbarImages`对象不包含用户定义的图像，或者如果某一其他出现错误。  
  
##  <a name="a-namedrawa--cmfctoolbarimagesdraw"></a><a name="draw"></a>CMFCToolBarImages::Draw  
 绘制一个工具栏上的图像。  
  
```  
BOOL Draw(
    CDC* pDC,  
    int x,  
    int y,  
    int iImageIndex,  
    BOOL bHilite=FALSE,  
    BOOL bDisabled=FALSE,  
    BOOL bIndeterminate=FALSE,  
    BOOL bShadow=FALSE,  
    BOOL bInactive=FALSE,  
    BYTE alphaSrc=255);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `x`  
 要绘制图像的位置的矩形的左侧的 X 坐标。  
  
 [in] `y`  
 要绘制图像的位置的矩形的顶部的 Y 坐标。  
  
 [in] `iImageIndex`  
 要显示的图像的从零开始的索引。  
  
 [in] `bHilite`  
 `TRUE`如果图像是要突出显示;否则为`FALSE`。  
  
 [in] `bDisabled`  
 `TRUE`如果要在已禁用的样式; 中绘制的图像否则为`FALSE`。  
  
 [in] `bIndeterminate`  
 `TRUE`如果要在不确定状态样式中; 中绘制的图像否则为`FALSE`。  
  
 [in] `bShadow`  
 `TRUE`如果使用投影，则绘制的图像否则为`FALSE`。  
  
 [in] `bInactive`  
 `TRUE`如果在处于非活动状态样式中; 中绘制的图像否则为`FALSE`。  
  
 [in] `alphaSrc`  
 Alpha 通道 (opacity) 值中。 值为 255 意味着图像是绘制不透明。 值为 0 表示图像绘制透明。 仅对于 32 位彩色图像和显示 Windows Vista 玻璃样式的映像，使用此值。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则显示了指定的图像`FALSE`如果图像索引已无效，或出现了其他错误。  
  
##  <a name="a-namedrawexa--cmfctoolbarimagesdrawex"></a><a name="drawex"></a>CMFCToolBarImages::DrawEx  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL DrawEx(
    CDC* pDC,  
    CRect rect,  
    int iImageIndex,  
    ImageAlignHorz horzAlign = ImageAlignHorzLeft,  
    ImageAlignVert vertAlign = ImageAlignVertTop,  
    CRect rectSrc = CRect(0,
    0,
    0,
    0),  
    BYTE alphaSrc = 255);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 [in] `rect`  
 [in] `iImageIndex`  
 [in] `horzAlign`  
 [in] `vertAlign`  
 [in] `rectSrc`  
 [in] `0`  
 [in] `0)`  
 [in] `alphaSrc`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameenablertla--cmfctoolbarimagesenablertl"></a><a name="enablertl"></a>CMFCToolBarImages::EnableRTL  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall EnableRTL(BOOL bIsRTL = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsRTL`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameenddrawimagea--cmfctoolbarimagesenddrawimage"></a><a name="enddrawimage"></a>CMFCToolBarImages::EndDrawImage  
 释放系统资源， [CMFCToolBarImages::PrepareDrawImage](#preparedrawimage)后通过调用绘制的工具栏图像分配[CMFCToolBarImages::Draw](#draw)。  
  
```  
void EndDrawImage(CAfxDrawState& ds);
```  
  
### <a name="parameters"></a>参数  
 [in] `ds`  
 对引用`CAfxDrawState`对象传递给`PrepareDrawImage`方法。  
  
##  <a name="a-nameextracticona--cmfctoolbarimagesextracticon"></a><a name="extracticon"></a>CMFCToolBarImages::ExtractIcon  
 返回具有指定的图像索引从工具栏图像的图标。  
  
```  
HICON ExtractIcon(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 要提取为图标的图像的图像列表中的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 提取图标的句柄或`NULL`如果`nIndex`超出范围。  
  
##  <a name="a-namefillditheredrecta--cmfctoolbarimagesfillditheredrect"></a><a name="fillditheredrect"></a>CMFCToolBarImages::FillDitheredRect  
 与工具栏背景色填充的矩形。  
  
```  
static void FillDitheredRect(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 若要填充的矩形的坐标。  
  
### <a name="remarks"></a>备注  
 使用此方法使用的系统颜色 COLOR_BTNFACE 和 COLOR_BTNHIGHLIGHT 的平均值的颜色填充矩形。 如果系统正在使用 256 色或更少的颜色，将填充该矩形与这两种颜色的抖动模式。  
  
##  <a name="a-namegetalwayslighta--cmfctoolbarimagesgetalwayslight"></a><a name="getalwayslight"></a>CMFCToolBarImages::GetAlwaysLight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetAlwaysLight() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetcounta--cmfctoolbarimagesgetcount"></a><a name="getcount"></a>CMFCToolBarImages::GetCount  
 在工具栏上的图像列表中返回映像的数量。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 中的图像数`CMFCToolBarImages`对象。  
  
##  <a name="a-namegetdisabledimagealphaa--cmfctoolbarimagesgetdisabledimagealpha"></a><a name="getdisabledimagealpha"></a>CMFCToolBarImages::GetDisabledImageAlpha  
 返回用于禁用图像的 alpha 通道 (opacity) 值。  
  
```  
static BYTE GetDisabledImageAlpha();
```  
  
### <a name="return-value"></a>返回值  
 当前的 alpha 通道值。  
  
### <a name="remarks"></a>备注  
 您可以调用[CMFCToolBarImages::SetDisabledImageAlpha](#setdisabledimagealpha)若要更改的 alpha 通道值。  
  
##  <a name="a-namegetfadedimagealphaa--cmfctoolbarimagesgetfadedimagealpha"></a><a name="getfadedimagealpha"></a>CMFCToolBarImages::GetFadedImageAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BYTE __stdcall GetFadedImageAlpha();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetimagesizea--cmfctoolbarimagesgetimagesize"></a><a name="getimagesize"></a>CMFCToolBarImages::GetImageSize  
 检索存储在内存 （源大小） 中的工具栏图像的大小或在 （目标大小） 屏幕绘制的工具栏图像的大小。  
  
```  
SIZE GetImageSize(BOOL bDest=FALSE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bDest`  
 `TRUE`若要检索的目标大小;`FALSE`以检索源图像大小。  
  
### <a name="return-value"></a>返回值  
 一个`SIZE`结构，以像素为单位指定映像的大小。  
  
### <a name="remarks"></a>备注  
 源映像的大小是存储在图像的大小[CMFCToolbarImages](../../mfc/reference/cmfctoolbarimages-class.md)对象。 您可以调用[CMFCToolBarImages::SetImageSize](#setimagesize)设置源的大小。 默认值为 16 x 15 像素。  
  
 默认情况下，目标映像大小为 0x0。 在调用时指定的目标大小[CMFCToolBarImages::PrepareDrawImage](#preparedrawimage)。 [CMFCToolBarImages::EndDrawImage](#enddrawimage)方法重置为默认值的目标大小。  
  
##  <a name="a-namegetimagewella--cmfctoolbarimagesgetimagewell"></a><a name="getimagewell"></a>CMFCToolBarImages::GetImageWell  
 返回包含所有的工具栏图像的位图句柄。  
  
```  
HBITMAP GetImageWell() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向包含的工具栏图像的位图的句柄。  
  
### <a name="remarks"></a>备注  
 工具栏图像存储在名为在单个位图中的行*image well — 图像*。 若要查找图像良好的工具栏图像，乘以的图像的索引的工具栏图像的宽度 (请参阅[CMFCToolBarImages::GetImageSize](#getimagesize)) 也获取映像内的图像的水平偏移量。  
  
##  <a name="a-namegetimagewelllighta--cmfctoolbarimagesgetimagewelllight"></a><a name="getimagewelllight"></a>CMFCToolBarImages::GetImageWellLight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
HBITMAP GetImageWellLight() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetlastimagerecta--cmfctoolbarimagesgetlastimagerect"></a><a name="getlastimagerect"></a>CMFCToolBarImages::GetLastImageRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetLastImageRect() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetlightpercentagea--cmfctoolbarimagesgetlightpercentage"></a><a name="getlightpercentage"></a>CMFCToolBarImages::GetLightPercentage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetLightPercentage() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetmapto3dcolorsa--cmfctoolbarimagesgetmapto3dcolors"></a><a name="getmapto3dcolors"></a>CMFCToolBarImages::GetMapTo3DColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetMapTo3DColors() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetmaska--cmfctoolbarimagesgetmask"></a><a name="getmask"></a>CMFCToolBarImages::GetMask  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
HBITMAP GetMask(int iImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `iImage`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetresourceoffseta--cmfctoolbarimagesgetresourceoffset"></a><a name="getresourceoffset"></a>CMFCToolBarImages::GetResourceOffset  
 返回指定的资源 id 的图像索引  
  
```  
int GetResourceOffset(UINT uiResId) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiResId`  
 图像资源 id。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则图像索引如果不存在具有指定的资源 ID 的图像，则为-1。  
  
##  <a name="a-namegettransparentcolora--cmfctoolbarimagesgettransparentcolor"></a><a name="gettransparentcolor"></a>CMFCToolBarImages::GetTransparentColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
COLORREF GetTransparentColor() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegrayimagesa--cmfctoolbarimagesgrayimages"></a><a name="grayimages"></a>CMFCToolBarImages::GrayImages  
 用灰色工具栏图像，使其看起来已禁用。  
  
```  
BOOL GrayImages(int nGrayImageLuminancePercentage);
```  
  
### <a name="parameters"></a>参数  
 [in] `nGrayImageLuminancePercentage`  
 亮度百分比。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则集合中的图像已显示为灰色否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法通过求平均值的每个像素的红色、 绿色和蓝色组件并相乘的结果来修改工具栏图像`nGrayImageLuminancePercentage`除以 100。 如果`nGrayImageLuminancePercentage`为零或负数，130 的默认值改用。  
  
> [!NOTE]
>  如果您想要撤消所做更改，您必须从源映像重新加载。 你可以通过调用[CMFCToolBarImages::Load](#load)或[CMFCToolBarImages::UpdateImage](#updateimage) （仅适用于用户定义的图像），或通过调用[CMFCToolBarImages::Clear](#clear) ，将映像重新添加通过调用[CMFCToolBarImages::AddIcon](#addicon)或[CMFCToolBarImages::AddImage](#addimage)。  
  
##  <a name="a-nameis32bittransparencysupporteda--cmfctoolbarimagesis32bittransparencysupported"></a><a name="is32bittransparencysupported"></a>CMFCToolBarImages::Is32BitTransparencySupported  
 指定操作系统是否支持 32 位 alpha 值混合处理。  
  
```  
static BOOL Is32BitTransparencySupported();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果支持 32 位 alpha 值混合处理，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此静态方法用于在运行时确定操作系统是否支持 32 位 alpha 值混合处理。 上均支持此功能[!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)]及更高版本。  
  
##  <a name="a-nameispremultiplyautochecka--cmfctoolbarimagesispremultiplyautocheck"></a><a name="ispremultiplyautocheck"></a>CMFCToolBarImages::IsPreMultiplyAutoCheck  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsPreMultiplyAutoCheck() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisreadonlya--cmfctoolbarimagesisreadonly"></a><a name="isreadonly"></a>CMFCToolBarImages::IsReadOnly  
 指定工具栏图像都是只读的。  
  
```  
BOOL IsReadOnly() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果工具栏图像是只读的否则`FALSE`。  
  
### <a name="remarks"></a>备注  
 `CMFCToolbarImages`对象是只读的当从只读文件，已加载的工具栏图像的位图或位图被复制到使用`CMFCToolBarImages::CopyTemp`方法。  
  
##  <a name="a-nameisrtla--cmfctoolbarimagesisrtl"></a><a name="isrtl"></a>CMFCToolBarImages::IsRTL  
 指定是否启用从右到左 (RTL) 支持。  
  
```  
static BOOL IsRTL();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果启用了 RTL 支持;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 应用程序本地化为一种语言，从右到左，如阿拉伯语、 希伯来语、 波斯语或乌尔都语读取时，将使用 RTL 支持。  
  
##  <a name="a-nameisuserimageslista--cmfctoolbarimagesisuserimageslist"></a><a name="isuserimageslist"></a>CMFCToolBarImages::IsUserImagesList  
 指定的工具栏图像此集是否包含用户定义的图像。  
  
```  
BOOL IsUserImagesList() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`CMFCToolBarImages`对象包含用户定义的工具栏图像; 否则为`FALSE`。  
  
##  <a name="a-nameisvalida--cmfctoolbarimagesisvalid"></a><a name="isvalid"></a>CMFCToolBarImages::IsValid  
 指示的工具栏图像此集是否包含有效的工具栏图像。  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`CMFCToolBarImages`对象是有效的; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `CMFCToolBarImages`对象不是有效的工具栏图像的位图的句柄时`NULL`。  
  
##  <a name="a-nameloada--cmfctoolbarimagesload"></a><a name="load"></a>CMFCToolBarImages::Load  
 与系统资源或从文件加载的工具栏图像。  
  
```  
BOOL Load(
    UINT uiResID,  
    HINSTANCE hinstRes=NULL,  
    BOOL bAdd=FALSE);

BOOL Load(
    LPCTSTR lpszBmpFileName,   
    DWORD nMaxFileSize = 819200);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiResID`  
 位图资源的 ID。  
  
 [in] `hinstRes`  
 资源 DLL 的一个实例。  
  
 [in] `bAdd`  
 `TRUE`若要将加载的位图添加到现有的位图或`FALSE`来替换现有的位图。  
  
 [in] `lpszBmpFileName`  
 要从其中加载位图磁盘文件的路径。  
  
 [in] `nMaxFileSize`  
 最大位图文件中; 中的字节数或 0，则加载而不考虑文件大小的位图。 如果文件的大小超过此最大大小，则此方法返回`FALSE`并不会加载位图。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则加载位图否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果该文件具有只读属性，以只读方式标记的图像列表。  
  
##  <a name="a-nameloadstra--cmfctoolbarimagesloadstr"></a><a name="loadstr"></a>CMFCToolBarImages::LoadStr  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL LoadStr(
    LPCTSTR lpszResourceName,  
    HINSTANCE hinstRes = NULL,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszResourceName`  
 [in] `hinstRes`  
 [in] `bAdd`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namemapfromsyscolora--cmfctoolbarimagesmapfromsyscolor"></a><a name="mapfromsyscolor"></a>CMFCToolBarImages::MapFromSysColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static COLORREF __stdcall MapFromSysColor(
    COLORREF color,  
    BOOL bUseRGBQUAD = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 [in] `bUseRGBQUAD`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namemapto3dcolorsa--cmfctoolbarimagesmapto3dcolors"></a><a name="mapto3dcolors"></a>CMFCToolBarImages::MapTo3dColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL MapTo3dColors(
    BOOL bUseRGBQUAD = TRUE,  
    COLORREF clrSrc = (COLORREF)-1,  
    COLORREF clrDest = (COLORREF)-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `bUseRGBQUAD`  
 [in] `clrSrc`  
 [in] `clrDest`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namemaptosyscolora--cmfctoolbarimagesmaptosyscolor"></a><a name="maptosyscolor"></a>CMFCToolBarImages::MapToSysColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static COLORREF __stdcall MapToSysColor(
    COLORREF color,  
    BOOL bUseRGBQUAD = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 [in] `bUseRGBQUAD`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namemaptosyscoloralphaa--cmfctoolbarimagesmaptosyscoloralpha"></a><a name="maptosyscoloralpha"></a>CMFCToolBarImages::MapToSysColorAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static COLORREF __stdcall MapToSysColorAlpha(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namemirrora--cmfctoolbarimagesmirror"></a><a name="mirror"></a>CMFCToolBarImages::Mirror  
 替换其水平的镜像图像的工具栏图像。  
  
```  
BOOL Mirror();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果映像已成功镜像;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法用于支持从右到左书写系统。  
  
##  <a name="a-namemirrorbitmapa--cmfctoolbarimagesmirrorbitmap"></a><a name="mirrorbitmap"></a>CMFCToolBarImages::MirrorBitmap  
 替换其水平的镜像图像的位图。  
  
```  
static BOOL MirrorBitmap(
    HBITMAP& hbmp,  
    int cxImage);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `hbmp`  
 若要镜像的位图句柄。  
  
 [in] `cxImage`  
 以像素为单位图像的宽度。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果映像已成功进行镜像;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此函数用于支持从右到左书写系统。  
  
##  <a name="a-namemirrorbitmapverta--cmfctoolbarimagesmirrorbitmapvert"></a><a name="mirrorbitmapvert"></a>CMFCToolBarImages::MirrorBitmapVert  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall MirrorBitmapVert(
    HBITMAP& hbmp,  
    int cyImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `hbmp`  
 [in] `cyImage`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namemirrorverta--cmfctoolbarimagesmirrorvert"></a><a name="mirrorvert"></a>CMFCToolBarImages::MirrorVert  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL MirrorVert();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonsyscolorchangea--cmfctoolbarimagesonsyscolorchange"></a><a name="onsyscolorchange"></a>CMFCToolBarImages::OnSysColorChange  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void OnSysColorChange();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namepremultiplyalphaa--cmfctoolbarimagespremultiplyalpha"></a><a name="premultiplyalpha"></a>CMFCToolBarImages::PreMultiplyAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall PreMultiplyAlpha(
    HBITMAP hbmp,  
    BOOL bAutoCheckPremlt);

BOOL PreMultiplyAlpha(HBITMAP hbmp);
```  
  
### <a name="parameters"></a>参数  
 [in] `hbmp`  
 [in] `bAutoCheckPremlt`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namembdisabletruecoloralphaa--cmfctoolbarimagesmbdisabletruecoloralpha"></a><a name="m_bdisabletruecoloralpha"></a>CMFCToolBarImages::m_bDisableTrueColorAlpha  
 `TRUE`如果禁用了真彩色 alpha 值混合处理 （32 位颜色）。  
  
```  
static BOOL m_bDisableTrueColorAlpha;  
```  
  
### <a name="remarks"></a>备注  
 此成员变量设置为`FALSE`若要启用真彩色 alpha 混合的工具栏图像。  
  
 默认值是`TRUE`为了向后兼容。  
  
##  <a name="a-namepreparedrawimagea--cmfctoolbarimagespreparedrawimage"></a><a name="preparedrawimage"></a>CMFCToolBarImages::PrepareDrawImage  
 分配指定大小绘制的工具栏图像所需的资源。  
  
```  
BOOL PrepareDrawImage(
    CAfxDrawState& ds,  
    CSize sizeImageDest=CSize(0,
    0)  
    BOOL bFadeInactive=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `ds`  
 对引用`CAfxDrawState`结构，它将存储图像呈现阶段之间分配的资源。  
  
 [in] `sizeImageDest`  
 指定目标图像的大小。  
  
 [in] `bFadeInactive`  
 `TRUE`如果您想要停用图像绘制成淡化。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果要绘制的工具栏图像所需的资源所分配成功，否则`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法后，您可以调用[CMFCToolBarImages::Draw](#draw)任意次数。 完成绘制后，必须调用[CMFCToolBarImages::EndDrawImage](#enddrawimage)以释放资源由分配`PrepareDrawImage`。  
  
##  <a name="a-namesavea--cmfctoolbarimagessave"></a><a name="save"></a>CMFCToolBarImages::Save  
 将工具栏图像存储在文件中，如果此集的工具栏图像包含用户定义的图像。  
  
```  
BOOL Save(LPCTSTR lpszBmpFileName=NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszBmpFileName`  
 磁盘文件的路径。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则保存的工具栏图像否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以将用户定义的映像存储到磁盘文件。 如果`lpszBmpFileName`是`NULL`，该方法将该位图存储到位图被从中加载该文件[CMFCToolBarImages::Load](#load)方法。  
  
##  <a name="a-namesetalwayslighta--cmfctoolbarimagessetalwayslight"></a><a name="setalwayslight"></a>CMFCToolBarImages::SetAlwaysLight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetAlwaysLight(BOOL bAlwaysLight = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAlwaysLight`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetdisabledimagealphaa--cmfctoolbarimagessetdisabledimagealpha"></a><a name="setdisabledimagealpha"></a>CMFCToolBarImages::SetDisabledImageAlpha  
 设置用于禁用图像的 alpha 通道 (opacity) 值。  
  
```  
static void SetDisabledImageAlpha(BYTE nValue);
```  
  
### <a name="parameters"></a>参数  
 [in] `nValue`  
 Alpha 通道的新值。  
  
### <a name="remarks"></a>备注  
 此方法用于设置已禁用的图像的自定义 alpha 值。 默认值为 127 个，这将导致是半透明的禁用的按钮图像。 如果您设置的值为 0，已禁用的图像将完全透明。 如果您设置的值为 255，已禁用的图像将完全不透明。  
  
##  <a name="a-namesetfadedimagealphaa--cmfctoolbarimagessetfadedimagealpha"></a><a name="setfadedimagealpha"></a>CMFCToolBarImages::SetFadedImageAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall SetFadedImageAlpha(BYTE nValue);
```  
  
### <a name="parameters"></a>参数  
 [in] `nValue`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetimagesizea--cmfctoolbarimagessetimagesize"></a><a name="setimagesize"></a>CMFCToolBarImages::SetImageSize  
 设置每个工具栏图像 （源大小） 的大小。  
  
```  
void SetImageSize(
    SIZE sizeImage,  
    BOOL bUpdateCount=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `sizeImage`  
 新的工具栏图像大小。  
  
### <a name="remarks"></a>备注  
 默认情况下工具栏图像的大小为 16 x 15 像素。 如果您想要使用的不同大小的工具栏图像，请调用此方法。  
  
##  <a name="a-namesetlightpercentagea--cmfctoolbarimagessetlightpercentage"></a><a name="setlightpercentage"></a>CMFCToolBarImages::SetLightPercentage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetLightPercentage(int nValue);
```  
  
### <a name="parameters"></a>参数  
 [in] `nValue`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetmapto3dcolorsa--cmfctoolbarimagessetmapto3dcolors"></a><a name="setmapto3dcolors"></a>CMFCToolBarImages::SetMapTo3DColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetMapTo3DColors(BOOL bMapTo3DColors);
```  
  
### <a name="parameters"></a>参数  
 [in] `bMapTo3DColors`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetpremultiplyautochecka--cmfctoolbarimagessetpremultiplyautocheck"></a><a name="setpremultiplyautocheck"></a>CMFCToolBarImages::SetPreMultiplyAutoCheck  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetPreMultiplyAutoCheck(BOOL bAuto = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAuto`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetsingleimagea--cmfctoolbarimagessetsingleimage"></a><a name="setsingleimage"></a>CMFCToolBarImages::SetSingleImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetSingleImage();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesettransparentcolora--cmfctoolbarimagessettransparentcolor"></a><a name="settransparentcolor"></a>CMFCToolBarImages::SetTransparentColor  
 设置的工具栏图像的透明色。  
  
```  
COLORREF SetTransparentColor(COLORREF clrTransparent);
```  
  
### <a name="parameters"></a>参数  
 [in] `clrTransparent`  
 RGB 值。  
  
### <a name="return-value"></a>返回值  
 以前的透明颜色。  
  
### <a name="remarks"></a>备注  
 当您或框架调用[CMFCToolBarImages::Draw](#draw)，该方法不绘制任何与指定的颜色相匹配的像素`clrTransparent`。  
  
##  <a name="a-nameupdateimagea--cmfctoolbarimagesupdateimage"></a><a name="updateimage"></a>CMFCToolBarImages::UpdateImage  
 更新从位图的用户定义的工具栏图像。  
  
```  
BOOL UpdateImage(
    int iImage,  
    HBITMAP hbmp);
```  
  
### <a name="parameters"></a>参数  
 [in] `iImage`  
 要更新的图像的从零开始的索引。  
  
 [in] `hbmp`  
 要更新的映像从中位图句柄。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则更新映像`FALSE`如果图像列表不是用户定义的或临时。  
  
##  <a name="a-nameconvertto32bitsa--cmfctoolbarimagesconvertto32bits"></a><a name="convertto32bits"></a>CMFCToolBarImages::ConvertTo32Bits  
 转换为它添加下划线为 32 bpp 图像的位图。  
  
```  
BOOL ConvertTo32Bits(COLORREF clrTransparent = (COLORREF)-1);
```  
  
### <a name="parameters"></a>参数  
 `clrTransparent`  
 指定带下划线的位图的透明的颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetbitsperpixela--cmfctoolbarimagesgetbitsperpixel"></a><a name="getbitsperpixel"></a>CMFCToolBarImages::GetBitsPerPixel  
 返回当前分辨率的带下划线的映像。  
  
```  
int GetBitsPerPixel() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个整数值，表示带下划线的图像，请在位 / 像素 (bpp) 的当前分辨率。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetscalea--cmfctoolbarimagesgetscale"></a><a name="getscale"></a>CMFCToolBarImages::GetScale  
 返回当前的缩放比例的带下划线的映像。  
  
```  
double GetScale() const;  
```  
  
### <a name="return-value"></a>返回值  
 表示当前的缩放比率的值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisscaleda--cmfctoolbarimagesisscaled"></a><a name="isscaled"></a>CMFCToolBarImages::IsScaled  
 指示是否对带下划线的图像缩放。  
  
```  
BOOL IsScaled () const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果带下划线的图像进行缩放。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesmoothresizea--cmfctoolbarimagessmoothresize"></a><a name="smoothresize"></a>CMFCToolBarImages::SmoothResize  
 顺利地调整带下划线的图像的大小。  
  
```  
BOOL SmoothResize(double dblImageScale);
```  
  
### <a name="parameters"></a>参数  
 `dblImageScale`  
 缩放比例。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功重设大小;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)

