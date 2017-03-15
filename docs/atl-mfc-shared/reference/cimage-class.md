---
title: "CImage 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CImage
- ATL.CImage
- ATL::CImage
dev_langs:
- C++
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
caps.latest.revision: 20
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: f74e5952401d6f9608425681cd91120b648e7b13
ms.lasthandoff: 02/24/2017

---
# <a name="cimage-class"></a>CImage 类
`CImage`提供了增强的位图支持，包括加载和保存 JPEG、 GIF、 BMP 和可移植网络图形 (PNG) 格式的图像的能力。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CImage
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CImage::CImage](#cimage)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Cimage:: Alphablend](#alphablend)|显示具有透明或半透明的像素的位图。|  
|[CImage::Attach](#attach)|将附加`HBITMAP`到`CImage`对象。 可以用于非 DIB 部分位图或 DIB 部分位图。|  
|[CImage::BitBlt](#bitblt)|将源设备上下文的位图复制到此当前的设备上下文。|  
|[CImage::Create](#create)|创建 DIB 部分位图，并将其附加到先前构造`CImage`对象。|  
|[CImage::CreateEx](#createex)|创建的 DIB 部分位图 （采用附加参数），并将其附加到先前构造`CImage`对象。|  
|[CImage::Destroy](#destroy)|分离从位图`CImage`对象，并销毁位图。|  
|[CImage::Detach](#detach)|分离从位图`CImage`对象。|  
|[Cimage:: Draw](#draw)|将位图从源矩形复制到目标矩形。 **绘制**拉伸或压缩位图以符合目标矩形的尺寸，如有必要，并处理 alpha 值混合处理和透明的颜色。|  
|[CImage::GetBits](#getbits)|检索指向位图的实际像素值的指针。|  
|[CImage::GetBPP](#getbpp)|检索每个像素的位数。|  
|[CImage::GetColorTable](#getcolortable)|从颜色表中的条目范围检索红、 绿、 蓝 (RGB) 颜色值。|  
|[CImage::GetDC](#getdc)|检索在其中选择当前位图的设备上下文。|  
|[CImage::GetExporterFilterString](#getexporterfilterstring)|查找可用的图像格式和它们的说明。|  
|[CImage::GetHeight](#getheight)|检索当前图像以像素为单位的高度。|  
|[CImage::GetImporterFilterString](#getimporterfilterstring)|查找可用的图像格式和它们的说明。|  
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|检索的最大颜色表中的条目数。|  
|[CImage::GetPitch](#getpitch)|检索当前的图像，以字节为单位的音调。|  
|[CImage::GetPixel](#getpixel)|检索由指定的像素颜色*x*和*y*。|  
|[CImage::GetPixelAddress](#getpixeladdress)|检索给定的像素的地址。|  
|[CImage::GetTransparentColor](#gettransparentcolor)|检索的透明颜色的颜色表中的位置。|  
|[CImage::GetWidth](#getwidth)|检索以像素为单位的当前图像的宽度。|  
|[CImage::IsDIBSection](#isdibsection)|确定附加的位图是 DIB 部分。|  
|[CImage::IsIndexed](#isindexed)|指示位图的颜色都映射到索引的调色板。|  
|[CImage::IsNull](#isnull)|指示当前已加载的源位图。|  
|[CImage::IsTransparencySupported](#istransparencysupported)|指示应用程序是否支持透明的位图，并且编译时用于 Windows 2000 或更高版本。|  
|[CImage::Load](#load)|从指定的文件加载图像。|  
|[CImage::LoadFromResource](#loadfromresource)|从指定的资源加载图像。|  
|[CImage::MaskBlt](#maskblt)|将组合使用指定的掩码和光栅操作的源和目标位图的颜色数据。|  
|[Cimage:: Plgblt](#plgblt)|执行从所源设备上下文中的矩形变成平行四边形目标设备上下文中位块传输。|  
|[CImage::ReleaseDC](#releasedc)|释放与检索到的设备上下文[CImage::GetDC](#getdc)。|  
|[CImage::ReleaseGDIPlus](#releasegdiplus)|释放使用的 GDI + 资源。 必须调用来释放资源创建的全局`CImage`对象。|  
|[CImage::Save](#save)|将图像保存为指定的类型。 **保存**不能指定图像选项。|  
|[CImage::SetColorTable](#setcolortable)|设置红、 绿、 蓝色 RGB） 颜色值区域中的 DIB 部分的颜色表中的条目。|  
|[CImage::SetPixel](#setpixel)|设置为指定的颜色的指定坐标处的像素。|  
|[CImage::SetPixelIndexed](#setpixelindexed)|设置在到颜色的调色板的指定索引处的指定坐标的像素。|  
|[CImage::SetPixelRGB](#setpixelrgb)|设置为指定的红色、 绿色、 蓝 (RGB) 值的指定坐标处的像素。|  
|[CImage::SetTransparentColor](#settransparentcolor)|设置要处理的颜色的索引为透明。 只有一种颜色调色板中的可以是透明的。|  
|[CImage::StretchBlt](#stretchblt)|将位图从源矩形复制到目标矩形，可拉伸或压缩位图以符合目标矩形的尺寸，如有必要。|  
|[Cimage:: Transparentblt](#transparentblt)|将位图，并使用透明颜色来自源设备上下文复制到此当前的设备上下文。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CImage::operator HBITMAP](#operator_hbitmap)|返回附加到的 Windows 句柄`CImage`对象。|  
  
## <a name="remarks"></a>备注  
 `CImage`采用的位图，任一与设备无关位图 (DIB) 部分但是，您可以使用[创建](#create)或[CImage::Load](#load)具有仅 DIB 区域。 您可以将附加到一个非 DIB 部分位图`CImage`对象使用[附加](#attach)，但不是能再使用以下`CImage`支持仅 DIB 部分位图的方法︰  
  
- [GetBits](#getbits)  
  
- [GetColorTable](#getcolortable)  
  
- [GetMaxColorTableEntries](#getmaxcolortableentries)  
  
- [GetPitch](#getpitch)  
  
- [GetPixelAddress](#getpixeladdress)  
  
- [IsIndexed](#isindexed)  
  
- [SetColorTable](#setcolortable)  
  
 若要确定是否附加的位图 DIB 部分，请调用[IsDibSection](#isdibsection)**。**  
  
> [!NOTE]
> **请注意**在 Visual Studio.NET 2003 中，此类保留数的计数`CImage`创建的对象。 只要计数变为 0，该函数**GdiplusShutdown**自动调用以释放使用的 GDI + 资源。 这样可确保任何`CImage`始终正确销毁对象创建的 Dll 的直接或间接地， **GdiplusShutdown**不从调用`DllMain`。  
  
> [!NOTE]
>  使用全局`CImage`不建议在 DLL 中的对象。 如果您需要使用全局`CImage`中一个 DLL，调用对象[CImage::ReleaseGDIPlus](#releasegdiplus)来显式释放所使用的 GDI + 资源。  
  
 `CImage`不能选择到新[CDC](../../mfc/reference/cdc-class.md)。 `CImage`创建其自己**HDC**的图像。 因为`HBITMAP`只能为一个选择**HDC**一次`HBITMAP`与关联`CImage`不能为另一选择**HDC**。 如果您需要`CDC`，检索**HDC**从`CImage`并将其交给 [CDC::FromHandle] (.../../mfc/reference/cdc-class.md#cdc__fromhandle。  
  
## <a name="example"></a>示例  
```cpp  
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```  
  
 当您使用`CImage`在 MFC 项目中，请注意您的项目中的哪些成员函数期望指向的指针[CBitmap](../../mfc/reference/cbitmap-class.md)对象。 如果您想要使用`CImage`与此类函数，如[CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)，使用[CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle)，将其传递您`CImage` `HBITMAP`，并使用返回`CBitmap*`。  

  
## <a name="example"></a>示例  
```cpp  
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
  UNREFERENCED_PARAMETER(nFlags);

  CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
  m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
  ClientToScreen(&point);
  m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x, 
  point.y, this);
}
```  

  
 通过`CImage`，您有权访问 DIB 部分的实际位数。 您可以使用`CImage`您以前使用过的 Win32 HBITMAP 或 DIB 部分任意位置对象。  
  
> [!NOTE]
>  以下`CImage`方法具有对它们的使用限制︰  
  
|方法|限制|  
|------------|----------------|  
|[PlgBlt](#plgblt)|只有 Windows NT 4.0 或更高版本的工作原理。 不会在运行 Windows 95/98 或更高版本的应用程序。|  
|[MaskBlt](#maskblt)|只有 Windows NT 4.0 或更高版本的工作原理。 不会在运行 Windows 95/98 或更高版本的应用程序。|  
|[AlphaBlend](#alphablend)|只有 Windows 2000、 Windows 98 及更高的系统与一起使用。|  
|[TransparentBlt](#transparentblt)|只有 Windows 2000、 Windows 98 及更高的系统与一起使用。|  
|[绘制](#draw)|支持使用 Windows 2000、 Windows 98 和更高的系统的透明度。|  
  
 您可以使用`CImage`从 MFC 或 atl。  
  
> [!NOTE]
>  当您创建一个项目使用`CImage`，必须定义`CString`您包括之前`atlimage.h`。 如果您的项目使用 ATL 无需 MFC，包括`atlstr.h`您包括之前`atlimage.h`。 如果您的项目使用 MFC （或如果它是 MFC 支持的 ATL 项目），包括`afxstr.h`您包括之前`atlimage.h`。  
>   
>  同样，您必须包括`atlimage.h`您包括之前`atlimpl.cpp`。 若要轻松实现此目的，包括`atlimage.h`中您`stdafx.h`。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlimage.h  
  
##  <a name="a-namealphablenda--cimagealphablend"></a><a name="alphablend"></a>Cimage:: Alphablend  
 显示具有透明或半透明的像素的位图。  
  
```
BOOL AlphaBlend(
 HDC hDestDC,
 int xDest,
 int yDest,
 BYTE bSrcAlpha = 0xff,
 BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
 HDC hDestDC,
 const POINT& pointDest,
 BYTE bSrcAlpha = 0xff,
 BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight,
 BYTE bSrcAlpha = 0xff,
 BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
 HDC hDestDC,
 const RECT& rectDest,
 const RECT& rectSrc,
 BYTE bSrcAlpha = 0xff,
 BYTE bBlendOp = AC_SRC_OVER);
```  
  
### <a name="parameters"></a>参数  
 `hDestDC`  
 目标设备上下文的句柄。  
  
 `xDest`  
 X 坐标，使用逻辑单位，目标矩形左上角。  
  
 `yDest`  
 Y 坐标，使用逻辑单位，目标矩形左上角。  
  
 *bSrcAlpha*  
 若要在整个源位图上使用一个 alpha 透明度值。 默认设置 0xff (255) 假定您的图像是不透明的并且您想要使用仅每像素 alpha 值。  
  
 `bBlendOp`  
 对源和目标位图、 要应用于整个源位图和源位图的格式信息的全局 alpha 值的 alpha 混合的函数。 源和目标 blend 函数是当前仅限于**AC_SRC_OVER**。  
  
 `pointDest`  
 对引用[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)标识中的逻辑单元的目标矩形左上的角的结构。  
  
 `nDestWidth`  
 使用逻辑单位，目标矩形的宽度。  
  
 `nDestHeight`  
 使用逻辑单位，目标矩形的高度。  
  
 `xSrc`  
 源矩形左上角逻辑 x 坐标。  
  
 `ySrc`  
 源矩形左上角逻辑 y 坐标。  
  
 `nSrcWidth`  
 使用逻辑单位，源矩形的宽度。  
  
 `nSrcHeight`  
 使用逻辑单位，源矩形的高度。  
  
 `rectDest`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，用于标识目标。  
  
 `rectSrc`  
 对引用`RECT`结构中，标识的源。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 Alpha 混合位图支持基于每个像素的颜色混合。  
  
 当`bBlendOp`设置为默认值为**AC_SRC_OVER**，源位图置于目标位图，并根据源像素的 alpha 值。  

##  <a name="a-nameattacha--cimageattach"></a><a name="attach"></a>CImage::Attach  
 将附加`hBitmap`到`CImage`对象。  
  
```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```  
  
### <a name="parameters"></a>参数  
 `hBitmap`  
 句柄`HBITMAP`。  
  
 *eOrientation*  
 指定位图的方向。 可以是以下各项之一：  
  
- **DIBOR_DEFAULT**由操作系统确定位图的方向。 但是，这并不总能预期的结果在所有操作系统上。 有关这方面的详细信息，请参阅以下知识库文章 ( **Q186586**): PRB: getobject （） 始终返回正高度为 DIB 部分。  
  
- **DIBOR_BOTTOMUP**位图的行将按相反的顺序。 这将导致[CImage::GetBits](#getbits)返回结尾处的位图缓冲区的指针和[CImage::GetPitch](#getpitch)返回一个负数。  
  
- **DIBOR_TOPDOWN**位图的行采用自上而下的顺序。 这将导致[CImage::GetBits](#getbits)以返回指向位图缓冲区的第一个字节的指针和[CImage::GetPitch](#getpitch)要返回的正数值。  
  
### <a name="remarks"></a>备注  
 位图可以是一个非 DIB 部分位图或 DIB 部分位图。 请参阅[IsDIBSection](#isdibsection)有关列表，可以使用只适用于 DIB 方法部分位图。  
  
##  <a name="a-namebitblta--cimagebitblt"></a><a name="bitblt"></a>CImage::BitBlt  
 将源设备上下文的位图复制到此当前的设备上下文。  
  
```
BOOL BitBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
 HDC hDestDC,
 const POINT& pointDest,
 DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
 HDC hDestDC,
 const RECT& rectDest,
 const POINT& pointSrc,
 DWORD dwROP = SRCCOPY) const throw();
```  
  
### <a name="parameters"></a>参数  
 `hDestDC`  
 目标**HDC**。  
  
 `xDest`  
 目标矩形左上角逻辑 x 坐标。  
  
 `yDest`  
 目标矩形左上角逻辑 y 坐标。  
  
 `dwROP`  
 要执行的光栅操作。 光栅操作代码定义如何组合源、 目标和模式的位 （如定义当前选择的画笔），将窗体目标。 请参阅[BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]有关其他光栅操作代码及其说明的列表。  
  
 `pointDest`  
 一个[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，指示目标矩形左上的角。  
  
 `nDestWidth`  
 使用逻辑单位，目标矩形的宽度。  
  
 `nDestHeight`  
 使用逻辑单位，目标矩形的高度。  
  
 `xSrc`  
 源矩形左上角逻辑 x 坐标。  
  
 `ySrc`  
 源矩形左上角逻辑 y 坐标。  
  
 `rectDest`  
 一个[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，指示目标矩形。  
  
 `pointSrc`  
 一个**点**结构，指示源矩形左上的角。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namecimagea--cimagecimage"></a><a name="cimage"></a>CImage::CImage  
 构造 `CImage` 对象。  
  
```
CImage() throw();
```  
  
### <a name="remarks"></a>备注  
 一旦你已构造该对象，调用[创建](#create)，[负载](#load)， [LoadFromResource](#loadfromresource)，或[附加](#attach)将位图附加到对象。  
  
 **请注意**在 Visual Studio 中，此类保留数的计数`CImage`创建的对象。 只要计数变为 0，该函数**GdiplusShutdown**自动调用以释放使用的 GDI + 资源。 这样可确保任何`CImage`始终正确销毁对象创建的 Dll 的直接或间接地， **GdiplusShutdown**不从 DllMain 调用。  
  
 使用全局`CImage`不建议在 DLL 中的对象。 如果您需要使用全局`CImage`中一个 DLL，调用对象[CImage::ReleaseGDIPlus](#releasegdiplus)来显式释放所使用的 GDI + 资源。  
  
##  <a name="a-namecreatea--cimagecreate"></a><a name="create"></a>CImage::Create  
 创建`CImage`位图，并将其附加到先前构造`CImage`对象。  
  
```
BOOL Create(
 int nWidth,
 int nHeight,
 int nBPP,
 DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>参数  
 `nWidth`  
 宽度`CImage`位图，以像素为单位。  
  
 `nHeight`  
 高度`CImage`位图，以像素为单位。 如果`nHeight`是正数，位图是自下而上的 DIB，其源是左下的角。 如果`nHeight`是负数，该位图自上而下的 DIB，其源是左上角。  
  
 `nBPP`  
 位 / 像素的位图中的数字。 通常 4、 8、 16、 24 或 32。 可以是 1 的单色位图或掩码。  
  
 `dwFlags`  
 指定位图对象是否具有 alpha 通道。 可以是零个或多个以下值的组合︰  
  
- **createAlphaChannel**如果可以只使用`nBPP`为 32，和`eCompression`是**BI_RGB**。 如果指定，创建的图像已存储在每个像素 （非 alpha 32 位映像中未使用） 的第四个字节的每个像素的 alpha （透明度） 值。 在调用时，会自动使用此 alpha 通道[cimage:: Alphablend](#alphablend)。  
  
> [!NOTE]
>  在调用[cimage:: Draw](#draw)，alpha 通道的映像会自动 alpha 混合到目标。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="a-namecreateexa--cimagecreateex"></a><a name="createex"></a>CImage::CreateEx  
 创建`CImage`位图，并将其附加到先前构造`CImage`对象。  
  
```
BOOL CreateEx(
 int nWidth,
 int nHeight,
 int nBPP,
 DWORD eCompression,
 const DWORD* pdwBitmasks = NULL,
 DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>参数  
 `nWidth`  
 宽度`CImage`位图，以像素为单位。  
  
 `nHeight`  
 高度`CImage`位图，以像素为单位。 如果`nHeight`是正数，位图是自下而上的 DIB，其源是左下的角。 如果`nHeight`是负数，该位图自上而下的 DIB，其源是左上角。  
  
 `nBPP`  
 位 / 像素的位图中的数字。 通常 4、 8、 16、 24 或 32。 可以是 1 的单色位图或掩码。  
  
 `eCompression`  
 指定压缩自下而上的位图 （无法压缩自上而下的 Dib） 的压缩的类型。 可以是以下值之一：  
  
- **BI_RGB**未压缩格式。 在调用时指定此值`CImage::CreateEx`等效于调用`CImage::Create`。  
  
- **BI_BITFIELDS**该格式为未压缩，颜色表由三个`DWORD`颜色掩码，指定红色，绿色，将组件，则分别和蓝色，每个像素。 这是与 16 和 32 bpp 位图一起使用时有效。  
  
 *pdwBitfields*  
 只有当使用`eCompression`设置为**BI_BITFIELDS**，否则必须**NULL**。 指向包含三个数组的指针`DWORD`位掩码，指定每个像素的哪些位用于红色，绿色，将分别和蓝色组件的颜色。 位域的限制的信息，请参阅[BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `dwFlags`  
 指定位图对象是否具有 alpha 通道。 可以是零个或多个以下值的组合︰  
  
- **createAlphaChannel**如果可以只使用`nBPP`为 32，和`eCompression`是**BI_RGB**。 如果指定，创建的图像已存储在每个像素 （非 alpha 32 位映像中未使用） 的第四个字节的每个像素的 alpha （透明度） 值。 在调用时，会自动使用此 alpha 通道[cimage:: Alphablend](#alphablend)。  
  
    > [!NOTE]
    >  在调用[cimage:: Draw](#draw)，alpha 通道的映像会自动 alpha 混合到目标。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果操作成功。 否则为**FALSE**。  
  
### <a name="example"></a>示例  
 下面的示例创建一个 100 x 100 像素的位图，使用 16 位编码每个像素。 在给定的 16 位像素，位 0-3 编码红色组件、 4-7 位编码绿色，和 8-11 位用于对蓝色编码。 其余的 4 位是未使用。  

```cpp  
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```


##  <a name="a-namedestroya--cimagedestroy"></a><a name="destroy"></a>CImage::Destroy  
 分离从位图`CImage`对象，并销毁位图。  
  
```
void Destroy() throw();
```  
  
##  <a name="a-namedetacha--cimagedetach"></a><a name="detach"></a>CImage::Detach  
 分离从位图`CImage`对象。  
  
```
HBITMAP Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 分离后，该位图的句柄或**NULL**如果连接不使用位图。  
  
##  <a name="a-namedrawa--cimagedraw"></a><a name="draw"></a>Cimage:: Draw  
 将源设备上下文的位图复制到当前的设备上下文。  
  
```
BOOL Draw(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight) const throw();

BOOL Draw(
 HDC hDestDC,
 const RECT& rectDest,
 const RECT& rectSrc) const throw();

BOOL Draw(
 HDC hDestDC,
 int xDest,
 int yDest) const throw();

BOOL Draw(
 HDC hDestDC,
 const POINT& pointDest) const throw();

BOOL Draw(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight) const throw();

BOOL Draw(
 HDC hDestDC,
 const RECT& rectDest) const throw();
```  
  
### <a name="parameters"></a>参数  
 `hDestDC`  
 目标设备上下文的句柄。  
  
 `xDest`  
 X 坐标，使用逻辑单位，目标矩形左上角。  
  
 `yDest`  
 Y 坐标，使用逻辑单位，目标矩形左上角。  
  
 `nDestWidth`  
 使用逻辑单位，目标矩形的宽度。  
  
 `nDestHeight`  
 使用逻辑单位，目标矩形的高度。  
  
 `xSrc`  
 X 坐标，使用逻辑单位，源矩形左上角。  
  
 `ySrc`  
 Y 坐标，使用逻辑单位，源矩形左上角。  
  
 `nSrcWidth`  
 使用逻辑单位，源矩形的宽度。  
  
 `nSrcHeight`  
 使用逻辑单位，源矩形的高度。  
  
 `rectDest`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，用于标识目标。  
  
 `rectSrc`  
 对引用`RECT`结构中，标识的源。  
  
 `pointDest`  
 对引用[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)标识中的逻辑单元的目标矩形左上的角的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 **绘制**执行相同的操作[StretchBlt](#stretchblt)，除非映像包含透明颜色或 alpha 通道。 在这种情况下，**绘制**执行相同的操作为[TransparentBlt](#transparentblt)或[AlphaBlend](#alphablend)所需的方式。  
  
 对于版本的**绘制**不指定源矩形、 整个源图像是默认设置。 版本**绘制**，未指定目标矩形的大小、 源映像的大小为默认值且没有拉伸或收缩时发生。  
  
##  <a name="a-namegetbitsa--cimagegetbits"></a><a name="getbits"></a>CImage::GetBits  
 检索指向给定像素位图中的实际位值的指针。  
  
```
void* GetBits() throw();
```  
  
### <a name="return-value"></a>返回值  
 指向位图缓冲区的指针。 如果位图，自下而上的 DIB 指针指向附近缓冲区的末尾。 如果位图是自上而下的 DIB，指针将指向第一个字节的缓冲区。  
  
### <a name="remarks"></a>备注  
 使用此指针，以及返回的值[GetPitch](#getpitch)，可以找到并更改在图像中的单个像素。  
  
> [!NOTE]
>  此方法支持仅 DIB 部分位图;因此，访问的像素`CImage`对象相同的方式的像素 DIB 部分。 返回的指针指向的位置 （0，0） 像素。  
  
##  <a name="a-namegetbppa--cimagegetbpp"></a><a name="getbpp"></a>CImage::GetBPP  
 检索的每像素位值。  
  
```
int GetBPP() const throw();
```  
  
### <a name="return-value"></a>返回值  
 每个像素的比特数。  
  
### <a name="remarks"></a>备注  
 此值确定定义每个像素的比特数和最大的位图中的颜色数。  
  
 1、 4、 8、 16、 24 或 32，通常是每像素位数。 请参阅**biBitCount**的成员[BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]有关此值的详细信息。  
  
##  <a name="a-namegetcolortablea--cimagegetcolortable"></a><a name="getcolortable"></a>CImage::GetColorTable  
 从 DIB 部分调色板中的项范围检索红、 绿、 蓝 (RGB) 颜色值。  
  
```
void GetColorTable(UINT iFirstColor,
 UINT nColors,
 RGBQUAD* prgbColors) const throw();
```  
  
### <a name="parameters"></a>参数  
 `iFirstColor`  
 要检索的第一个条目的颜色表索引。  
  
 `nColors`  
 颜色表要检索的条目数。  
  
 `prgbColors`  
 指向数组的指针[RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)结构，以检索颜色表项。  
  
##  <a name="a-namegetdca--cimagegetdc"></a><a name="getdc"></a>CImage::GetDC  
 检索当前具有到该选择的映像的设备上下文。  
  
```
HDC GetDC() const throw();
```  
  
### <a name="return-value"></a>返回值  
 设备上下文的句柄。  
  
### <a name="remarks"></a>备注  
 每次调用`GetDC`，您必须具有的后续调用[ReleaseDC](#releasedc)。  
  
##  <a name="a-namegetexporterfilterstringa--cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage::GetExporterFilterString  
 查找可用的图像格式来保存图像。  
  
```
static HRESULT GetExporterFilterString(CSimpleString& strExporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultSave,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>参数  
 *strExporters*  
 对引用**CSimpleString**对象。 请参阅**备注**有关详细信息。  
  
 `aguidFileTypes`  
 Guid 的数组，且每个元素对应于一个字符串中的文件类型。 在示例中`pszAllFilesDescription`下面`aguidFileTypes`[0] 是`GUID_NULL`和剩余的数组值是当前的操作系统支持的图像文件格式。  
  
> [!NOTE]
>  常量的完整列表，请参阅**图像文件格式常量**中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `pszAllFilesDescription`  
 如果此参数不是**NULL**，筛选器字符串将列表的开头带有一个附加的筛选器。 此筛选器将具有的当前值`pszAllFilesDescription`有关其说明，并接受列表中的任何其他导出程序支持的任何文件扩展名的文件。  
  
 例如：  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 指定要从列表中排除的文件类型的位标志的组。 允许使用的标志是︰  
  
- **excludeGIF** = 0x01 排除 GIF 文件。  
  
- **excludeBMP** = 0x02 排除 BMP （Windows 位图） 文件。  
  
- **excludeEMF** = 0x04，则不包括 EMF （增强型图元文件） 文件。  
  
- **excludeWMF** = 0x08 排除 WMF （Windows 图元文件） 文件。  
  
- **excludeJPEG** = 0x10 排除 JPEG 文件。  
  
- **excludePNG** = 0x20 排除 PNG 文件。  
  
- **excludeTIFF** = 0x40 排除 TIFF 文件。  
  
- **excludeIcon** = 0x80 排除 ICO （Windows 图标） 文件。  
  
- **excludeOther** = 0x80000000 排除上面未列出的任何其他文件类型。  
  
- **excludeDefaultLoad** = 0 对于负载，默认情况下包含类型的所有文件  
  
- **excludeDefaultSave** = **excludeIcon | excludeEMF | excludeWMF**来保存，这些文件被排除在默认情况下因为它们通常有特殊要求。  
  
 `chSeparator`  
 使用图像格式之间的分隔符。 请参阅**备注**有关详细信息。  
  
### <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
### <a name="remarks"></a>备注  
 可以将生成的格式字符串传递到您 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)对象公开可用的图像的文件扩展名在文件另存为对话框中设置的格式。  
  
 该参数*strExporter*具有格式︰  
  
 文件 description0 |\*.ext0 | filedescription1 |\*.ext1 |...文件描述*n*|\*。ext *n*||  
  
 其中 | 由指定的分隔符字符`chSeparator`。 例如:   
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 使用默认分隔符 ' |' 如果将此字符串传递给 MFC`CFileDialog`对象。 如果将此字符串传递给标准保存文件对话框中，请使用空分隔符 \0'。  
  
##  <a name="a-namegetheighta--cimagegetheight"></a><a name="getheight"></a>CImage::GetHeight  
 检索的高度，以像素为单位的图像。  
  
```
int GetHeight() const throw();
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位的图像的高度。  
  
##  <a name="a-namegetimporterfilterstringa--cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage::GetImporterFilterString  
 查找可用的图像格式加载图像。  
  
```
static HRESULT GetImporterFilterString(CSimpleString& strImporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultLoad,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>参数  
 *strImporters*  
 对引用**CSimpleString**对象。 请参阅**备注**有关详细信息。  
  
 `aguidFileTypes`  
 Guid 的数组，且每个元素对应于一个字符串中的文件类型。 在示例中`pszAllFilesDescription`下面`aguidFileTypes`[0] 是`GUID_NULL`包含剩余的数组的值为当前的操作系统支持的图像文件格式。  
  
> [!NOTE]
>  常量的完整列表，请参阅**图像文件格式常量**中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `pszAllFilesDescription`  
 如果此参数不是**NULL**，筛选器字符串将列表的开头带有一个附加的筛选器。 此筛选器将具有的当前值`pszAllFilesDescription`有关其说明，并接受列表中的任何其他导出程序支持的任何文件扩展名的文件。  
  
 例如:   

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 指定要从列表中排除的文件类型的位标志的组。 允许使用的标志是︰  
  
- **excludeGIF** = 0x01 排除 GIF 文件。  
  
- **excludeBMP** = 0x02 排除 BMP （Windows 位图） 文件。  
  
- **excludeEMF** = 0x04，则不包括 EMF （增强型图元文件） 文件。  
  
- **excludeWMF** = 0x08 排除 WMF （Windows 图元文件） 文件。  
  
- **excludeJPEG** = 0x10 排除 JPEG 文件。  
  
- **excludePNG** = 0x20 排除 PNG 文件。  
  
- **excludeTIFF** = 0x40 排除 TIFF 文件。  
  
- **excludeIcon** = 0x80 排除 ICO （Windows 图标） 文件。  
  
- **excludeOther** = 0x80000000 排除上面未列出的任何其他文件类型。  
  
- **excludeDefaultLoad** = 0 对于负载，默认情况下包含类型的所有文件  
  
- **excludeDefaultSave** = **excludeIcon | excludeEMF | excludeWMF**来保存，这些文件被排除在默认情况下因为它们通常有特殊要求。  
  
 `chSeparator`  
 使用图像格式之间的分隔符。 请参阅**备注**有关详细信息。  
  
### <a name="remarks"></a>备注  
 可以将生成的格式字符串传递到您 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)对象公开可用的图像的文件扩展名格式中**文件打开**对话框。  
  
 该参数*strImporter*具有格式︰  
  
 文件 description0 |\*.ext0 | filedescription1 |\*.ext1 |...文件描述*n*|\*。ext *n*||  
  
 其中 | 由指定的分隔符字符`chSeparator`。 例如：  
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 使用默认分隔符 ' |' 如果将此字符串传递给 MFC`CFileDialog`对象。 如果将此字符串传递到一种常见使用 null 分隔符 \0'**文件打开**对话框。  
  
##  <a name="a-namegetmaxcolortableentriesa--cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage::GetMaxColorTableEntries  
 检索的最大颜色表中的条目数。  
  
```
int GetMaxColorTableEntries() const throw();
```  
  
### <a name="return-value"></a>返回值  
 颜色表中的条目数。  
  
### <a name="remarks"></a>备注  
 此方法支持仅 DIB 部分位图。  
  
##  <a name="a-namegetpitcha--cimagegetpitch"></a><a name="getpitch"></a>CImage::GetPitch  
 检索图像的音调。  
  
```
int GetPitch() const throw();
```  
  
### <a name="return-value"></a>返回值  
 图像的音调。 如果返回值为负，位图自下而上的 DIB，其源是左下的角。 如果返回值为正，位图是自上而下的 DIB，其源是左上角。  
  
### <a name="remarks"></a>备注  
 俯仰是以字节为单位，表示一个位图行的开头的两个内存地址和下一步的位图行的开头之间的距离。 俯仰以字节为单位，因为图像的音调可帮助您确定的像素格式。 音调还可以包含额外的内存，留待位图。  
  
 使用`GetPitch`与[GetBits](#getbits)来查找单个像素的图像。  
  
> [!NOTE]
>  此方法支持仅 DIB 部分位图。  
  
##  <a name="a-namegetpixela--cimagegetpixel"></a><a name="getpixel"></a>CImage::GetPixel  
 检索由指定的位置处的像素颜色*x*和*y*。  
  
```
COLORREF GetPixel(int x,int y) const throw();
```  
  
### <a name="parameters"></a>参数  
 *x*  
 像素 x 坐标。  
  
 *y*  
 Y 坐标的像素。  
  
### <a name="return-value"></a>返回值  
 红、 绿、 蓝 (RGB) 像素的值。 如果该像素是与当前剪辑区域之外，返回值是**CLR_INVALID**。  
  
##  <a name="a-namegetpixeladdressa--cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage::GetPixelAddress  
 检索一个像素的确切的地址。  
  
```
void* GetPixelAddress(int x,int y) throw();
```  
  
### <a name="parameters"></a>参数  
 *x*  
 像素 x 坐标。  
  
 *y*  
 Y 坐标的像素。  
  
### <a name="remarks"></a>备注  
 根据一个像素坐标，在位图中和每像素位数的音调确定的地址。  
  
 对于具有小于 8 位 / 像素的格式，此方法返回包含像素的字节的地址。 例如，如果您的图像格式具有 4 位 / 像素，`GetPixelAddress`返回字节，并且您的第一个像素的地址必须为每个字节的 2 个像素计算。  
  
> [!NOTE]
>  此方法支持仅 DIB 部分位图。  
  
##  <a name="a-namegettransparentcolora--cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage::GetTransparentColor  
 检索的透明颜色在调色板中的索引的位置。  
  
```
LONG GetTransparentColor() const throw();
```  
  
### <a name="return-value"></a>返回值  
 透明颜色的索引。  
  
##  <a name="a-namegetwidtha--cimagegetwidth"></a><a name="getwidth"></a>CImage::GetWidth  
 检索的宽度，以像素为单位的图像。  
  
```
int GetWidth() const throw();
```  
  
### <a name="return-value"></a>返回值  
 位图，以像素为单位的宽度。  
  
##  <a name="a-nameisdibsectiona--cimageisdibsection"></a><a name="isdibsection"></a>CImage::IsDIBSection  
 确定附加的位图是 DIB 部分。  
  
```
bool IsDIBSection() const throw();
```  
  
### <a name="return-value"></a>返回值  
 **true**如果附加的位图是 DIB 部分。 否则为**false**。  
  
### <a name="remarks"></a>备注  
 如果位图不是 DIB 部分，您不能使用以下`CImage`支持仅 DIB 部分位图的方法︰  
  
- [GetBits](#getbits)  
  
- [GetColorTable](#getcolortable)  
  
- [GetMaxColorTableEntries](#getmaxcolortableentries)  
  
- [GetPitch](#getpitch)  
  
- [GetPixelAddress](#getpixeladdress)  
  
- [IsIndexed](#isindexed)  
  
- [SetColorTable](#setcolortable)  
  
##  <a name="a-nameisindexeda--cimageisindexed"></a><a name="isindexed"></a>CImage::IsIndexed  
 确定是否将位图的像素映射到调色板。  
  
```
bool IsIndexed() const throw();
```  
  
### <a name="return-value"></a>返回值  
 **true**索引; 否则为如果**false**。  
  
### <a name="remarks"></a>备注  
 此方法返回**true**仅当位图为 8 位 （256 色） 或更少。  
  
> [!NOTE]
>  此方法支持仅 DIB 部分位图。  
  
##  <a name="a-nameisnulla--cimageisnull"></a><a name="isnull"></a>CImage::IsNull  
 确定当前已加载位图。  
  
```
bool IsNull() const throw();
```  
  
### <a name="remarks"></a>备注  
 此方法返回**True**如果位图不是当前加载; 否则为**False**。  
  
##  <a name="a-nameistransparencysupporteda--cimageistransparencysupported"></a><a name="istransparencysupported"></a>CImage::IsTransparencySupported  
 指示应用程序是否支持透明的位图，并且编译时用于 Windows 2000 或更高版本。  
  
```
static BOOL IsTransparencySupported() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果当前平台支持透明，非零值。 否则为 0。  
  
### <a name="remarks"></a>备注  
 如果返回值为非零值，且支持透明度，则调用[AlphaBlend](#alphablend)， [TransparentBlt](#transparentblt)，或[绘制](#draw)将处理透明的颜色。  
  
 如果在 Windows 2000 或 Windows 98 之前编译与操作系统一起使用的应用程序，此方法将始终返回 0，即使在较新的操作系统上。  
  

##  <a name="a-nameloada--cimageload"></a><a name="load"></a>CImage::Load  
 加载图像。  
  
```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszFileName`  
 指向包含要加载的图像文件的名称的字符串的指针。  
  
 `pStream`  
 指向包含要加载的图像文件的名称的流的指针。  
  
### <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
### <a name="remarks"></a>备注  
 加载所指定的图像*pszFileName*或`pStream`。  
  
 有效的图像类型是 BMP、 GIF、 JPEG、 PNG 和 TIFF。  
  
##  <a name="a-nameloadfromresourcea--cimageloadfromresource"></a><a name="loadfromresource"></a>CImage::LoadFromResource  
 将从映像加载`BITMAP`资源。  
  
```
void LoadFromResource(
 HINSTANCE hInstance,
 LPCTSTR pszResourceName) throw();

void LoadFromResource(
 HINSTANCE hInstance,
 UINT nIDResource) throw();
```  
  
### <a name="parameters"></a>参数  
 `hInstance`  
 包含要加载的图像的模块的实例的句柄。  
  
 `pszResourceName`  
 指向包含的包含要加载的图像的资源名称的字符串的指针。  
  
 `nIDResource`  
 若要加载的资源 ID。  
  
### <a name="remarks"></a>备注  
 该资源的类型必须为`BITMAP`。  
  
##  <a name="a-namemaskblta--cimagemaskblt"></a><a name="maskblt"></a>CImage::MaskBlt  
 将组合使用指定的掩码和光栅操作的源和目标位图的颜色数据。  
  
```
BOOL MaskBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 HBITMAP hbmMask,
 int xMask,
 int yMask,
 DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
 HDC hDestDC,
 const RECT& rectDest,
 const POINT& pointSrc,
 HBITMAP hbmMask,
 const POINT& pointMask,
 DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 HBITMAP hbmMask,
 DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
 HDC hDestDC,
 const POINT& pointDest,
 HBITMAP hbmMask,
 DWORD dwROP = SRCCOPY) const throw();
```  
  
### <a name="parameters"></a>参数  
 `hDestDC`  
 其可执行文件包含该资源的模块句柄。  
  
 `xDest`  
 X 坐标，使用逻辑单位，目标矩形左上角。  
  
 `yDest`  
 Y 坐标，使用逻辑单位，目标矩形左上角。  
  
 `nDestWidth`  
 使用逻辑单位，目标矩形，源位图的宽度。  
  
 `nDestHeight`  
 使用逻辑单位，目标矩形，源位图的高度。  
  
 `xSrc`  
 源位图左上角逻辑 x 坐标。  
  
 `ySrc`  
 源位图左上角逻辑 y 坐标。  
  
 `hbmMask`  
 单色屏蔽位图结合源设备上下文中的颜色位图的句柄。  
  
 `xMask`  
 通过指定的掩码位图的水平像素偏移量`hbmMask`参数。  
  
 `yMask`  
 通过指定的掩码位图的像素垂直偏移量`hbmMask`参数。  
  
 `dwROP`  
 指定该方法用来控制数据源和目标数据的组合的前景色和背景三元光栅操作代码。 背景光栅操作代码存储在此值; 高序位字的高序位字节前景色光栅操作代码存储在此值; 高序位字低位字节此值的低位字将被忽略，并且应为零。 前景色和背景此方法的上下文中的讨论，请参阅`MaskBlt`中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 常见的光栅操作代码的列表，请参阅`BitBlt`中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `rectDest`  
 对引用`RECT`结构，用于标识目标。  
  
 `pointSrc`  
 一个`POINT`结构，指示源矩形左上的角。  
  
 `pointMask`  
 一个**点**结构，指示掩码位图左上的角。  
  
 `pointDest`  
 对引用**点**标识中的逻辑单元的目标矩形左上的角的结构。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法适用于 Windows NT 中，4.0 版和更高版本的唯一版本。  
  
##  <a name="a-nameoperatorhbitmapa--cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage::operator HBITMAP  
 使用此运算符将获得附加的 Windows GDI 句柄的`CImage`对象。 此运算符被强制转换运算符，它支持直接使用`HBITMAP`对象。  
  
##  <a name="a-nameplgblta--cimageplgblt"></a><a name="plgblt"></a>Cimage:: Plgblt  
 执行从所源设备上下文中的矩形变成平行四边形目标设备上下文中位块传输。  
  
```
BOOL PlgBlt(
 HDC hDestDC,
 const POINT* pPoints,
 HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
 HDC hDestDC,
 const POINT* pPoints,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight,
 HBITMAP hbmMask = NULL,
 int xMask = 0,
 int yMask = 0) const throw();

BOOL PlgBlt(
 HDC hDestDC,
 const POINT* pPoints,
 const RECT& rectSrc,
 HBITMAP hbmMask = NULL,
 const POINT& pointMask = CPoint(0, 0)) const throw();
```  
  
### <a name="parameters"></a>参数  
 `hDestDC`  
 目标设备上下文的句柄。  
  
 *pPoints*  
 指向的逻辑空间中三个标识的目标平行四边形的三个角的点数组的指针。 源矩形左上的角映射到此数组，此数组中的第二个点的右上角，然后向第三个点左下的角的第一个点。 源矩形的右下角映射到在平行四边形中隐式的第四个点。  
  
 `hbmMask`  
 用于屏蔽一些源矩形的颜色的可选单色位图句柄。  
  
 `xSrc`  
 X 坐标，使用逻辑单位，源矩形左上角。  
  
 `ySrc`  
 Y 坐标，使用逻辑单位，源矩形左上角。  
  
 `nSrcWidth`  
 使用逻辑单位，源矩形的宽度。  
  
 `nSrcHeight`  
 使用逻辑单位，源矩形的高度。  
  
 `xMask`  
 单色位图左上角 x 坐标。  
  
 `yMask`  
 单色位图左上角 y 坐标。  
  
 `rectSrc`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定源矩形的坐标。  
  
 `pointMask`  
 一个[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，指示掩码位图左上的角。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`hbmMask`标识有效的单色位图， **PlgBit**使用此位图来掩码的源矩形的颜色数据位。  
  
 此方法适用于 Windows NT 中，4.0 版和更高版本的唯一版本。 请参阅[PlgBlt](http://msdn.microsoft.com/library/windows/desktop/dd162804)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]更多详细信息。  
  
##  <a name="a-namereleasedca--cimagereleasedc"></a><a name="releasedc"></a>CImage::ReleaseDC  
 释放设备上下文。  
  
```
void ReleaseDC() const throw();
```  
  
### <a name="remarks"></a>备注  
 由于只有一个位图可以一次选入设备上下文，因此你必须调用`ReleaseDC`每次调用[GetDC](#getdc)。  
  
##  <a name="a-namereleasegdiplusa--cimagereleasegdiplus"></a><a name="releasegdiplus"></a>CImage::ReleaseGDIPlus  
 释放使用的 GDI + 资源。  
  
```
void ReleaseGDIPlus() throw();
```  
  
### <a name="remarks"></a>备注  
 必须先调用此方法，来释放资源分配的全局`CImage`对象。 请参阅[CImage::CImage](#cimage)。  
  
##  <a name="a-namesavea--cimagesave"></a><a name="save"></a>CImage::Save  
 将图像保存到指定的流或文件在磁盘上。  
  
```
HRESULT Save(IStream* pStream,
 REFGUID guidFileType) const throw();

HRESULT Save(LPCTSTR pszFileName,
 REFGUID guidFileType= GUID_NULL) const throw();
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 指向一个包含文件图像数据的 COM IStream 对象的指针。  
  
 *pszFileName*  
 指向图像的文件名的指针。  
  
 `guidFileType`  
 若要保存为图像文件类型。 可以是以下各项之一：  
  
- **ImageFormatBMP**未压缩的位图图像。  
  
- **ImageFormatPNG**可移植网络图形 (PNG) 压缩的映像。  
  
- **ImageFormatJPEG** JPEG 压缩的映像。  
  
- **ImageFormatGIF** GIF 压缩的映像。  
  
> [!NOTE]
>  常量的完整列表，请参阅**图像文件格式常量**中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
### <a name="remarks"></a>备注  
 调用此函数将使用指定的名称和类型的图像存储。 如果`guidFileType`不包含参数，将使用文件名的文件扩展名确定图像格式。 如果未不提供任何扩展，将以 BMP 格式保存图像。  
  
##  <a name="a-namesetcolortablea--cimagesetcolortable"></a><a name="setcolortable"></a>CImage::SetColorTable  
 DIB 部分调色板中设置的条目范围的红、 绿、 蓝 (RGB) 颜色值。  
  
```
void SetColorTable(
  UINT iFirstColor, 
  UINT nColors,
  const RGBQUAD* prgbColors) throw();
```  
  
### <a name="parameters"></a>参数  
 `iFirstColor`  
 要设置的第一个项的颜色表索引。  
  
 `nColors`  
 若要设置的颜色表条目数。  
  
 `prgbColors`  
 指向数组的指针[RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)结构，以设置颜色表项。  
  
### <a name="remarks"></a>备注  
 此方法支持仅 DIB 部分位图。  
  
##  <a name="a-namesetpixela--cimagesetpixel"></a><a name="setpixel"></a>CImage::SetPixel  
 在位图中的给定位置设置像素的颜色。  
  
```
void SetPixel(int x, int y, COLORREF color) throw();
```  
  
### <a name="parameters"></a>参数  
 *x*  
 要设置的像素水平位置。  
  
 *y*  
 要设置的像素垂直位置。  
  
 `color`  
 为其设置像素的颜色。  
  
### <a name="remarks"></a>备注  
 如果像素坐标落在选定的剪辑区域之外，此方法将失败。  
  
##  <a name="a-namesetpixelindexeda--cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage::SetPixelIndexed  
 将像素颜色设置为位于颜色`iIndex`的调色板颜色。  
  
```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```  
  
### <a name="parameters"></a>参数  
 *x*  
 要设置的像素水平位置。  
  
 *y*  
 要设置的像素垂直位置。  
  
 `iIndex`  
 一种颜色在调色板中的索引。  
  
##  <a name="a-namesetpixelrgba--cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage::SetPixelRGB  
 设置由指定的位置处的像素*x*和*y*为所指示的颜色*r*， *g*，和*b*、 为红色，绿色、 蓝 (RGB) 映像。  
  
```
void SetPixelRGB(  
 int x,
 int y,
 BYTE r,
 BYTE g,
 BYTE b) throw();
```  
  
### <a name="parameters"></a>参数  
 *x*  
 要设置的像素水平位置。  
  
 *y*  
 要设置的像素垂直位置。  
  
 *r*  
 红色色彩浓度。  
  
 *g*  
 绿色色彩浓度。  
  
 *b*  
 蓝色色彩浓度。  
  
### <a name="remarks"></a>备注  
 介于 0 和 255 之间的分别表示红色、 绿色和蓝色参数。 如果将所有三个参数设置为零，则组合生成的颜色为黑色。 如果将所有三个参数设置为 255，组合结果色为白色。  
  
##  <a name="a-namesettransparentcolora--cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage::SetTransparentColor  
 设置为透明给定索引位置处的一种颜色。  
  
```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```  
  
### <a name="parameters"></a>参数  
 *iTransparentColor*  
 要将设置为透明的颜色的调色板中的索引。 如果为 –&1;，没有颜色设置为透明。  
  
### <a name="return-value"></a>返回值  
 先前颜色的索引设置为透明。  
  
##  <a name="a-namestretchblta--cimagestretchblt"></a><a name="stretchblt"></a>CImage::StretchBlt  
 将源设备上下文的位图复制到此当前的设备上下文。  
  
```
BOOL StretchBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
 HDC hDestDC,
 const RECT& rectDest,
 DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight,
 DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
 HDC hDestDC,
 const RECT& rectDest,
 const RECT& rectSrc,
 DWORD dwROP = SRCCOPY) const throw();
```  
  
### <a name="parameters"></a>参数  
 `hDestDC`  
 目标设备上下文的句柄。  
  
 `xDest`  
 X 坐标，使用逻辑单位，目标矩形左上角。  
  
 `yDest`  
 Y 坐标，使用逻辑单位，目标矩形左上角。  
  
 `nDestWidth`  
 使用逻辑单位，目标矩形的宽度。  
  
 `nDestHeight`  
 使用逻辑单位，目标矩形的高度。  
  
 `dwROP`  
 要执行的光栅操作。 光栅操作代码定义如何组合源、 目标和模式的位 （如定义当前选择的画笔），将窗体目标。 请参阅[BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]有关其他光栅操作代码及其说明的列表。  
  
 `rectDest`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，用于标识目标。  
  
 `xSrc`  
 X 坐标，使用逻辑单位，源矩形左上角。  
  
 `ySrc`  
 Y 坐标，使用逻辑单位，源矩形左上角。  
  
 `nSrcWidth`  
 使用逻辑单位，源矩形的宽度。  
  
 `nSrcHeight`  
 使用逻辑单位，源矩形的高度。  
  
 `rectSrc`  
 对引用`RECT`结构中，标识的源。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[StretchBlt](http://msdn.microsoft.com/library/windows/desktop/dd145120)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nametransparentblta--cimagetransparentblt"></a><a name="transparentblt"></a>Cimage:: Transparentblt  
 将源设备上下文的位图复制到此当前的设备上下文。  
  
```
BOOL TransparentBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
 HDC hDestDC,
 const RECT& rectDest,
 UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight,
 UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
 HDC hDestDC,
 const RECT& rectDest,
 const RECT& rectSrc,
 UINT crTransparent = CLR_INVALID) const throw();
```  
  
### <a name="parameters"></a>参数  
 `hDestDC`  
 目标设备上下文的句柄。  
  
 `xDest`  
 X 坐标，使用逻辑单位，目标矩形左上角。  
  
 `yDest`  
 Y 坐标，使用逻辑单位，目标矩形左上角。  
  
 `nDestWidth`  
 使用逻辑单位，目标矩形的宽度。  
  
 `nDestHeight`  
 使用逻辑单位，目标矩形的高度。  
  
 *crTransparent*  
 中的源位图被视为透明的颜色。 默认情况下， **CLR_INVALID**，指示应使用当前设置为图像的透明颜色的颜色。  
  
 `rectDest`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，用于标识目标。  
  
 `xSrc`  
 X 坐标，使用逻辑单位，源矩形左上角。  
  
 `ySrc`  
 Y 坐标，使用逻辑单位，源矩形左上角。  
  
 `nSrcWidth`  
 使用逻辑单位，源矩形的宽度。  
  
 `nSrcHeight`  
 使用逻辑单位，源矩形的高度。  
  
 `rectSrc`  
 对引用`RECT`结构中，标识的源。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果成功，否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 `TransparentBlt`适用于 4 位 / 像素和 8 位 / 像素的源位图。 使用[cimage:: Alphablend](#alphablend)来指定每个像素 32 位的位图的透明度。  
  
  
### <a name="example"></a>示例  

```cpp  
// Performs a transparent blit from the source image to the destination 
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage, 
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
  HDC hDstDC = NULL;
  BOOL bResult;

  if(pSrcImage == NULL || pDstImage == NULL)
  {
  // Invalid parameter
  return FALSE;
  }

  // Obtain a DC to the destination image
  hDstDC = pDstImage->GetDC();

  // Perform the blit
  bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

  // Release the destination DC
  pDstImage->ReleaseDC();

  return bResult;
}
```

  
## <a name="see-also"></a>另请参阅  
 [MMXSwarm 示例](../../visual-cpp-samples.md)   
 [SimpleImage 示例](../../visual-cpp-samples.md)   
 [与设备无关位图](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   
 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)
 [设备无关位图](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   










