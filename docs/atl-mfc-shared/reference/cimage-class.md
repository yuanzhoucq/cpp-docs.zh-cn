---
title: CImage 类 |Microsoft Docs
ms.custom: ''
ms.date: 02/01/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd0858763d31e1f46e1cb366154871f06ae7a910
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400401"
---
# <a name="cimage-class"></a>CImage 类

`CImage` 提供了增强的位图支持，包括加载和保存 JPEG、 GIF、 BMP、 和可移植网络图形 (PNG) 格式图像的能力。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CImage
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CImage::CImage](#cimage)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Cimage:: Alphablend](#alphablend)|显示透明或半透明的像素的位图。|
|[CImage::Attach](#attach)|将附加到 HBITMAP`CImage`对象。 可以用于非 DIB 部分位图或 DIB 部分位图。|
|[CImage::BitBlt](#bitblt)|将位图从源设备上下文复制到此当前设备上下文。|
|[CImage::Create](#create)|创建 DIB 部分位图，并将其附加到以前构造`CImage`对象。|
|[CImage::CreateEx](#createex)|创建 DIB 部分位图 （使用其他参数），并将其附加到以前构造`CImage`对象。|
|[CImage::Destroy](#destroy)|从位图中分离`CImage`对象，并销毁位图。|
|[CImage::Detach](#detach)|从位图中分离`CImage`对象。|
|[Cimage:: Draw](#draw)|将位图从源矩形复制到目标矩形。 `Draw` 拉伸或压缩位图以适合目标矩形的尺寸，如有必要，并处理 alpha 值混合处理和透明的颜色。|
|[CImage::GetBits](#getbits)|检索指向位图的实际像素值。|
|[CImage::GetBPP](#getbpp)|检索每个像素的位数。|
|[CImage::GetColorTable](#getcolortable)|从颜色表中的项的范围中检索红、 绿、 蓝 (RGB) 颜色值。|
|[CImage::GetDC](#getdc)|检索在其中选择的当前位图的设备上下文。|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|查找可用的图像格式和及其说明。|
|[CImage::GetHeight](#getheight)|检索当前图像以像素为单位的高度。|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|查找可用的图像格式和及其说明。|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|检索的最大颜色表中的条目数。|
|[CImage::GetPitch](#getpitch)|检索当前的图像，以字节为单位的间距。|
|[CImage::GetPixel](#getpixel)|检索由指定的像素的颜色*x*并*y*。|
|[CImage::GetPixelAddress](#getpixeladdress)|检索给定像素的地址。|
|[CImage::GetTransparentColor](#gettransparentcolor)|检索的透明颜色的颜色表中的位置。|
|[CImage::GetWidth](#getwidth)|检索以像素为单位的当前图像的宽度。|
|[CImage::IsDIBSection](#isdibsection)|确定附加的位图是 DIB 部分。|
|[CImage::IsIndexed](#isindexed)|表示位图的颜色都映射到索引的调色板。|
|[CImage::IsNull](#isnull)|指示当前已加载的源位图。|
|[CImage::IsTransparencySupported](#istransparencysupported)|指示应用程序是否支持透明位图。|
|[CImage::Load](#load)|从指定的文件加载图像。|
|[CImage::LoadFromResource](#loadfromresource)|从指定的资源加载图像。|
|[CImage::MaskBlt](#maskblt)|将组合使用指定的掩码和光栅操作的源和目标位图的颜色数据。|
|[CImage::PlgBlt](#plgblt)|源设备上下文中的矩形从执行位块传输到目标设备上下文中一个平行四边形。|
|[CImage::ReleaseDC](#releasedc)|释放与检索到的设备上下文[CImage::GetDC](#getdc)。|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|释放使用 GDI + 资源。 必须创建的全局释放资源调用`CImage`对象。|
|[CImage::Save](#save)|将图像保存为指定的类型。 `Save` 不能指定图像选项。|
|[CImage::SetColorTable](#setcolortable)|设置红色、 绿色、 蓝色 RGB） 颜色 DIB 部分的颜色表中的条目的一系列中的值。|
|[CImage::SetPixel](#setpixel)|将像素设置为指定的颜色的指定坐标处。|
|[CImage::SetPixelIndexed](#setpixelindexed)|设置颜色的调色板的指定索引处的指定坐标处的像素。|
|[CImage::SetPixelRGB](#setpixelrgb)|将像素设置为指定的红色、 绿色、 蓝 (RGB) 值的指定坐标处。|
|[CImage::SetTransparentColor](#settransparentcolor)|设置为透明效果的颜色来处理索引。 调色板中的只有一个颜色可以是透明的。|
|[CImage::StretchBlt](#stretchblt)|将位图从源矩形复制到目标矩形，拉伸或压缩位图以适合目标矩形的尺寸，如有必要。|
|[CImage::TransparentBlt](#transparentblt)|将源设备上下文透明色的调色板位图复制到此当前设备上下文。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CImage::operator HBITMAP](#operator_hbitmap)|返回附加到的 Windows 句柄`CImage`对象。|

## <a name="remarks"></a>备注

`CImage` 将位图为任一与设备无关位图 (DIB) 部分，或未;但是，可以使用[创建](#create)或[CImage::Load](#load)仅 DIB 部分。 可以将附加到的非 DIB 部分位图`CImage`对象使用[附加](#attach)，但您不能使用以下`CImage`方法，它支持仅 DIB 部分位图：

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

若要确定是否附加的位图 DIB 部分，请调用[IsDibSection](#isdibsection)。

> [!NOTE]
> **请注意**在 Visual Studio.NET 2003 中，此类保留数的计数`CImage`创建的对象。 每当在计数归为 0，该函数`GdiplusShutdown`自动调用以释放使用的 GDI + 资源。 这可确保任何`CImage`创建的 Dll 的直接或间接对象始终正确销毁并且`GdiplusShutdown`不能从调用`DllMain`。

> [!NOTE]
>  使用全局`CImage`不建议在 DLL 中的对象。 如果你需要使用全局`CImage`对象中的 DLL，调用[CImage::ReleaseGDIPlus](#releasegdiplus)来显式释放资源使用的 GDI +。

`CImage` 不能选择到新[CDC](../../mfc/reference/cdc-class.md)。 `CImage` 创建其自己 HDC 的图像。 由于一次仅为一个 HDC 选择 HBITMAP，与关联 HBITMAP`CImage`不能选择到另一个 HDC。 如果您需要 CDC，检索从 HDC`CImage`并将其交给 [CDC::FromHandle] (../../mfc/reference/cdc-class.md#cdc__fromhandle。

## <a name="example"></a>示例

```cpp  
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

当你使用`CImage`在 MFC 项目中，请注意在项目中的成员函数需要指向的指针[CBitmap](../../mfc/reference/cbitmap-class.md)对象。 如果你想要使用`CImage`使用此类函数，如[CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)，使用[CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle)，将其传递你`CImage`HBITMAP，并使用返回`CBitmap*`。  


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


通过`CImage`，有权访问 DIB 部分的实际位。 可以使用`CImage`对象之前使用 Win32 HBITMAP 或 DIB 部分。

可以使用`CImage`从 MFC 或 atl。

> [!NOTE]
>  创建项目使用时`CImage`，则必须定义`CString`包含之前`atlimage.h`。 如果你的项目使用而不使用 MFC ATL，包括`atlstr.h`包含之前`atlimage.h`。 如果你的项目使用 MFC （或它是否与 MFC 支持 ATL 项目），包括`afxstr.h`包含之前`atlimage.h`。  
>   
>  同样，必须包括`atlimage.h`包含之前`atlimpl.cpp`。 若要轻松地完成此操作，包括`atlimage.h`在您`stdafx.h`。

## <a name="requirements"></a>要求

**标头：** atlimage.h

##  <a name="alphablend"></a>  Cimage:: Alphablend

显示透明或半透明的像素的位图。

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

*hDestDC*  
目标设备上下文的句柄。

*xDest*  
X 坐标中的目标矩形左上角的逻辑单元。

*yDest*  
Y 坐标中的目标矩形左上角的逻辑单元。

*bSrcAlpha*  
要用于整个源位图的 alpha 透明度值。 默认值 0xff (255) 假定您的图像是不透明的并且你想要使用仅每像素 alpha 值。

*bBlendOp*  
对源和目标位图、 要应用于整个源位图和源位图的格式信息的全局 alpha 值的 alpha 值混合处理函数。 目前仅限于 AC_SRC_OVER 源和目标 blend 函数。

*pointDest*  
对引用[点](https://msdn.microsoft.com/library/windows/desktop/dd162805)标识中的逻辑单元的目标矩形左上的角的结构。

*nDestWidth*  
使用逻辑单位，目标矩形的宽度。

*nDestHeight*  
使用逻辑单位，目标矩形的高度。

*xSrc*  
源矩形左上角逻辑 x 坐标。

*ySrc*  
源矩形左上角逻辑 y 坐标。

*nSrcWidth*  
使用逻辑单位，源矩形的宽度。

*nSrcHeight*  
使用逻辑单位，源矩形的高度。

*rectDest*  
对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，确定目标。

*rectSrc*  
对引用`RECT`结构，用于标识源。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

Alpha 混合位图支持每个像素的颜色混合。

当*bBlendOp*设置源像素的 alpha 值的目标位图为 AC_SRC_OVER 默认放置源位图。  

##  <a name="attach"></a>  CImage::Attach

将附加*hBitmap*到`CImage`对象。

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>参数

*hBitmap*  
HBITMAP 句柄。

*eOrientation*  
指定位图的方向。 可以是以下各项之一：

- 由操作系统确定 DIBOR_DEFAULT 位图的方向。 但是，这可能始终没有预期的结果在所有操作系统上。 有关这方面的详细信息，请参阅以下知识库文章 (**Q186586**): PRB: getobject （） 始终返回正高度为 DIB 部分。

- DIBOR_BOTTOMUP 位图的行是按相反的顺序。 这将导致[CImage::GetBits](#getbits)返回快要结束的时候位图缓冲区的指针和[CImage::GetPitch](#getpitch)返回一个负数。

- DIBOR_TOPDOWN 位图的行采用自上而下的顺序。 这将导致[CImage::GetBits](#getbits)指针要返回的第一个字节的位图缓冲区并[CImage::GetPitch](#getpitch)要返回的正数值。

### <a name="remarks"></a>备注

位图可以是一个非 DIB 部分位图或 DIB 部分位图。 请参阅[IsDIBSection](#isdibsection)有关可将仅用于 DIB 的方法的列表部分的位图。

##  <a name="bitblt"></a>  CImage::BitBlt

将位图从源设备上下文复制到此当前设备上下文。

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

*hDestDC*  
目标 HDC。

*xDest*  
目标矩形左上角逻辑 x 坐标。

*yDest*  
目标矩形左上角逻辑 y 坐标。

*dwROP*  
要执行的光栅操作。 光栅操作代码定义了如何结合在一起的源、 目标和模式的位 （根据当前选定的画笔的定义） 形成目标。 请参阅[BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) Windows SDK for 其他光栅操作代码及其说明的列表中。

*pointDest*  
一个[点](https://msdn.microsoft.com/library/windows/desktop/dd162805)结构，指示目标矩形左上的角。

*nDestWidth*  
使用逻辑单位，目标矩形的宽度。

*nDestHeight*  
使用逻辑单位，目标矩形的高度。

*xSrc*  
源矩形左上角逻辑 x 坐标。

*ySrc*  
源矩形左上角逻辑 y 坐标。

*rectDest*  
一个[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，指示目标矩形。

*pointSrc*  
一个`POINT`结构，指示源矩形左上的角。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

有关详细信息，请参阅[BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) Windows SDK 中。

##  <a name="cimage"></a>  CImage::CImage

构造 `CImage` 对象。

```
CImage() throw();
```

### <a name="remarks"></a>备注

一旦已构造对象，调用[创建](#create)，[负载](#load)， [LoadFromResource](#loadfromresource)，或者[附加](#attach)将附加到对象的位图。

**请注意**在 Visual Studio 中，此类保留数的计数`CImage`创建的对象。 每当在计数归为 0，该函数`GdiplusShutdown`自动调用以释放使用的 GDI + 资源。 这可确保任何`CImage`创建的 Dll 的直接或间接对象始终正确销毁并且`GdiplusShutdown`不从 DllMain 调用。

使用全局`CImage`不建议在 DLL 中的对象。 如果你需要使用全局`CImage`对象中的 DLL，调用[CImage::ReleaseGDIPlus](#releasegdiplus)来显式释放资源使用的 GDI +。

##  <a name="create"></a>  CImage::Create

创建`CImage`位图，并将其附加到以前构造`CImage`对象。

```
BOOL Create(
int nWidth,
int nHeight,
int nBPP,
DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>参数

*nWidth*  
宽度`CImage`位图，以像素为单位。

*nHeight*  
高度`CImage`位图，以像素为单位。 如果*nHeight*为正，位图是自下而上的 DIB，其源是左下的角。 如果*nHeight*是负数，位图是自上而下的 DIB 和其源是左上的角。

*nBPP*  
位 / 像素的位图中的数字。 通常 4、 8、 16、 24、 或 32。 可以是 1 单色位图或掩码。

*dwFlags*  
指定位图对象是否具有 alpha 通道。 可以是零个或多个以下值的组合：

- *createAlphaChannel*如果只能在*nBPP*为 32，和*eCompression*是 BI_RGB。 如果指定，创建的映像已存储在每个像素 （非 alpha 32 位映像中未使用） 的第 4 个字节中的每个像素的 alpha （透明度） 值。 调用时，会自动使用此 alpha 通道[cimage:: Alphablend](#alphablend)。

> [!NOTE]
>  在调用[cimage:: Draw](#draw)，具有 alpha 通道的映像是自动 alpha 值混合处理到目标。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="createex"></a>  CImage::CreateEx

创建`CImage`位图，并将其附加到以前构造`CImage`对象。

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

*nWidth*  
宽度`CImage`位图，以像素为单位。

*nHeight*  
高度`CImage`位图，以像素为单位。 如果*nHeight*为正，位图是自下而上的 DIB，其源是左下的角。 如果*nHeight*是负数，位图是自上而下的 DIB 和其源是左上的角。

*nBPP*  
位 / 像素的位图中的数字。 通常 4、 8、 16、 24、 或 32。 可以是 1 单色位图或掩码。

*eCompression*  
指定压缩自下而上的位图 （Dib 上而下不能压缩） 的压缩的类型。 可以是以下值之一：

- BI_RGB 格式是未压缩。 指定此值时调用`CImage::CreateEx`等效于调用`CImage::Create`。

- 未压缩 BI_BITFIELDS 格式和颜色表包含三个 DWORD 颜色掩码，每个像素分别指定红色、 绿色和蓝色组件。 此值与 16 和 32 bpp 位图一起使用时有效。

*pdwBitfields*  
仅当使用*eCompression*设置到 BI_BITFIELDS，否则它必须为 NULL。 指向的三个 DWORD 位掩码，指定颜色的红色、 绿色和蓝色组件分别使用每个像素的位数组的指针。 有关限制的位域的信息，请参阅[BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) Windows SDK 中。

*dwFlags*  
指定位图对象是否具有 alpha 通道。 可以是零个或多个以下值的组合：

- *createAlphaChannel*如果只能在*nBPP*为 32，和*eCompression*是 BI_RGB。 如果指定，创建的映像已存储在每个像素 （非 alpha 32 位映像中未使用） 的第 4 个字节中的每个像素的 alpha （透明度） 值。 调用时，会自动使用此 alpha 通道[cimage:: Alphablend](#alphablend)。

   > [!NOTE]
   > 在调用[cimage:: Draw](#draw)，具有 alpha 通道的映像是自动 alpha 值混合处理到目标。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE。 否则为 FALSE。

### <a name="example"></a>示例

以下示例创建一个 100 x 100 像素的位图，使用 16 位进行编码的每个像素。 在给定的 16 位像素，0-3 位进行编码的红色组件、 4-7 位编码绿色，和 8 到 11 位用于对蓝色编码。 其余的 4 位是未使用。  

```cpp  
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>  CImage::Destroy

从位图中分离`CImage`对象，并销毁位图。

```
void Destroy() throw();
```

##  <a name="detach"></a>  CImage::Detach

从位图中分离`CImage`对象。

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>返回值

分离，位图的句柄或如果没有位图已附加，则为 NULL。

##  <a name="draw"></a>  Cimage:: Draw

将位图从源设备上下文复制到当前的设备上下文。

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

*hDestDC*  
目标设备上下文的句柄。

*xDest*  
X 坐标中的目标矩形左上角的逻辑单元。

*yDest*  
Y 坐标中的目标矩形左上角的逻辑单元。

*nDestWidth*  
使用逻辑单位，目标矩形的宽度。

*nDestHeight*  
使用逻辑单位，目标矩形的高度。

*xSrc*  
X 坐标，以逻辑单元的源矩形左上角。

*ySrc*  
Y 坐标，以逻辑单元的源矩形左上角。

*nSrcWidth*  
使用逻辑单位，源矩形的宽度。

*nSrcHeight*  
使用逻辑单位，源矩形的高度。

*rectDest*  
对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，确定目标。

*rectSrc*  
对引用`RECT`结构，用于标识源。

*pointDest*  
对引用[点](https://msdn.microsoft.com/library/windows/desktop/dd162805)标识中的逻辑单元的目标矩形左上的角的结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`Draw` 执行相同的操作[StretchBlt](#stretchblt)，除非映像包含透明的颜色或 alpha 通道。 在这种情况下，`Draw`执行的操作为相同[TransparentBlt](#transparentblt)或[AlphaBlend](#alphablend)所需的方式。

对于版本的`Draw`，未指定源矩形，整个源映像是默认值。 新版`Draw`未指定目标矩形的大小、 源映像的大小是默认值且没有拉伸或收缩时发生。

##  <a name="getbits"></a>  CImage::GetBits

检索指向位图中给定的像素的实际位值。

```
void* GetBits() throw();
```

### <a name="return-value"></a>返回值

指向位图缓冲区的指针。 如果位图，自下而上的 DIB 附近缓冲区末尾的指针点。 如果位图是自上而下的 DIB，指针将指向第一个字节的缓冲区。

### <a name="remarks"></a>备注

使用此指针，以及返回的值[GetPitch](#getpitch)，可以找到并更改图像中的单个像素。

> [!NOTE]
>  此方法支持仅 DIB 部分位图;因此，访问的像素`CImage`对象相同的方式 DIB 部分的像素为单位。 返回的指针指向的位置 （0，0） 像素。

##  <a name="getbpp"></a>  CImage::GetBPP

检索每像素位值。

```
int GetBPP() const throw();
```

### <a name="return-value"></a>返回值

每个像素的比特数。

### <a name="remarks"></a>备注

此值确定的定义每个像素的位数和颜色位图中的最大数目。

1、 4、 8、 16、 24、 或 32，通常是每个像素的位数。 请参阅`biBitCount`的成员[BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376)适用于此值有关的详细信息的 Windows SDK 中。

##  <a name="getcolortable"></a>  CImage::GetColorTable

从控制板的 DIB 部分中的项的范围中检索红、 绿、 蓝 (RGB) 颜色值。

```
void GetColorTable(UINT iFirstColor,
UINT nColors,
RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>参数

*iFirstColor*  
要检索的第一个条目的颜色表索引。

*nColors*  
若要检索的颜色表条目数。

*prgbColors*  
指向数组的指针[RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)结构以检索颜色表条目。

##  <a name="getdc"></a>  CImage::GetDC

检索当前具有到它所选择的映像的设备上下文。

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>返回值

设备上下文的句柄。

### <a name="remarks"></a>备注

每次调用`GetDC`，你必须随后调用[ReleaseDC](#releasedc)。

##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString

查找可用的图像格式保存图像。

```
static HRESULT GetExporterFilterString(CSimpleString& strExporters,
CSimpleArray<GUID>& aguidFileTypes,
LPCTSTR pszAllFilesDescription = NULL,
DWORD dwExclude = excludeDefaultSave,
TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>参数

*strExporters*  
对 `CSimpleString` 对象的引用。 请参阅**备注**有关详细信息。

*aguidFileTypes*  
Guid 的数组，每个元素对应于一个字符串中的文件类型。 在中的示例*pszAllFilesDescription*下面， *aguidFileTypes*[0] 是 GUID_NULL，剩余的数组值是当前的操作系统支持的图像文件格式。

> [!NOTE]
>  常量的完整列表，请参阅**图像文件格式常量**Windows SDK 中。

*pszAllFilesDescription*  
如果此参数不为 NULL，则筛选器字符串将列表的开头带有一个附加的筛选器。 此筛选器将具有的当前值*pszAllFilesDescription*有关其说明，并接受文件列表中的任何其他导出程序支持的任何文件扩展名。

例如：  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes, 
_T("All Image Files"));
```


*dwExclude*  
指定要从列表中排除的文件类型的位标志的集。 允许使用的标志是：

- `excludeGIF` = 0x01 排除 GIF 文件。

- `excludeBMP` = 0x02 不包括 BMP （Windows 位图） 文件。

- `excludeEMF` = 0x04，则不包括 EMF （增强型图元文件） 文件。

- `excludeWMF` = 0x08 排除 WMF （Windows 图元文件） 文件。

- `excludeJPEG` = 0x10 不包括 JPEG 文件。

- `excludePNG` = 0x20 不包括 PNG 文件。

- `excludeTIFF` = 0x40 排除 TIFF 文件。

- `excludeIcon` = 0x80 排除 ICO （Windows 图标） 文件。

- `excludeOther` = 0x80000000 排除上面未列出的任何其他文件类型。

- `excludeDefaultLoad` = 0 表示负载，默认情况下包含类型的所有文件

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` 来保存，这些文件将被排除默认情况下，因为它们通常具有特殊的要求了。

*chSeparator*  
使用图像格式之间的分隔符。 请参阅**备注**有关详细信息。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

可以将生成的格式字符串传递到您的 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)对象公开可用的图像的文件扩展名格式在文件另存为对话框中。

将参数*strExporter*采用格式：

文件 description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;....file 说明*n*&#124;\*.ext *n*&#124;&#124;

其中&#124;由指定的分隔符字符`chSeparator`。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

使用默认分隔符&#124;如果将此字符串传递给 MFC`CFileDialog`对象。 如果将此字符串传递给标准保存文件对话框中，请使用空分隔符 \0。

##  <a name="getheight"></a>  CImage::GetHeight

检索的高度，单位为像素的图像。

```
int GetHeight() const throw();
```

### <a name="return-value"></a>返回值

以像素为单位的图像的高度。

##  <a name="getimporterfilterstring"></a>  CImage::GetImporterFilterString

查找可用的映像格式加载图像。

```
static HRESULT GetImporterFilterString(CSimpleString& strImporters,
CSimpleArray<GUID>& aguidFileTypes,
LPCTSTR pszAllFilesDescription = NULL,
DWORD dwExclude = excludeDefaultLoad,
TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>参数

*strImporters*  
对 `CSimpleString` 对象的引用。 请参阅**备注**有关详细信息。

*aguidFileTypes*  
Guid 的数组，每个元素对应于一个字符串中的文件类型。 在中的示例*pszAllFilesDescription*下面， *aguidFileTypes*[0] 是 GUID_NULL 剩余数组值是当前的操作系统支持的图像文件格式。

> [!NOTE]
>  常量的完整列表，请参阅**图像文件格式常量**Windows SDK 中。

*pszAllFilesDescription*  
如果此参数不为 NULL，则筛选器字符串将列表的开头带有一个附加的筛选器。 此筛选器将具有的当前值*pszAllFilesDescription*有关其说明，并接受文件列表中的任何其他导出程序支持的任何文件扩展名。

例如：  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes, 
_T("All Image Files"));
```


*dwExclude*  
指定要从列表中排除的文件类型的位标志的集。 允许使用的标志是：

- `excludeGIF` = 0x01 排除 GIF 文件。

- `excludeBMP` = 0x02 不包括 BMP （Windows 位图） 文件。

- `excludeEMF` = 0x04，则不包括 EMF （增强型图元文件） 文件。

- `excludeWMF` = 0x08 排除 WMF （Windows 图元文件） 文件。

- `excludeJPEG` = 0x10 不包括 JPEG 文件。

- `excludePNG` = 0x20 不包括 PNG 文件。

- `excludeTIFF` = 0x40 排除 TIFF 文件。

- `excludeIcon` = 0x80 排除 ICO （Windows 图标） 文件。

- `excludeOther` = 0x80000000 排除上面未列出的任何其他文件类型。

- `excludeDefaultLoad` = 0 表示负载，默认情况下包含类型的所有文件

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` 来保存，这些文件将被排除默认情况下，因为它们通常具有特殊的要求了。

*chSeparator*  
使用图像格式之间的分隔符。 请参阅**备注**有关详细信息。

### <a name="remarks"></a>备注

可以将生成的格式字符串传递到您的 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)格式中的对象公开可用的图像的文件扩展名**文件打开**对话框。

将参数*strImporter*采用格式：

文件 description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;....file 说明*n*&#124;\*.ext *n*&#124;&#124;

其中&#124;是由指定的分隔符*chSeparator*。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

使用默认分隔符&#124;如果将此字符串传递给 MFC`CFileDialog`对象。 如果将此字符串传递给一组公共，请使用空分隔符 \0'**文件打开**对话框。

##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries

检索的最大颜色表中的条目数。

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>返回值

颜色表中的条目数。

### <a name="remarks"></a>备注

此方法支持仅 DIB 部分位图。

##  <a name="getpitch"></a>  CImage::GetPitch

检索的图像的间距。

```
int GetPitch() const throw();
```

### <a name="return-value"></a>返回值

图像的音调。 如果返回值为负，位图的自下而上的 DIB 和其源是左下的角。 如果返回值为正，位图是自上而下的 DIB，其源是左上的角。

### <a name="remarks"></a>备注

间距是以字节为单位，表示一个位图行的开头的两个内存地址和下一步的位图行的开头之间的距离。 间距以字节为单位，因为图像的音调可帮助您确定像素格式。 间距还可以包含额外的内存，为位图保留。

使用`GetPitch`与[GetBits](#getbits)查找单个像素的图像。

> [!NOTE]
>  此方法支持仅 DIB 部分位图。

##  <a name="getpixel"></a>  CImage::GetPixel

检索指定的位置处的像素的颜色*x*并*y*。

```
COLORREF GetPixel(int x,int y) const throw();
```

### <a name="parameters"></a>参数

*x*  
像素的 x 坐标。

*y*  
像素的 y 坐标。

### <a name="return-value"></a>返回值

红色、 绿色、 蓝色 (RGB) 像素的值。 如果像素的当前剪辑区域之外，返回值将为 CLR_INVALID。

##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress

检索一个像素的确切地址。

```
void* GetPixelAddress(int x,int y) throw();
```

### <a name="parameters"></a>参数

*x*  
像素的 x 坐标。

*y*  
像素的 y 坐标。

### <a name="remarks"></a>备注

根据的像素坐标、 位图和每像素位数间距，确定该地址。

对于具有小于 8 位 / 像素的格式，此方法返回包含像素的字节的地址。 例如，如果您的图像格式具有每像素 4 位`GetPixelAddress`返回字节，并且您的第一个像素的地址必须为每个字节的 2 个像素计算。

> [!NOTE]
>  此方法支持仅 DIB 部分位图。

##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor

检索颜色调色板中的透明颜色的索引的位置。

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>返回值

透明颜色的索引。

##  <a name="getwidth"></a>  CImage::GetWidth

检索的宽度，单位为像素的图像。

```
int GetWidth() const throw();
```

### <a name="return-value"></a>返回值

位图，以像素为单位的宽度。

##  <a name="isdibsection"></a>  CImage::IsDIBSection

确定附加的位图是 DIB 部分。

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>返回值

如果附加的位图是 DIB 部分，则为 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

如果位图不是 DIB 部分，则无法使用以下`CImage`方法，它支持仅 DIB 部分位图：

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>  CImage::IsIndexed

确定位图的像素将映射到调色板颜色。

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>返回值

编制索引; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法返回 TRUE，仅当位图为 8 位 （256 色） 或更少。

> [!NOTE]
>  此方法支持仅 DIB 部分位图。

##  <a name="isnull"></a>  CImage::IsNull

确定当前已加载位图。

```
bool IsNull() const throw();
```

### <a name="remarks"></a>备注

如果当前未加载位图; 此方法返回 TRUE否则为 FALSE。

##  <a name="istransparencysupported"></a>  CImage::IsTransparencySupported

指示应用程序是否支持透明位图。

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>返回值

如果当前平台支持透明度，非零值。 否则为 0。

### <a name="remarks"></a>备注

如果返回值为非零值，并且支持透明度，则调用[AlphaBlend](#alphablend)， [TransparentBlt](#transparentblt)，或[绘制](#draw)将处理透明的颜色。

##  <a name="load"></a>  CImage::Load

加载图像。

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>参数

*pszFileName*  
指向包含要加载的图像文件的名称的字符串的指针。

*pStream*  
指向包含要加载的图像文件的名称的流的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

加载指定的图像*pszFileName*或*pStream*。

有效的图像类型是 BMP、 GIF、 JPEG、 PNG 和 TIFF。

##  <a name="loadfromresource"></a>  CImage::LoadFromResource

从位图资源加载图像。

```
void LoadFromResource(
HINSTANCE hInstance,
LPCTSTR pszResourceName) throw();

void LoadFromResource(
HINSTANCE hInstance,
UINT nIDResource) throw();
```

### <a name="parameters"></a>参数

*hInstance*  
包含要加载的图像的模块的实例的句柄。

*pszResourceName*  
指向包含的包含要加载的图像的资源名称的字符串的指针。

*nIDResource*  
若要加载的资源 ID。

### <a name="remarks"></a>备注

资源必须是类型的位图。

##  <a name="maskblt"></a>  CImage::MaskBlt

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

*hDestDC*  
其可执行文件包含资源的模块句柄。

*xDest*  
X 坐标中的目标矩形左上角的逻辑单元。

*yDest*  
Y 坐标中的目标矩形左上角的逻辑单元。

*nDestWidth*  
使用逻辑单位，目标矩形和源位图的宽度。

*nDestHeight*  
使用逻辑单位，目标矩形和源位图的高度。

*xSrc*  
源位图左上角逻辑 x 坐标。

*ySrc*  
源位图左上角逻辑 y 坐标。

*hbmMask*  
结合使用与源设备上下文中颜色位图的单色掩码位图的句柄。

*xMask*  
通过指定的掩码位图的水平像素偏移量*hbmMask*参数。

*yMask*  
通过指定的掩码位图的垂直像素偏移量*hbmMask*参数。

*dwROP*  
指定该方法用来控制数据源和目标数据的组合的前景色和背景三元光栅操作代码。 后台光栅操作代码存储在此值; 高序位字的高序位字节前景色光栅操作代码存储在此值; 高序位字的低序位字节此值的低序位字将被忽略，并且应为零。 前景色和背景，此方法的上下文中的讨论，请参阅`MaskBlt`Windows SDK 中。 常见的光栅操作代码的列表，请参阅`BitBlt`Windows SDK 中。

*rectDest*  
对引用`RECT`结构，确定目标。

*pointSrc*  
一个`POINT`结构，指示源矩形左上的角。

*pointMask*  
一个`POINT`结构，指示掩码位图左上的角。

*pointDest*  
对引用`POINT`标识中的逻辑单元的目标矩形左上的角的结构。

### <a name="return-value"></a>返回值

非零，如果成功，否则为 0。

### <a name="remarks"></a>备注

此方法适用于 Windows NT，版本 4.0 及更高版本。

##  <a name="operator_hbitmap"></a>  CImage::operator HBITMAP

此运算符用于获取附加的 Windows GDI 句柄的`CImage`对象。 此运算符是强制转换运算符，支持直接使用 HBITMAP 对象。

##  <a name="plgblt"></a>  CImage::PlgBlt

源设备上下文中的矩形从执行位块传输到目标设备上下文中一个平行四边形。

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

*hDestDC*  
目标设备上下文的句柄。

*pPoints*  
指向数组的逻辑空间的标识的目标的平行四边形的三个角的三个点的指针。 源矩形左上的角映射到此数组，此数组中的第二个点的右上角和第三个点到左下的角中的第一个点。 源矩形的右下角将映射到的平行四边形中的隐式第四个点。

*hbmMask*  
用于屏蔽源矩形的颜色的可选单色位图句柄。

*xSrc*  
X 坐标，以逻辑单元的源矩形左上角。

*ySrc*  
Y 坐标，以逻辑单元的源矩形左上角。

*nSrcWidth*  
使用逻辑单位，源矩形的宽度。

*nSrcHeight*  
使用逻辑单位，源矩形的高度。

*xMask*  
单色位图左上角 x 坐标。

*yMask*  
单色位图左上角 y 坐标。

*rectSrc*  
对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它指定源矩形的坐标。

*pointMask*  
一个[点](https://msdn.microsoft.com/library/windows/desktop/dd162805)结构，指示掩码位图左上的角。

### <a name="return-value"></a>返回值

非零，如果成功，否则为 0。

### <a name="remarks"></a>备注

如果*hbmMask*标识有效的单色位图，`PlgBit`使用此位图掩码中的源矩形的颜色数据的位。

此方法适用于 Windows NT，版本 4.0 及更高版本。 请参阅[PlgBlt](/windows/desktop/api/wingdi/nf-wingdi-plgblt)适用于更多详细信息的 Windows SDK 中。

##  <a name="releasedc"></a>  CImage::ReleaseDC

释放设备上下文。

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>备注

由于只有一个位图可以一次选入设备上下文，因此你必须调用`ReleaseDC`每次调用[GetDC](#getdc)。

##  <a name="releasegdiplus"></a>  CImage::ReleaseGDIPlus

释放使用 GDI + 资源。

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>备注

必须在调用此方法，来释放资源分配的全局`CImage`对象。 请参阅[CImage::CImage](#cimage)。

##  <a name="save"></a>  CImage::Save

将图像保存到指定的流或文件在磁盘上。

```
HRESULT Save(IStream* pStream,
REFGUID guidFileType) const throw();

HRESULT Save(LPCTSTR pszFileName,
REFGUID guidFileType= GUID_NULL) const throw();
```

### <a name="parameters"></a>参数

*pStream*  
指向包含文件的图像数据的 COM IStream 对象的指针。

*pszFileName*  
指向图像的文件名称的指针。

*guidFileType*  
若要保存为图像文件类型。 可以是以下各项之一：

- `ImageFormatBMP` 未压缩的位图图像。

- `ImageFormatPNG` 可移植网络图形 (PNG) 的压缩的映像。

- `ImageFormatJPEG` JPEG 压缩的映像。

- `ImageFormatGIF` GIF 压缩的映像。

> [!NOTE]
>  常量的完整列表，请参阅**图像文件格式常量**Windows SDK 中。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

调用此函数可保存使用指定的名称和类型的映像。 如果*guidFileType*不包括参数，将使用文件名的文件扩展名确定图像格式。 如果没有扩展提供，图像将保存在 BMP 格式。

##  <a name="setcolortable"></a>  CImage::SetColorTable

DIB 部分控制板中设置的条目范围的红色、 绿色、 蓝色 (RGB) 颜色值。

```
void SetColorTable(
    UINT iFirstColor, 
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>参数

*iFirstColor*  
要设置的第一个条目的颜色表索引。

*nColors*  
若要设置的颜色表条目数。

*prgbColors*  
指向数组的指针[RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)结构，以设置颜色表条目。

### <a name="remarks"></a>备注

此方法支持仅 DIB 部分位图。

##  <a name="setpixel"></a>  CImage::SetPixel

在位图中的给定位置设置的像素的颜色。

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>参数

*x*  
要设置的像素的水平位置。

*y*  
要设置的像素的垂直位置。

*颜色*  
为其设置像素的颜色。

### <a name="remarks"></a>备注

如果像素坐标欺骗的所选的剪辑区域之外，此方法将失败。

##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed

将像素颜色设置为位于的颜色*iIndex*调色板中。

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>参数

*x*  
要设置的像素的水平位置。

*y*  
要设置的像素的垂直位置。

*iIndex*  
一种颜色的调色板中的索引。

##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB

在指定的位置设置像素*x*并*y*到所指示的颜色*r*， *g*，和*b*、 为红色，绿色、 蓝色 (RGB) 映像。

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
要设置的像素的水平位置。

*y*  
要设置的像素的垂直位置。

*r*  
红色颜色的强度。

*g*  
绿色颜色的强度。

*b*  
蓝色颜色的强度。

### <a name="remarks"></a>备注

每个都由介于 0 和 255 之间的数字表示红色、 绿色和蓝色参数。 如果将所有三个参数设置为零，组合生成的颜色为黑色。 如果将所有三个参数设置为 255，组合生成的颜色为白色。

##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor

设置为透明给定索引位置处的一种颜色。

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>参数

*iTransparentColor*  
要设置为透明的颜色的调色板中的索引。 如果为-1，没有颜色设置为透明。

### <a name="return-value"></a>返回值

以前，颜色的索引设置为透明效果。

##  <a name="stretchblt"></a>  CImage::StretchBlt

将位图从源设备上下文复制到此当前设备上下文。

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

*hDestDC*  
目标设备上下文的句柄。

*xDest*  
X 坐标中的目标矩形左上角的逻辑单元。

*yDest*  
Y 坐标中的目标矩形左上角的逻辑单元。

*nDestWidth*  
使用逻辑单位，目标矩形的宽度。

*nDestHeight*  
使用逻辑单位，目标矩形的高度。

*dwROP*  
要执行的光栅操作。 光栅操作代码定义了如何结合在一起的源、 目标和模式的位 （根据当前选定的画笔的定义） 形成目标。 请参阅[BitBlt](/windows/desktop/api/wingdi/nf-wingdi-bitblt) Windows SDK for 其他光栅操作代码及其说明的列表中。

*rectDest*  
对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，确定目标。

*xSrc*  
X 坐标，以逻辑单元的源矩形左上角。

*ySrc*  
Y 坐标，以逻辑单元的源矩形左上角。

*nSrcWidth*  
使用逻辑单位，源矩形的宽度。

*nSrcHeight*  
使用逻辑单位，源矩形的高度。

*rectSrc*  
对引用`RECT`结构，用于标识源。

### <a name="return-value"></a>返回值

非零，如果成功，否则为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅[StretchBlt](/windows/desktop/api/wingdi/nf-wingdi-stretchblt) Windows SDK 中。

##  <a name="transparentblt"></a>  CImage::TransparentBlt

将位图从源设备上下文复制到此当前设备上下文。

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

*hDestDC*  
目标设备上下文的句柄。

*xDest*  
X 坐标中的目标矩形左上角的逻辑单元。

*yDest*  
Y 坐标中的目标矩形左上角的逻辑单元。

*nDestWidth*  
使用逻辑单位，目标矩形的宽度。

*nDestHeight*  
使用逻辑单位，目标矩形的高度。

*crTransparent*  
中要被视为透明的源位图的颜色。 通过默认情况下，CLR_INVALID，指示应使用当前设置为图像的透明色的颜色。

*rectDest*  
对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，确定目标。

*xSrc*  
X 坐标，以逻辑单元的源矩形左上角。

*ySrc*  
Y 坐标，以逻辑单元的源矩形左上角。

*nSrcWidth*  
使用逻辑单位，源矩形的宽度。

*nSrcHeight*  
使用逻辑单位，源矩形的高度。

*rectSrc*  
对引用`RECT`结构，用于标识源。

### <a name="return-value"></a>返回值

如果成功，否则为 FALSE，则为 TRUE。

### <a name="remarks"></a>备注

`TransparentBlt` 支持的每个像素和 8 位每像素 4 位的源位图。 使用[cimage:: Alphablend](#alphablend)使用透明度指定每个像素 32 位的位图。


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


## <a name="see-also"></a>请参阅

[MMXSwarm 示例](../../visual-cpp-samples.md)<br/>
[SimpleImage 示例](../../visual-cpp-samples.md)<br/>
[与设备无关位图](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)<br/>
[与设备无关位图](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)   

