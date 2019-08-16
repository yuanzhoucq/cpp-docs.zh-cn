---
title: CImage 类
ms.date: 02/01/2018
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
ms.openlocfilehash: 6c651f160fdab582b769cf1764add2cc482745bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491333"
---
# <a name="cimage-class"></a>CImage 类

`CImage`提供增强的位图支持, 包括以 JPEG、GIF、BMP 和可移植网络图形 (PNG) 格式加载和保存图像的功能。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

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
|[CImage::AlphaBlend](#alphablend)|显示具有透明或半透明像素的位图。|
|[CImage::Attach](#attach)|将 HBITMAP 附加到`CImage`对象。 可与非 DIB 部分位图或 DIB 部分位图一起使用。|
|[CImage::BitBlt](#bitblt)|将位图从源设备上下文复制到此当前设备上下文。|
|[CImage::Create](#create)|创建一个 DIB 节位图, 并将其附加到前面`CImage`构造的对象。|
|[CImage::CreateEx](#createex)|创建一个 DIB 节位图 (其中包含附加参数), 并将其附加到`CImage`前面构造的对象。|
|[CImage::Destroy](#destroy)|将位图与`CImage`对象分离并销毁位图。|
|[CImage::Detach](#detach)|将位图与`CImage`对象分离。|
|[CImage::Draw](#draw)|将位图从源矩形复制到目标矩形。 `Draw`拉伸或压缩位图以适合目标矩形的尺寸 (如有必要), 并处理 alpha 混合和透明颜色。|
|[CImage::GetBits](#getbits)|检索指向位图的实际像素值的指针。|
|[CImage::GetBPP](#getbpp)|检索每个像素的位数。|
|[CImage::GetColorTable](#getcolortable)|检索颜色表中某一范围的项中的红色、绿色、蓝色 (RGB) 颜色值。|
|[CImage::GetDC](#getdc)|检索要在其中选择当前位图的设备上下文。|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|查找可用的图像格式及其说明。|
|[CImage::GetHeight](#getheight)|检索当前图像的高度 (以像素为单位)。|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|查找可用的图像格式及其说明。|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|检索颜色表中的最大项数。|
|[CImage::GetPitch](#getpitch)|检索当前图像的间距 (以字节为单位)。|
|[CImage::GetPixel](#getpixel)|检索*x*和*y*指定的像素的颜色。|
|[CImage::GetPixelAddress](#getpixeladdress)|检索给定像素的地址。|
|[CImage::GetTransparentColor](#gettransparentcolor)|检索颜色表中透明色的位置。|
|[CImage::GetWidth](#getwidth)|检索当前图像的宽度 (以像素为单位)。|
|[CImage::IsDIBSection](#isdibsection)|确定附加位图是否为 DIB 部分。|
|[CImage::IsIndexed](#isindexed)|指示位图的颜色映射到索引调色板。|
|[CImage::IsNull](#isnull)|指示源位图当前是否已加载。|
|[CImage::IsTransparencySupported](#istransparencysupported)|指示应用程序是否支持透明位图。|
|[CImage::Load](#load)|从指定的文件加载图像。|
|[CImage::LoadFromResource](#loadfromresource)|从指定的资源加载图像。|
|[CImage::MaskBlt](#maskblt)|使用指定的掩码和光栅操作合并源和目标位图的颜色数据。|
|[CImage::PlgBlt](#plgblt)|执行从源设备上下文中的矩形到目标设备上下文中的平行四边形的位块传输。|
|[CImage::ReleaseDC](#releasedc)|释放用[CImage:: GetDC](#getdc)检索到的设备上下文。|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|释放 GDI + 使用的资源。 必须调用才能释放由全局`CImage`对象创建的资源。|
|[CImage::Save](#save)|将图像另存为指定类型。 `Save`无法指定图像选项。|
|[CImage::SetColorTable](#setcolortable)|设置 DIB 部分的颜色表中的一系列条目中的红色、绿色、蓝色 RGB) 颜色值。|
|[CImage::SetPixel](#setpixel)|将指定坐标处的像素设置为指定的颜色。|
|[CImage::SetPixelIndexed](#setpixelindexed)|将指定坐标处的像素设置为调色板指定索引处的颜色。|
|[CImage::SetPixelRGB](#setpixelrgb)|将指定坐标处的像素设置为指定的红色、绿色、蓝色 (RGB) 值。|
|[CImage::SetTransparentColor](#settransparentcolor)|设置要被视为透明的颜色的索引。 调色板中只有一种颜色可以是透明的。|
|[CImage::StretchBlt](#stretchblt)|如有必要, 将位图从源矩形复制到目标矩形, 拉伸或压缩位图以适合目标矩形的尺寸。|
|[CImage::TransparentBlt](#transparentblt)|将具有透明色的位图从源设备上下文复制到此当前设备上下文。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CImage:: operator HBITMAP](#operator_hbitmap)|返回附加到`CImage`对象的 Windows 句柄。|

## <a name="remarks"></a>备注

`CImage`采用与设备无关的位图 (DIB) 部分的位图; 否则为。但是, 可以使用[Create](#create)或[CImage:: Load](#load) , 只使用 DIB 部分。 您可以使用[attach](#attach)将非 DIB 部分位图附加`CImage`到`CImage`对象, 但随后不能使用以下方法, 这种方法仅支持 DIB 部分位图:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

若要确定附加位图是否为 DIB 部分, 请调用[IsDibSection](#isdibsection)。

> [!NOTE]
> 在 Visual Studio .net 2003 中, 此类保留创建的`CImage`对象数的计数。 每当计数为0时, 将自动调用`GdiplusShutdown`函数以释放 gdi + 使用的资源。 这可确保由`CImage` dll 直接或间接创建的任何对象始终会正确销毁`GdiplusShutdown`并且不会从中`DllMain`调用。

> [!NOTE]
> 不建议`CImage`在 DLL 中使用全局对象。 如果需要在 DLL 中使用全局`CImage`对象, 请调用[CImage:: ReleaseGDIPlus](#releasegdiplus)以显式释放 gdi + 所使用的资源。

`CImage`不能选择新的[CDC](../../mfc/reference/cdc-class.md)。 `CImage`为图像创建自己的 HDC。 由于一次只能选择一个 HBITMAP, 因此`CImage`不能将与关联的 HBITMAP 选择到另一个 hdc。 如果需要 CDC, 请从中`CImage`检索 HDC, 并将其赋给[CDC:: FromHandle](../../mfc/reference/cdc-class.md#fromhandle)。

## <a name="example"></a>示例

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

在 MFC 项目`CImage`中使用时, 请注意, 项目中的哪些成员函数需要指向[CBitmap](../../mfc/reference/cbitmap-class.md)对象的指针。 如果`CImage`要将用于此类函数 (如[CMenu:: AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)), 请使用[CBitmap:: FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), 将其传递`CImage`给你的 HBITMAP, 并`CBitmap*`使用返回的。

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

通过`CImage`, 你可以访问 DIB 部分的实际位。 你可以在以前`CImage`使用 Win32 HBITMAP 或 DIB 部分的任何位置使用对象。

可以从 MFC `CImage`或 ATL 使用。

> [!NOTE]
> 使用`CImage`创建项目时, 必须先定义`CString` , 然后再添加`atlimage.h`。 如果你的项目使用不带 MFC 的`atlstr.h` ATL, 请`atlimage.h`在包含之前包括。 如果你的项目使用 mfc (或者, 如果它是包含 mfc 支持的 ATL 项目) `afxstr.h` , 请在`atlimage.h`添加之前包括。<br/>
> <br/>
> 同样, 在包括`atlimage.h` `atlimpl.cpp`之前, 必须包括。 若要轻松实现此目的`atlimage.h` , 请`stdafx.h`将包含在中。

## <a name="requirements"></a>要求

**标头:** atlimage

##  <a name="alphablend"></a>CImage:: AlphaBlend

显示具有透明或半透明像素的位图。

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

*hDestDC*<br/>
目标设备上下文的句柄。

*xDest*<br/>
目标矩形左上角的 x 坐标 (以逻辑单位表示)。

*yDest*<br/>
目标矩形左上角的 y 坐标 (以逻辑单位表示)。

*bSrcAlpha*<br/>
要用于整个源位图的 alpha 透明度值。 默认的 0xff (255) 假设您的图像是不透明的, 并且您希望只使用每像素的 alpha 值。

*bBlendOp*<br/>
用于源和目标位图的 alpha 混合函数、要应用于整个源位图的全局 alpha 值以及源位图的格式信息。 源和目标 blend 函数当前限制为 AC_SRC_OVER。

*pointDest*<br/>
对用于标识目标矩形左上角的[点](/previous-versions/dd162805\(v=vs.85\))结构的引用 (以逻辑单元表示)。

*nDestWidth*<br/>
目标矩形的宽度 (以逻辑单位为单位)。

*nDestHeight*<br/>
目标矩形的高度 (以逻辑单位为单位)。

*xSrc*<br/>
源矩形左上角的逻辑 x 坐标。

*ySrc*<br/>
源矩形左上角的逻辑 y 坐标。

*nSrcWidth*<br/>
源矩形的宽度 (以逻辑单位为单位)。

*nSrcHeight*<br/>
源矩形的高度 (以逻辑单位为单位)。

*rectDest*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用, 该结构标识目标。

*rectSrc*<br/>
对`RECT`结构的引用, 标识源。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

Alpha blend 位图支持每个像素的颜色混合。

当*bBlendOp*设置为 AC_SRC_OVER 的默认值时, 将基于源像素的 alpha 值将源位图放置在目标位图上。

##  <a name="attach"></a>CImage:: Attach

将*hBitmap*附加到`CImage`对象。

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
HBITMAP 的句柄。

*eOrientation*<br/>
指定位图的方向。 可以是以下各项之一：

- DIBOR_DEFAULT 位图的方向取决于操作系统。

- DIBOR_BOTTOMUP 位图的行顺序相反。 这将导致[CImage:: GetBits](#getbits)在位图缓冲区的末尾附近返回指针, 并使[CImage:: GetPitch](#getpitch)返回负数。

- DIBOR_TOPDOWN 位图的行按从上到下的顺序排列。 这将导致[CImage:: GetBits](#getbits)返回指向位图缓冲区的第一个字节的指针, 并使[CImage:: GetPitch](#getpitch)返回一个正数。

### <a name="remarks"></a>备注

位图可以是非 DIB 部分位图或 DIB 节位图。 有关只能与 DIB 部分位图一起使用的方法列表, 请参阅[IsDIBSection](#isdibsection) 。

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

*hDestDC*<br/>
目标 HDC。

*xDest*<br/>
目标矩形左上角的逻辑 x 坐标。

*yDest*<br/>
目标矩形左上角的逻辑 y 坐标。

*dwROP*<br/>
要执行的光栅运算。 光栅操作代码定义了如何将源、目标和模式的位 (由当前选定的画笔定义) 组合在一起以形成目标。 请参阅 Windows SDK 中的[BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt)以获取其他光栅操作代码及其说明的列表。

*pointDest*<br/>
指示目标矩形左上角的[点](/previous-versions/dd162805\(v=vs.85\))结构。

*nDestWidth*<br/>
目标矩形的宽度 (以逻辑单位为单位)。

*nDestHeight*<br/>
目标矩形的高度 (以逻辑单位为单位)。

*xSrc*<br/>
源矩形左上角的逻辑 x 坐标。

*ySrc*<br/>
源矩形左上角的逻辑 y 坐标。

*rectDest*<br/>
指示目标矩形的[矩形](/previous-versions/dd162897\(v=vs.85\))结构。

*pointSrc*<br/>
指示源矩形左上角的结构。`POINT`

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 。

##  <a name="cimage"></a>CImage:: CImage

构造 `CImage` 对象。

```
CImage() throw();
```

### <a name="remarks"></a>备注

构造对象后, 调用[Create](#create)、 [Load](#load)、 [LoadFromResource](#loadfromresource)或[attach](#attach)将位图附加到对象。

**注意**在 Visual Studio 中, 此类保留创建的`CImage`对象数的计数。 每当计数为0时, 将自动调用`GdiplusShutdown`函数以释放 gdi + 使用的资源。 这可确保由`CImage` dll 直接或间接创建的任何对象始终会正确销毁`GdiplusShutdown`并且不会从 DllMain 中调用。

不建议`CImage`在 DLL 中使用全局对象。 如果需要在 DLL 中使用全局`CImage`对象, 请调用[CImage:: ReleaseGDIPlus](#releasegdiplus)以显式释放 gdi + 所使用的资源。

##  <a name="create"></a>CImage:: Create

创建位图, 并将其附加到前面构造`CImage`的对象。 `CImage`

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>参数

*nWidth*<br/>
`CImage`位图的宽度 (以像素为单位)。

*nHeight*<br/>
`CImage`位图的高度 (以像素为单位)。 如果*nHeight*为正, 则位图为自下而上的 DIB, 其原点为左下角。 如果*nHeight*为负, 则位图为自顶向下的 DIB, 其原点为左上角。

*nBPP*<br/>
位图中每个像素的位数。 通常为4、8、16、24或32。 对于单色位图或掩码, 可以为1。

*dwFlags*<br/>
指定位图对象是否具有 alpha 通道。 可以是零个或多个以下值的组合:

- *createAlphaChannel*仅当*nBPP*为 32, 并且*eCompression*为 BI_RGB 时才可使用。 如果已指定, 则创建的图像对于每个像素都有一个 alpha (透明度) 值, 存储在每个像素的第4个字节 (非 alpha 32 位图像中)。 调用[CImage:: AlphaBlend](#alphablend)时, 将自动使用此 alpha 通道。

> [!NOTE]
> 在对 CImage 的调用中[::D raw](#draw), 具有 alpha 通道的图像会自动将 alpha 混合到目标。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="createex"></a>CImage:: CreateEx

创建位图, 并将其附加到前面构造`CImage`的对象。 `CImage`

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

*nWidth*<br/>
`CImage`位图的宽度 (以像素为单位)。

*nHeight*<br/>
`CImage`位图的高度 (以像素为单位)。 如果*nHeight*为正, 则位图为自下而上的 DIB, 其原点为左下角。 如果*nHeight*为负, 则位图为自顶向下的 DIB, 其原点为左上角。

*nBPP*<br/>
位图中每个像素的位数。 通常为4、8、16、24或32。 对于单色位图或掩码, 可以为1。

*eCompression*<br/>
指定压缩的下边缘位图的压缩类型 (无法压缩自顶向下的 Dib)。 可以是以下值之一：

- BI_RGB 格式未压缩。 如果调用`CImage::CreateEx`等效于调用`CImage::Create`, 则指定此值。

- BI_BITFIELDS 格式未压缩, 颜色表由三个 DWORD 颜色掩码组成, 分别指定每个像素的红色、绿色和蓝色成分。 此项在与16和 32 bpp 位图一起使用时有效。

*pdwBitfields*<br/>
仅当*eCompression*设置为 BI_BITFIELDS 时才使用, 否则它必须为 NULL。 一个指针, 指向三个 DWORD 位掩码的数组, 分别指定每个像素的哪些位分别用于颜色的红色、绿色和蓝色分量。 有关位域限制的信息, 请参阅 "Windows SDK 中的" [BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) "。

*dwFlags*<br/>
指定位图对象是否具有 alpha 通道。 可以是零个或多个以下值的组合:

- *createAlphaChannel*仅当*nBPP*为 32, 并且*eCompression*为 BI_RGB 时才可使用。 如果已指定, 则创建的图像对于每个像素都有一个 alpha (透明度) 值, 存储在每个像素的第4个字节 (非 alpha 32 位图像中)。 调用[CImage:: AlphaBlend](#alphablend)时, 将自动使用此 alpha 通道。

   > [!NOTE]
   > 在对 CImage 的调用中[::D raw](#draw), 具有 alpha 通道的图像会自动将 alpha 混合到目标。

### <a name="return-value"></a>返回值

如果成功, 则为 TRUE。 否则为 FALSE。

### <a name="example"></a>示例

下面的示例创建一个100x100 像素位图, 使用16位对每个像素进行编码。 在给定的16位像素中, bits 0-3 对红色分量进行编码, bits 4-7 编码为绿色, 位8-11 编码为蓝色。 其余4位未使用。

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>CImage::D estroy

将位图与`CImage`对象分离并销毁位图。

```
void Destroy() throw();
```

##  <a name="detach"></a>  CImage::Detach

从`CImage`对象分离位图。

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>返回值

已分离的位图的句柄; 如果未附加位图, 则为 NULL。

##  <a name="draw"></a>CImage::D raw

将位图从源设备上下文复制到当前设备上下文。

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

*hDestDC*<br/>
目标设备上下文的句柄。

*xDest*<br/>
目标矩形左上角的 x 坐标 (以逻辑单位表示)。

*yDest*<br/>
目标矩形左上角的 y 坐标 (以逻辑单位表示)。

*nDestWidth*<br/>
目标矩形的宽度 (以逻辑单位为单位)。

*nDestHeight*<br/>
目标矩形的高度 (以逻辑单位为单位)。

*xSrc*<br/>
源矩形左上角的 x 坐标 (以逻辑单位表示)。

*ySrc*<br/>
源矩形左上角的 y 坐标 (以逻辑单位表示)。

*nSrcWidth*<br/>
源矩形的宽度 (以逻辑单位为单位)。

*nSrcHeight*<br/>
源矩形的高度 (以逻辑单位为单位)。

*rectDest*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用, 该结构标识目标。

*rectSrc*<br/>
对`RECT`结构的引用, 标识源。

*pointDest*<br/>
对用于标识目标矩形左上角的[点](/previous-versions/dd162805\(v=vs.85\))结构的引用 (以逻辑单元表示)。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`Draw`执行与[StretchBlt](#stretchblt)相同的操作, 除非图像包含透明颜色或 alpha 通道。 在这种情况`Draw`下, 将根据需要执行与[TransparentBlt](#transparentblt)或[AlphaBlend](#alphablend)相同的操作。

对于未指定`Draw`源矩形的的版本, 将默认为整个源映像。 对于未指定目标`Draw`矩形大小的的版本, 源映像的大小是默认值, 不会进行拉伸或收缩。

##  <a name="getbits"></a>CImage:: GetBits

检索一个指针, 该指针指向位图中给定像素的实际位值。

```
void* GetBits() throw();
```

### <a name="return-value"></a>返回值

指向位图缓冲区的指针。 如果位图是自下而上的 DIB, 则指针指向缓冲区末尾附近。 如果位图是自顶向下的 DIB, 则指针指向缓冲区的第一个字节。

### <a name="remarks"></a>备注

使用此指针以及[GetPitch](#getpitch)返回的值, 您可以在图像中找到并更改各个像素。

> [!NOTE]
> 此方法仅支持 DIB 节位图;因此, 您可以通过与 DIB 部分`CImage`的像素相同的方式访问对象的像素。 返回的指针指向位置 (0, 0) 处的像素。

##  <a name="getbpp"></a>  CImage::GetBPP

检索每像素位的值。

```
int GetBPP() const throw();
```

### <a name="return-value"></a>返回值

每像素位数。

### <a name="remarks"></a>备注

此值决定了用于定义位图中每个像素和最大颜色数的位数。

每像素位数通常为1、4、8、16、24或32。 有关此值的详细信息, 请参阅 Windows SDK 中[BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\))的成员。`biBitCount`

##  <a name="getcolortable"></a>  CImage::GetColorTable

从 DIB 部分调色板中的一系列项中检索红色、绿色、蓝色 (RGB) 颜色值。

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>参数

*iFirstColor*<br/>
要检索的第一个项的颜色表索引。

*nColors*<br/>
要检索的颜色表项的数目。

*prgbColors*<br/>
一个指针, 指向要检索其颜色表项的[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)结构的数组。

##  <a name="getdc"></a>  CImage::GetDC

检索当前具有选定图像的设备上下文。

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>返回值

设备上下文的句柄。

### <a name="remarks"></a>备注

对于每个调用`GetDC`, 必须对[ReleaseDC](#releasedc)进行后续调用。

##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString

查找可用于保存图像的图像格式。

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>参数

*strExporters*<br/>
对 `CSimpleString` 对象的引用。 有关详细信息, 请参阅 "**备注**"。

*aguidFileTypes*<br/>
Guid 的数组, 其中每个元素对应于字符串中的一种文件类型。 在下面的示例中, *aguidFileTypes*[0] 为 GUID_NULL, 其余数组值为当前操作系统支持的图像文件格式*pszAllFilesDescription* 。

> [!NOTE]
> 有关常量的完整列表, 请参阅 Windows SDK 中的**图像文件格式常数**。

*pszAllFilesDescription*<br/>
如果此参数不为 NULL, 则筛选器字符串将在列表的开头添加一个附加筛选器。 此筛选器的说明将具有*pszAllFilesDescription*的当前值, 并接受列表中任何其他导出程序支持的任何扩展的文件。

例如:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
用于指定要从列表中排除的文件类型的一组位标志。 允许的标志包括:

- `excludeGIF`= 0x01 不包括 GIF 文件。

- `excludeBMP`= 0x02 不包括 BMP (Windows 位图) 文件。

- `excludeEMF`= 0x04 不包括 EMF (增强型图元文件) 文件。

- `excludeWMF`= 0x08 排除 WMF (Windows 图元文件) 文件。

- `excludeJPEG`= 0x10 排除 JPEG 文件。

- `excludePNG`= 0x20 排除 PNG 文件。

- `excludeTIFF`= 0x40 不包括 TIFF 文件。

- `excludeIcon`= 0x80 不包括 .ICO (Windows 图标) 文件。

- `excludeOther`= 0x80000000 排除上面未列出的任何其他文件类型。

- `excludeDefaultLoad`= 0 对于负载, 默认情况下包括所有文件类型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`对于保存, 默认情况下会排除这些文件, 因为这些文件通常具有特殊要求。

*chSeparator*<br/>
图像格式之间使用的分隔符。 有关详细信息, 请参阅 "**备注**"。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

您可以将生成的格式字符串传递给 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)对象, 以便在 "文件另存为" 对话框中公开可用图像格式的文件扩展名。

参数*strExporter*的格式为:

file description0&#124;\*. ext0&#124;&#124;filedescription1\*. ext1&#124;文件说明*n.* &#124;\* *n*&#124;&#124;

其中,&#124;"" 是指定的`chSeparator`分隔符。 例如:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果将此字符串传递&#124;到 MFC `CFileDialog`对象, 则使用默认分隔符 ""。 如果将此字符串传递到公共文件保存对话框, 请使用空分隔符 "\ 0"。

##  <a name="getheight"></a>CImage:: GetHeight

检索图像的高度 (以像素为单位)。

```
int GetHeight() const throw();
```

### <a name="return-value"></a>返回值

图像的高度 (以像素为单位)。

##  <a name="getimporterfilterstring"></a>CImage:: GetImporterFilterString

查找可用于加载图像的图像格式。

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>参数

*strImporters*<br/>
对 `CSimpleString` 对象的引用。 有关详细信息, 请参阅 "**备注**"。

*aguidFileTypes*<br/>
Guid 的数组, 其中每个元素对应于字符串中的一种文件类型。 在下面的示例中, *aguidFileTypes*[0] 为 GUID_NULL, 其余数组值为当前操作系统支持的图像文件格式*pszAllFilesDescription* 。

> [!NOTE]
> 有关常量的完整列表, 请参阅 Windows SDK 中的**图像文件格式常数**。

*pszAllFilesDescription*<br/>
如果此参数不为 NULL, 则筛选器字符串将在列表的开头添加一个附加筛选器。 此筛选器的说明将具有*pszAllFilesDescription*的当前值, 并接受列表中任何其他导出程序支持的任何扩展的文件。

例如:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
用于指定要从列表中排除的文件类型的一组位标志。 允许的标志包括:

- `excludeGIF`= 0x01 不包括 GIF 文件。

- `excludeBMP`= 0x02 不包括 BMP (Windows 位图) 文件。

- `excludeEMF`= 0x04 不包括 EMF (增强型图元文件) 文件。

- `excludeWMF`= 0x08 排除 WMF (Windows 图元文件) 文件。

- `excludeJPEG`= 0x10 排除 JPEG 文件。

- `excludePNG`= 0x20 排除 PNG 文件。

- `excludeTIFF`= 0x40 不包括 TIFF 文件。

- `excludeIcon`= 0x80 不包括 .ICO (Windows 图标) 文件。

- `excludeOther`= 0x80000000 排除上面未列出的任何其他文件类型。

- `excludeDefaultLoad`= 0 对于负载, 默认情况下包括所有文件类型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`对于保存, 默认情况下会排除这些文件, 因为这些文件通常具有特殊要求。

*chSeparator*<br/>
图像格式之间使用的分隔符。 有关详细信息, 请参阅 "**备注**"。

### <a name="remarks"></a>备注

您可以将生成的格式字符串传递给 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)对象, 以在 "**文件打开**" 对话框中公开可用图像格式的文件扩展名。

参数*strImporter*的格式为:

file description0&#124;\*. ext0&#124;&#124;filedescription1\*. ext1&#124;文件说明*n.* &#124;\* *n*&#124;&#124;

其中,&#124;"" 是*chSeparator*指定的分隔符。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果将此字符串传递&#124;到 MFC `CFileDialog`对象, 则使用默认分隔符 ""。 如果将此字符串传递到公共**文件打开**对话框, 请使用空分隔符 "\ 0"。

##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries

检索颜色表中的最大项数。

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>返回值

颜色表中的条目数。

### <a name="remarks"></a>备注

此方法仅支持 DIB 节位图。

##  <a name="getpitch"></a>  CImage::GetPitch

检索图像的间距。

```
int GetPitch() const throw();
```

### <a name="return-value"></a>返回值

图像的间距。 如果返回值为负, 则位图为下边距 DIB, 其原点为左下角。 如果返回值为正, 则位图为自顶向下的 DIB, 其原点为左上角。

### <a name="remarks"></a>备注

螺距是两个内存地址之间的距离 (以字节为单位), 表示一个位图行的开头和下一个位图行的开头。 由于螺距以字节为单位进行测量, 因此图像的间距有助于确定像素格式。 螺距还可以包括为位图预留的额外内存。

使用`GetPitch` with [GetBits](#getbits)查找图像的各个像素。

> [!NOTE]
> 此方法仅支持 DIB 节位图。

##  <a name="getpixel"></a>  CImage::GetPixel

检索*x*和*y*指定的位置处的像素颜色。

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>参数

*x*<br/>
像素的 x 坐标。

*y*<br/>
像素的 y 坐标。

### <a name="return-value"></a>返回值

像素的红色、绿色、蓝色 (RGB) 值。 如果像素在当前剪辑区域外, 则返回值为 CLR_INVALID。

##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress

检索像素的确切地址。

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
像素的 x 坐标。

*y*<br/>
像素的 y 坐标。

### <a name="remarks"></a>备注

根据像素的坐标、位图的间距和每个像素的位数确定地址。

对于每个像素小于8位的格式, 此方法返回包含像素的字节的地址。 例如, 如果图像格式具有每个像素4位的, `GetPixelAddress`则返回字节中第一个像素的地址, 并且必须计算每个字节2个像素。

> [!NOTE]
> 此方法仅支持 DIB 节位图。

##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor

检索调色板中透明颜色的索引位置。

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>返回值

透明颜色的索引。

##  <a name="getwidth"></a>  CImage::GetWidth

检索图像的宽度 (以像素为单位)。

```
int GetWidth() const throw();
```

### <a name="return-value"></a>返回值

位图的宽度 (以像素为单位)。

##  <a name="isdibsection"></a>  CImage::IsDIBSection

确定附加位图是否为 DIB 部分。

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>返回值

如果附加位图是 DIB 部分, 则为 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

如果位图不是 dib 部分, 则不能使用以下`CImage`仅支持 DIB 节位图的方法:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>CImage:: IsIndexed

确定位图的像素是否映射到调色板。

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>返回值

如果已编制索引, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅当位图为8位 (256 色) 或更低时, 此方法才返回 TRUE。

> [!NOTE]
> 此方法仅支持 DIB 节位图。

##  <a name="isnull"></a>  CImage::IsNull

确定当前是否已加载位图。

```
bool IsNull() const throw();
```

### <a name="remarks"></a>备注

如果当前未加载位图, 则此方法返回 TRUE;否则为 FALSE。

##  <a name="istransparencysupported"></a>CImage:: IsTransparencySupported

指示应用程序是否支持透明位图。

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>返回值

如果当前平台支持透明度, 则为非零值。 否则为0。

### <a name="remarks"></a>备注

如果返回值不为零, 并且支持透明度, 则调用[AlphaBlend](#alphablend)、 [TransparentBlt](#transparentblt)或[Draw](#draw)将处理透明颜色。

##  <a name="load"></a>CImage:: Load

加载图像。

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>参数

*pszFileName*<br/>
指向字符串的指针, 该字符串包含要加载的图像文件的名称。

*pStream*<br/>
指向流的指针, 其中包含要加载的图像文件的名称。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

加载*pszFileName*或*pStream*指定的图像。

有效的图像类型为 BMP、GIF、JPEG、PNG 和 TIFF。

##  <a name="loadfromresource"></a>CImage:: LoadFromResource

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

*hInstance*<br/>
包含要加载的图像的模块实例的句柄。

*pszResourceName*<br/>
一个指向字符串的指针, 该字符串包含包含要加载的图像的资源的名称。

*nIDResource*<br/>
要加载的资源的 ID。

### <a name="remarks"></a>备注

资源必须是位图类型。

##  <a name="maskblt"></a>CImage:: MaskBlt

使用指定的掩码和光栅操作合并源和目标位图的颜色数据。

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

*hDestDC*<br/>
可执行文件包含资源的模块的句柄。

*xDest*<br/>
目标矩形左上角的 x 坐标 (以逻辑单位表示)。

*yDest*<br/>
目标矩形左上角的 y 坐标 (以逻辑单位表示)。

*nDestWidth*<br/>
目标矩形和源位图的宽度 (以逻辑单位为单位)。

*nDestHeight*<br/>
目标矩形和源位图的高度 (以逻辑单位为单位)。

*xSrc*<br/>
源位图左上角的逻辑 x 坐标。

*ySrc*<br/>
源位图左上角的逻辑 y 坐标。

*hbmMask*<br/>
与源设备上下文中的颜色位图组合在一起的单色掩码位图的句柄。

*xMask*<br/>
由*hbmMask*参数指定的掩码位图的水平像素偏移量。

*yMask*<br/>
*HbmMask*参数指定的掩码位图的垂直像素偏移量。

*dwROP*<br/>
指定方法用来控制源数据和目标数据的组合的前台和后台三元光栅操作代码。 后台光栅操作代码存储在此值的高序位字的高序位字节内;前台光栅操作代码存储在此值的高序位字的低序位字节内;此值的低序位字将被忽略, 并且应为零。 有关此方法上下文中前景和背景的讨论, 请参阅`MaskBlt`中的 Windows SDK。 有关常见的光栅操作代码的列表, 请`BitBlt`参阅 Windows SDK 中的。

*rectDest*<br/>
对`RECT`结构的引用, 该结构标识目标。

*pointSrc*<br/>
指示源矩形左上角的结构。`POINT`

*pointMask*<br/>
一个`POINT`结构, 指示掩码位图的左上角。

*pointDest*<br/>
对`POINT`结构的引用, 该结构标识目标矩形的左上角 (以逻辑单元表示)。

### <a name="return-value"></a>返回值

如果成功, 则为非零; 否则为0。

### <a name="remarks"></a>备注

此方法仅适用于 Windows NT 版本4.0 和更高版本。

##  <a name="operator_hbitmap"></a>CImage:: operator HBITMAP

使用此运算符可获取`CImage`对象的附加 Windows GDI 句柄。 此运算符是支持直接使用 HBITMAP 对象的强制转换运算符。

##  <a name="plgblt"></a>  CImage::PlgBlt

执行从源设备上下文中的矩形到目标设备上下文中的平行四边形的位块传输。

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

*hDestDC*<br/>
目标设备上下文的句柄。

*pPoints*<br/>
指向逻辑空间中三个点的数组的指针, 该数组标识目标平行四边形的三个角。 源矩形的左上角映射到此数组中的第一个点、此数组中的第二个点的右上角和第三个点的左下角。 源矩形的右下角映射到平行四边形中的隐式第四个点。

*hbmMask*<br/>
用于遮蔽源矩形颜色的可选单色位图的句柄。

*xSrc*<br/>
源矩形左上角的 x 坐标 (以逻辑单位表示)。

*ySrc*<br/>
源矩形左上角的 y 坐标 (以逻辑单位表示)。

*nSrcWidth*<br/>
源矩形的宽度 (以逻辑单位为单位)。

*nSrcHeight*<br/>
源矩形的高度 (以逻辑单位为单位)。

*xMask*<br/>
单色位图左上角的 x 坐标。

*yMask*<br/>
单色位图的左上角的 y 坐标。

*rectSrc*<br/>
对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用, 该结构指定源矩形的坐标。

*pointMask*<br/>
指示掩码位图左上角的[点](/previous-versions/dd162805\(v=vs.85\))结构。

### <a name="return-value"></a>返回值

如果成功, 则为非零; 否则为0。

### <a name="remarks"></a>备注

如果*hbmMask*标识有效的单色位图, `PlgBit`则使用此位图屏蔽源矩形中颜色数据的位数。

此方法仅适用于 Windows NT 版本4.0 和更高版本。 有关更多详细信息, 请参阅 Windows SDK 中的[PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) 。

##  <a name="releasedc"></a>CImage:: ReleaseDC

释放设备上下文。

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>备注

由于一次只能将一个位图选入设备上下文, 因此必须调用`ReleaseDC` [GetDC](#getdc)的每个调用。

##  <a name="releasegdiplus"></a>CImage:: ReleaseGDIPlus

释放 GDI + 使用的资源。

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>备注

必须调用此方法来释放全局`CImage`对象分配的资源。 请参阅[CImage:: CImage](#cimage)。

##  <a name="save"></a>CImage:: Save

将映像保存到指定的流或磁盘上的文件。

```
HRESULT Save(
    IStream* pStream,
    REFGUID guidFileType) const throw();

HRESULT Save(
    LPCTSTR pszFileName,
    REFGUID guidFileType = GUID_NULL) const throw();
```

### <a name="parameters"></a>参数

*pStream*<br/>
指向包含文件图像数据的 COM IStream 对象的指针。

*pszFileName*<br/>
指向图像的文件名的指针。

*guidFileType*<br/>
要将图像保存为的文件类型。 可以是以下各项之一：

- `ImageFormatBMP`未压缩的位图图像。

- `ImageFormatPNG`可移植网络图形 (PNG) 压缩映像。

- `ImageFormatJPEG`JPEG 压缩映像。

- `ImageFormatGIF`GIF 压缩映像。

> [!NOTE]
> 有关常量的完整列表, 请参阅 Windows SDK 中的**图像文件格式常数**。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

调用此函数可使用指定的名称和类型保存图像。 如果未包括*guidFileType*参数, 则将使用文件名的文件扩展名来确定映像格式。 如果未提供扩展, 则将以 BMP 格式保存图像。

##  <a name="setcolortable"></a>  CImage::SetColorTable

设置 DIB 部分调色板中某个条目范围的红色、绿色、蓝色 (RGB) 颜色值。

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>参数

*iFirstColor*<br/>
要设置的第一个项的颜色表索引。

*nColors*<br/>
要设置的颜色表项的数目。

*prgbColors*<br/>
一个指针, 指向用于设置颜色表项的[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)结构的数组。

### <a name="remarks"></a>备注

此方法仅支持 DIB 节位图。

##  <a name="setpixel"></a>  CImage::SetPixel

设置位图中给定位置的像素颜色。

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
要设置的像素的水平位置。

*y*<br/>
要设置的像素的垂直位置。

*color*<br/>
要为其设置像素的颜色。

### <a name="remarks"></a>备注

如果像素坐标位于所选剪辑区域外, 则此方法将失败。

##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed

将像素颜色设置为调色板中*iIndex*处的颜色。

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
要设置的像素的水平位置。

*y*<br/>
要设置的像素的垂直位置。

*iIndex*<br/>
调色板中颜色的索引。

##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB

将*x*和*y*指定的位置处的像素设置为由*r*、 *g*和*b*(红色、绿色、蓝色 (RGB) 图像) 指示的颜色。

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
要设置的像素的水平位置。

*y*<br/>
要设置的像素的垂直位置。

*r*<br/>
红色的强度。

*g*<br/>
绿色颜色的强度。

*b*<br/>
蓝色的强度。

### <a name="remarks"></a>备注

红色、绿色和蓝色参数分别用0到255之间的一个数字表示。 如果将所有三个参数均设置为零, 则合并的结果颜色为黑色。 如果将所有三个参数设置为 255, 则合并后的结果颜色为白色。

##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor

将给定索引位置处的颜色设置为透明。

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>参数

*iTransparentColor*<br/>
要设置为透明的颜色在调色板中的索引。 如果为-1, 则不将颜色设置为透明。

### <a name="return-value"></a>返回值

之前设置为透明的颜色的索引。

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

*hDestDC*<br/>
目标设备上下文的句柄。

*xDest*<br/>
目标矩形左上角的 x 坐标 (以逻辑单位表示)。

*yDest*<br/>
目标矩形左上角的 y 坐标 (以逻辑单位表示)。

*nDestWidth*<br/>
目标矩形的宽度 (以逻辑单位为单位)。

*nDestHeight*<br/>
目标矩形的高度 (以逻辑单位为单位)。

*dwROP*<br/>
要执行的光栅运算。 光栅操作代码定义了如何将源、目标和模式的位 (由当前选定的画笔定义) 组合在一起以形成目标。 请参阅 Windows SDK 中的[BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt)以获取其他光栅操作代码及其说明的列表。

*rectDest*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用, 该结构标识目标。

*xSrc*<br/>
源矩形左上角的 x 坐标 (以逻辑单位表示)。

*ySrc*<br/>
源矩形左上角的 y 坐标 (以逻辑单位表示)。

*nSrcWidth*<br/>
源矩形的宽度 (以逻辑单位为单位)。

*nSrcHeight*<br/>
源矩形的高度 (以逻辑单位为单位)。

*rectSrc*<br/>
对`RECT`结构的引用, 标识源。

### <a name="return-value"></a>返回值

如果成功, 则为非零; 否则为0。

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) 。

##  <a name="transparentblt"></a>CImage:: TransparentBlt

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

*hDestDC*<br/>
目标设备上下文的句柄。

*xDest*<br/>
目标矩形左上角的 x 坐标 (以逻辑单位表示)。

*yDest*<br/>
目标矩形左上角的 y 坐标 (以逻辑单位表示)。

*nDestWidth*<br/>
目标矩形的宽度 (以逻辑单位为单位)。

*nDestHeight*<br/>
目标矩形的高度 (以逻辑单位为单位)。

*crTransparent*<br/>
源位图中要视为透明的颜色。 默认情况下, CLR_INVALID, 表示应使用当前设置为图像透明色的颜色。

*rectDest*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用, 该结构标识目标。

*xSrc*<br/>
源矩形左上角的 x 坐标 (以逻辑单位表示)。

*ySrc*<br/>
源矩形左上角的 y 坐标 (以逻辑单位表示)。

*nSrcWidth*<br/>
源矩形的宽度 (以逻辑单位为单位)。

*nSrcHeight*<br/>
源矩形的高度 (以逻辑单位为单位)。

*rectSrc*<br/>
对`RECT`结构的引用, 标识源。

### <a name="return-value"></a>返回值

如果成功, 则为 TRUE; 否则为 FALSE。

### <a name="remarks"></a>备注

`TransparentBlt`对于每像素4位和每像素8位的源位图支持。 使用[CImage:: AlphaBlend](#alphablend)指定具有透明度的32位每像素位图。

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

[MMXSwarm 示例](../../overview/visual-cpp-samples.md)<br/>
[SimpleImage 示例](../../overview/visual-cpp-samples.md)<br/>
[与设备无关的位图](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)<br/>
[与设备无关的位图](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
