---
title: CImage 类
ms.date: 08/19/2019
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
ms.openlocfilehash: a6d20e1bf12f5fe7d1e9b41d88b088ca9fad35ed
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747176"
---
# <a name="cimage-class"></a>CImage 类

`CImage`提供增强的位图支持，包括以 JPEG、GIF、BMP 和便携式网络图形 （PNG） 格式加载和保存图像的能力。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CImage
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CImage：CImage](#cimage)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[图片：：阿尔法布林](#alphablend)|显示具有透明或半透明像素的位图。|
|[CImage：：附加](#attach)|将 HBITMAP 附加到`CImage`对象。 可用于非 DIB 截面位图或 DIB 部分位图。|
|[图片：：比特布拉特](#bitblt)|将位图从源设备上下文复制到此当前设备上下文。|
|[CImage：创建](#create)|创建 DIB 剖面位图并将其附加到以前构造`CImage`的对象。|
|[图片：：创建Ex](#createex)|创建 DIB 截面位图（包含其他参数），并将其附加到以前构造`CImage`的对象。|
|[图片：:D](#destroy)|从`CImage`对象分离位图并销毁位图。|
|[图片：:D](#detach)|从`CImage`对象分离位图。|
|[C图像：:D原](#draw)|将位图从源矩形复制到目标矩形中。 `Draw`如有必要，拉伸或压缩位图以适合目标矩形的尺寸，并处理 Alpha 混合和透明颜色。|
|[CImage：获取位](#getbits)|检索指向位图的实际像素值的指针。|
|[图片：：GetBPP](#getbpp)|检索每像素的位。|
|[CImage：获取颜色表](#getcolortable)|从颜色表中的一系列条目中检索红色、绿色、蓝色 （RGB） 颜色值。|
|[CImage：GetDC](#getdc)|检索选择当前位图的设备上下文。|
|[CImage：：获取导出器筛选器字符串](#getexporterfilterstring)|查找可用的图像格式及其说明。|
|[CImage：获取高度](#getheight)|检索当前图像的高度（以像素为单位）。|
|[CImage：获取导入筛选器字符串](#getimporterfilterstring)|查找可用的图像格式及其说明。|
|[CImage：获取最大颜色表条目](#getmaxcolortableentries)|检索颜色表中的最大条目数。|
|[图片：：获取投球](#getpitch)|检索当前图像的间距（以字节为单位）。|
|[CImage：获取像素](#getpixel)|检索*x*和*y*指定的像素的颜色。|
|[CImage：获取像素地址](#getpixeladdress)|检索给定像素的地址。|
|[CImage：获取透明颜色](#gettransparentcolor)|检索透明颜色在颜色表中的位置。|
|[CImage：获取宽度](#getwidth)|检索当前图像的宽度（以像素为单位）。|
|[图片：：IsDIB节](#isdibsection)|确定附加位图是否为 DIB 部分。|
|[CImage：已编制索引](#isindexed)|指示位图的颜色映射到索引调色板。|
|[C图像：：IsNull](#isnull)|指示当前是否加载源位图。|
|[CImage：是支持透明度的](#istransparencysupported)|指示应用程序是否支持透明位图。|
|[CImage：加载](#load)|从指定的文件加载图像。|
|[CImage：：从资源加载](#loadfromresource)|从指定资源加载图像。|
|[图片：：面具](#maskblt)|使用指定的蒙版和栅格操作组合源和目标位图的颜色数据。|
|[图片：:PlgBlt](#plgblt)|在目标设备上下文中执行从源设备上下文中的矩形到并行四字形的位块传输。|
|[CImage：释放DC](#releasedc)|释放使用 CImage 检索的设备上下文[：：GetDC](#getdc)。|
|[CImage：：发布GDIPlus](#releasegdiplus)|释放 GDI+ 使用的资源。 必须调用以释放由全局`CImage`对象创建的资源。|
|[CImage：：保存](#save)|将图像保存为指定类型。 `Save`无法指定图像选项。|
|[CImage：设置颜色表](#setcolortable)|在 DIB 部分的颜色表中的一系列条目中设置红色、绿色、蓝色 RGB 颜色值。|
|[CImage：设置像素](#setpixel)|将指定坐标上的像素设置为指定颜色。|
|[CImage：：设置像素索引](#setpixelindexed)|将指定坐标处的像素设置到调色板指定索引处的颜色。|
|[CImage：SetPixelRGB](#setpixelrgb)|将指定坐标处的像素设置为指定的红色、绿色、蓝色 （RGB） 值。|
|[CImage：：设置透明色](#settransparentcolor)|设置要被视为透明的颜色的索引。 调色板中只有一种颜色是透明的。|
|[C图像：拉伸Blt](#stretchblt)|将位图从源矩形复制到目标矩形中，根据需要拉伸或压缩位图以适合目标矩形的尺寸。|
|[图片：：透明布拉特](#transparentblt)|将具有透明颜色的位图从源设备上下文复制到此当前设备上下文。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CImage：：操作员 HBITMAP](#operator_hbitmap)|返回附加到`CImage`对象的 Windows 句柄。|

## <a name="remarks"></a>备注

`CImage`获取与设备无关的位图 （DIB） 部分或不采用位图;但是，您可以使用["创建](#create)"或["CImage：："](#load)仅使用 DIB 部分加载。 可以使用 Attach 将非 DIB 节位图`CImage`附加到对象[Attach](#attach)，但不能使用以下`CImage`方法，这些方法仅支持 DIB 节位图：

- [获取位](#getbits)

- [获取颜色表](#getcolortable)

- [获取最大颜色表条目](#getmaxcolortableentries)

- [获取间距](#getpitch)

- [获取像素地址](#getpixeladdress)

- [IsIndexed](#isindexed)

- [设置颜色表](#setcolortable)

要确定附加位图是否为 DIB 部分，请致电[IsDibSection](#isdibsection)。

> [!NOTE]
> 在 Visual Studio .NET 2003 中，此类保留创建`CImage`的对象数的计数。 每当计数达到 0 时，将自动`GdiplusShutdown`调用函数以释放 GDI+使用的资源。 这可确保由`CImage`DLL 直接或间接创建的任何对象始终被正确销毁，`GdiplusShutdown`并且不会从`DllMain`调用。

> [!NOTE]
> 不建议`CImage`在 DLL 中使用全局对象。 如果需要在 DLL 中使用`CImage`全局对象，请致电[CImage：：ReleaseGDIPlus](#releasegdiplus)以显式释放 GDI+使用的资源。

`CImage`无法选择到新的[CDC](../../mfc/reference/cdc-class.md)中。 `CImage`为映像创建自己的 HDC。 由于 HBITMAP 一次只能选择到一个 HDC 中，因此无法将与`CImage`HBITMAP 关联的 HBITMAP 选入另一个 HDC。 如果需要 CDC，请从 中检索 HDC`CImage`并将其交给[CDC：：fromHandle](../../mfc/reference/cdc-class.md#fromhandle)。

## <a name="example"></a>示例

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

在 MFC 项目中使用`CImage`时，请注意项目中的哪个成员函数需要指向[CBitmap](../../mfc/reference/cbitmap-class.md)对象的指针。 如果要将此类函数（`CImage`如[CMenu：：AppendMenu）](../../mfc/reference/cmenu-class.md#appendmenu)用于，请使用[CBitmap：：FromHandle，](../../mfc/reference/cbitmap-class.md#fromhandle)将其传递为`CImage`HBITMAP，并使用返回`CBitmap*`的 。

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

通过`CImage`，您可以访问 DIB 部分的实际位。 您可以在以前使用`CImage`Win32 HBITMAP 或 DIB 部分的任何位置使用对象。

您可以使用`CImage`MFC 或 ATL。

> [!NOTE]
> 使用`CImage`创建项目时，必须先在包含`CString`*atlimage.h*之前进行定义。 如果您的项目使用没有 MFC 的 ATL，请在包含*atlimage.h*之前包括*atlstr.h。* 如果您的项目使用 MFC（或者它是支持 MFC 的 ATL 项目），请在包含*atlimage.h*之前包括*afxstr.h。*<br/>
> <br/>
> 同样，在包含*atlimpl.cpp*之前，您必须包括*atlimage.h。* 要轻松完成此目的，请在*pch.h*中包括*atlimage.h（Visual* Studio 2017 及更早版本中的*stdafx.h）。*

## <a name="requirements"></a>要求

**标题：** atlimage.h

## <a name="cimagealphablend"></a><a name="alphablend"></a>图片：：阿尔法布林

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
处理目标设备上下文。

*xDest*<br/>
以逻辑单位表示目标矩形左上角的 x 坐标。

*yDest*<br/>
以逻辑单位表示目标矩形左上角的 y 坐标。

*bSrcAlpha*<br/>
要在整个源位图上使用的 alpha 透明度值。 默认 0xff （255） 假定图像不透明，并且只想使用每像素 alpha 值。

*bBlendOp*<br/>
源位图和目标位图的 alpha 混合函数、要应用于整个源位图的全局 alpha 值以及源位图的格式信息。 源和目标混合函数目前仅限于AC_SRC_OVER。

*点 Dest*<br/>
对[POINT](/windows/win32/api/windef/ns-windef-point)结构的引用，该结构以逻辑单位标识目标矩形的左上角。

*nD最大宽度*<br/>
目标矩形的宽度（以逻辑单位为单位）。

*nDestHeight*<br/>
目标矩形的高度（以逻辑单位为单位）。

*xSrc*<br/>
源矩形左上角的逻辑 x 坐标。

*伊斯尔克*<br/>
源矩形左上角的逻辑 y 坐标。

*nSrcWidth*<br/>
源矩形的宽度（以逻辑单位为单位）。

*nSrcHeight*<br/>
源矩形的高度（以逻辑单位为单位）。

*整流*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，标识目标。

*雷克斯尔*<br/>
对结构的`RECT`引用，标识源。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

Alpha 混合位图支持按像素进行颜色混合。

当*bBlendOp*设置为默认AC_SRC_OVER时，源位图将根据源像素的 alpha 值放置在目标位图上。

## <a name="cimageattach"></a><a name="attach"></a>CImage：：附加

将*hBitmap* `CImage`附加到对象。

```cpp
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
HBITMAP 的句柄。

*e方向*<br/>
指定位图的方向。 可以是以下值之一：

- DIBOR_DEFAULT位图的方向由操作系统确定。

- DIBOR_BOTTOMUP 位图的行顺序相反。 这将导致[CImage：getBits](#getbits)返回位图缓冲区末尾附近的指针[，CImage：GetPitch](#getpitch)返回负数。

- DIBOR_TOPDOWN 位图的行按从上到下的顺序排列。 这会导致[CImage：getBits](#getbits)返回指向位图缓冲区的第一个字节的指针[，CImage：getPitch](#getpitch)返回正数。

### <a name="remarks"></a>备注

位图可以是非 DIB 部分位图或 DIB 部分位图。 有关只能对 DIB 部分位图使用的方法列表，请参阅[IsDIBSection。](#isdibsection)

## <a name="cimagebitblt"></a><a name="bitblt"></a>图片：：比特布拉特

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

*德沃罗普*<br/>
要执行的栅格操作。 栅格操作代码精确定义如何组合源、目标和模式（由当前选择的画笔定义）以形成目标。 有关其他栅格操作代码及其说明的列表，请参阅 Windows SDK 中的[BitBlt。](/windows/win32/api/wingdi/nf-wingdi-bitblt)

*点 Dest*<br/>
指示目标矩形左上角的[POINT](/windows/win32/api/windef/ns-windef-point)结构。

*nD最大宽度*<br/>
目标矩形的宽度（以逻辑单位为单位）。

*nDestHeight*<br/>
目标矩形的高度（以逻辑单位为单位）。

*xSrc*<br/>
源矩形左上角的逻辑 x 坐标。

*伊斯尔克*<br/>
源矩形左上角的逻辑 y 坐标。

*整流*<br/>
指示目标矩形的[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*点Src*<br/>
指示`POINT`源矩形左上角的结构。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[BitBlt。](/windows/win32/api/wingdi/nf-wingdi-bitblt)

## <a name="cimagecimage"></a><a name="cimage"></a>CImage：CImage

构造 `CImage` 对象。

```
CImage() throw();
```

### <a name="remarks"></a>备注

构造对象后，调用["创建](#create)、[加载](#load)、[加载资源](#loadfromresource)"或["附加](#attach)"以将位图附加到对象。

**注意**在 Visual Studio 中，此类保留所创建对象`CImage`数的计数。 每当计数达到 0 时，将自动`GdiplusShutdown`调用函数以释放 GDI+使用的资源。 这可确保由`CImage`DLL 直接或间接创建的任何对象始终被正确销毁，`GdiplusShutdown`并且不会从 DllMain 调用。

不建议`CImage`在 DLL 中使用全局对象。 如果需要在 DLL 中使用`CImage`全局对象，请致电[CImage：：ReleaseGDIPlus](#releasegdiplus)以显式释放 GDI+使用的资源。

## <a name="cimagecreate"></a><a name="create"></a>CImage：创建

创建`CImage`位图并将其附加到以前构造`CImage`的对象。

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>参数

*n 宽度*<br/>
位图的`CImage`宽度（以像素为单位）。

*nHeight*<br/>
`CImage`位图的高度（以像素为单位）。 如果*nHeight*为正，则位图是自下而上的 DIB，其原点是左下角。 如果*nHeight*为负数，则位图是自上而下的 DIB，其原点是左上角。

*nBPP*<br/>
位图中每像素的位数。 通常为 4、8、16、24 或 32。 可以是 1 用于单色位图或蒙版。

dwFlags**<br/>
指定位图对象是否具有 alpha 通道。 可以是以下零个或多个值的组合：

- *创建Alpha通道*仅当*nBPP*为 32 且*e 压缩*是BI_RGB时才能使用。 如果指定，则创建的图像具有每个像素的 alpha（透明度）值，存储在每个像素的第 4 个字节中（在非 alpha 32 位图像中未使用）。 此 Alpha 通道在调用[CImage：：AlphaBlend](#alphablend)时会自动使用。

> [!NOTE]
> 在调用[CImage：:Draw](#draw)中，具有 alpha 通道的图像会自动与目标混合 alpha。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="cimagecreateex"></a><a name="createex"></a>图片：：创建Ex

创建`CImage`位图并将其附加到以前构造`CImage`的对象。

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

*n 宽度*<br/>
位图的`CImage`宽度（以像素为单位）。

*nHeight*<br/>
`CImage`位图的高度（以像素为单位）。 如果*nHeight*为正，则位图是自下而上的 DIB，其原点是左下角。 如果*nHeight*为负数，则位图是自上而下的 DIB，其原点是左上角。

*nBPP*<br/>
位图中每像素的位数。 通常为 4、8、16、24 或 32。 可以是 1 用于单色位图或蒙版。

*电子压缩*<br/>
指定压缩自下而上位图的压缩类型（无法压缩自上而下的 DIB）。 可以是以下值之一：

- BI_RGB格式未压缩。 调用`CImage::CreateEx`时指定此值等效于调用`CImage::Create`。

- BI_BITFIELDS 格式未压缩，颜色表由三个 DWORD 颜色蒙版组成，分别指定每个像素的红色、绿色和蓝色分量。 当与 16 和 32 bpp 位图一起使用时，这一点有效。

*pdwBitfields*<br/>
仅当*e 压缩*设置为BI_BITFIELDS时才使用，否则必须为 NULL。 指向三个 DWORD 位掩码数组的指针，分别指定每个像素的哪些位分别用于颜色的红色、绿色和蓝色分量。 有关位字段限制的信息，请参阅 Windows SDK 中的[BITMAPINFOHEADER。](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader)

dwFlags**<br/>
指定位图对象是否具有 alpha 通道。 可以是以下零个或多个值的组合：

- *创建Alpha通道*仅当*nBPP*为 32 且*e 压缩*是BI_RGB时才能使用。 如果指定，则创建的图像具有每个像素的 alpha（透明度）值，存储在每个像素的第 4 个字节中（在非 alpha 32 位图像中未使用）。 此 Alpha 通道在调用[CImage：：AlphaBlend](#alphablend)时会自动使用。

   > [!NOTE]
   > 在调用[CImage：:Draw](#draw)中，具有 alpha 通道的图像会自动与目标混合 alpha。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE。 否则，FALSE。

### <a name="example"></a>示例

下面的示例创建一个 100x100 像素位图，使用 16 位对每个像素进行编码。 在给定的 16 位像素中，位 0-3 对红色分量进行编码，位 4-7 编码绿色，位 8-11 编码蓝色。 其余 4 位未使用。

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a>图片：:D

从`CImage`对象分离位图并销毁位图。

```cpp
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a>图片：:D

从`CImage`对象分离位图。

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>返回值

已分离位图的句柄，如果没有附加位图，则为 NULL。

## <a name="cimagedraw"></a><a name="draw"></a>C图像：:D原

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
以逻辑单位表示目标矩形左上角的 x 坐标。

*yDest*<br/>
以逻辑单位表示目标矩形左上角的 y 坐标。

*nD最大宽度*<br/>
目标矩形的宽度（以逻辑单位为单位）。

*nDestHeight*<br/>
目标矩形的高度（以逻辑单位为单位）。

*xSrc*<br/>
源矩形左上角的 x 坐标（以逻辑单位为单位）。

*伊斯尔克*<br/>
源矩形左上角的 y 坐标（以逻辑单位为单位）。

*nSrcWidth*<br/>
源矩形的宽度（以逻辑单位为单位）。

*nSrcHeight*<br/>
源矩形的高度（以逻辑单位为单位）。

*整流*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，标识目标。

*雷克斯尔*<br/>
对结构的`RECT`引用，标识源。

*点 Dest*<br/>
对[POINT](/windows/win32/api/windef/ns-windef-point)结构的引用，该结构以逻辑单位标识目标矩形的左上角。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`Draw`执行与[拉伸 Blt](#stretchblt)相同的操作，除非图像包含透明颜色或 alpha 通道。 在这种情况下，`Draw`根据需要执行与[透明 Blt](#transparentblt)或[AlphaBlend](#alphablend)相同的操作。

对于不指定`Draw`源矩形的版本，整个源图像为默认值。 对于未指定目标`Draw`矩形大小的版本，源图像的大小为默认值，并且不会发生拉伸或收缩。

## <a name="cimagegetbits"></a><a name="getbits"></a>CImage：获取位

检索指向位图中给定像素的实际位值的指针。

```cpp
void* GetBits() throw();
```

### <a name="return-value"></a>返回值

指向位图缓冲区的指针。 如果位图是自下而上的 DIB，指针指向缓冲区末端附近。 如果位图是自上而下的 DIB，指针将指向缓冲区的第一个字节。

### <a name="remarks"></a>备注

使用此指针，以及[GetPitch](#getpitch)返回的值，可以定位和更改图像中的单个像素。

> [!NOTE]
> 此方法仅支持 DIB 部分位图;此方法仅支持 DIB 部分位图。因此，访问`CImage`对象的像素的方式与 DIB 部分的像素相同。 返回的指针指向位置 （0， 0） 处的像素。

## <a name="cimagegetbpp"></a><a name="getbpp"></a>图片：：GetBPP

检索每像素位值。

```
int GetBPP() const throw();
```

### <a name="return-value"></a>返回值

每像素的位数。

### <a name="remarks"></a>备注

此值确定定义每个像素的位数和位图中的最大颜色数。

每像素的位数通常为 1、4、8、16、24 或 32。 有关此值`biBitCount`的详细信息，请参阅 Windows SDK 中的[BITMAPINFOHEADER](/windows/win32/api/wingdi/ns-wingdi-bitmapinfoheader)成员。

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a>CImage：获取颜色表

从 DIB 部分的调色板中的一系列条目中检索红色、绿色、蓝色 （RGB） 颜色值。

```cpp
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>参数

*i第一颜色*<br/>
要检索的第一个条目的颜色表索引。

*n 颜色*<br/>
要检索的颜色表条目数。

*普尔格格颜色*<br/>
指向[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)结构数组的指针，用于检索颜色表条目。

## <a name="cimagegetdc"></a><a name="getdc"></a>CImage：GetDC

检索当前已选择图像的设备上下文。

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>返回值

设备上下文的句柄。

### <a name="remarks"></a>备注

对于 对`GetDC`的每个调用 ，您必须对[ReleaseDC](#releasedc)进行后续调用。

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage：：获取导出器筛选器字符串

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

*斯特输出*<br/>
对 `CSimpleString` 对象的引用。 有关详细信息，请参阅**备注**。

*阿吉德文件类型*<br/>
一个 GUID 数组，每个元素对应于字符串中的一个文件类型。 在下面的*pszAllFiles 描述*中的示例*中，aguidFileType*[0] GUID_NULL，其余数组值是当前操作系统支持的图像文件格式。

> [!NOTE]
> 有关常量的完整列表，请参阅 Windows SDK 中**的图像文件格式常量**。

*pszAll文件描述*<br/>
如果此参数不是 NULL，则筛选器字符串将在列表的开头有一个额外的筛选器。 此筛选器将具有*pszAllFiles 描述*的当前值，并接受列表中任何其他导出者支持的任何扩展文件。

例如：

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
指定要从列表中排除的文件类型的位标志集。 允许的标志包括：

- `excludeGIF`= 0x01 排除 GIF 文件。

- `excludeBMP`• 0x02 排除 BMP（Windows 位图）文件。

- `excludeEMF`• 0x04 排除 EMF（增强型元文件）文件。

- `excludeWMF`• 0x08 排除 WMF（Windows 元文件）文件。

- `excludeJPEG`• 0x10 排除 JPEG 文件。

- `excludePNG`= 0x20 排除 PNG 文件。

- `excludeTIFF`• 0x40 排除 TIFF 文件。

- `excludeIcon`• 0x80 排除 ICO（Windows 图标）文件。

- `excludeOther`= 0x8000000 排除上面未列出的任何其他文件类型。

- `excludeDefaultLoad`= 0 对于负载，默认情况下包括所有文件类型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`对于保存，默认情况下排除这些文件，因为它们通常具有特殊要求。

*chseparator*<br/>
在图像格式之间使用的分隔符。 有关详细信息，请参阅**备注**。

### <a name="return-value"></a>返回值

标准 HRESULT。

### <a name="remarks"></a>备注

您可以将生成的格式字符串传递给 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)对象，以在"文件保存为"对话框中公开可用图像格式的文件扩展名。

参数*str 导出*具有以下格式：

文件描述0 \*&#124;.ext0&#124;文件\*描述1&#124;.ext1&#124;...文件描述*n*n \*&#124;.ext *n*&#124;&#124;

其中"&#124;"是 指定的`chSeparator`分隔符。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果将此字符串传递给 MFC`CFileDialog`对象，请使用默认分隔符"&#124;"。 如果将此字符串传递给公共文件保存对话框，请使用空分隔符"\0"。

## <a name="cimagegetheight"></a><a name="getheight"></a>CImage：获取高度

检索图像的高度（以像素为单位）。

```
int GetHeight() const throw();
```

### <a name="return-value"></a>返回值

图像的高度（以像素为单位）。

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage：获取导入筛选器字符串

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

*串进口商*<br/>
对 `CSimpleString` 对象的引用。 有关详细信息，请参阅**备注**。

*阿吉德文件类型*<br/>
一个 GUID 数组，每个元素对应于字符串中的一个文件类型。 在下面的*pszAllFiles 描述*中的示例中 *，aguidFileType*[0] GUID_NULL，其余数组值是当前操作系统支持的图像文件格式。

> [!NOTE]
> 有关常量的完整列表，请参阅 Windows SDK 中**的图像文件格式常量**。

*pszAll文件描述*<br/>
如果此参数不是 NULL，则筛选器字符串将在列表的开头有一个额外的筛选器。 此筛选器将具有*pszAllFiles 描述*的当前值，并接受列表中任何其他导出者支持的任何扩展文件。

例如：

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
指定要从列表中排除的文件类型的位标志集。 允许的标志包括：

- `excludeGIF`= 0x01 排除 GIF 文件。

- `excludeBMP`• 0x02 排除 BMP（Windows 位图）文件。

- `excludeEMF`• 0x04 排除 EMF（增强型元文件）文件。

- `excludeWMF`• 0x08 排除 WMF（Windows 元文件）文件。

- `excludeJPEG`• 0x10 排除 JPEG 文件。

- `excludePNG`= 0x20 排除 PNG 文件。

- `excludeTIFF`• 0x40 排除 TIFF 文件。

- `excludeIcon`• 0x80 排除 ICO（Windows 图标）文件。

- `excludeOther`= 0x8000000 排除上面未列出的任何其他文件类型。

- `excludeDefaultLoad`= 0 对于负载，默认情况下包括所有文件类型

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`对于保存，默认情况下排除这些文件，因为它们通常具有特殊要求。

*chseparator*<br/>
在图像格式之间使用的分隔符。 有关详细信息，请参阅**备注**。

### <a name="remarks"></a>备注

您可以将生成的格式字符串传递给 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)对象，以在 **"文件打开"** 对话框中公开可用图像格式的文件扩展名。

参数*str导入*器的格式为：

文件描述0 \*&#124;.ext0&#124;文件\*描述1&#124;.ext1&#124;...文件描述*n*n \*&#124;.ext *n*&#124;&#124;

其中"&#124;"是*chSeparor*指定的分隔符。 例如：

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

如果将此字符串传递给 MFC`CFileDialog`对象，请使用默认分隔符"&#124;"。 如果将此字符串传递给公共**文件打开**对话框，请使用空分隔符"\0"。

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage：获取最大颜色表条目

检索颜色表中的最大条目数。

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>返回值

颜色表中的条目数。

### <a name="remarks"></a>备注

此方法仅支持 DIB 部分位图。

## <a name="cimagegetpitch"></a><a name="getpitch"></a>图片：：获取投球

检索图像的间距。

```
int GetPitch() const throw();
```

### <a name="return-value"></a>返回值

图像的间距。 如果返回值为负，则位图是自下而上的 DIB，其原点是左下角。 如果返回值为正，则位图是自上而下的 DIB，其原点是左上角。

### <a name="remarks"></a>备注

间距是两个内存地址之间的距离（以字节为单位）表示一个位图线的开头和下一位图线的开头。 由于间距以字节为单位测量，因此图像的间距可帮助您确定像素格式。 音高还可以包括额外的内存，为位图保留。

与`GetPitch` [GetBits](#getbits)一起查找图像的单个像素。

> [!NOTE]
> 此方法仅支持 DIB 部分位图。

## <a name="cimagegetpixel"></a><a name="getpixel"></a>CImage：获取像素

检索*x*和*y*指定的位置的像素颜色。

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>参数

*x*<br/>
像素的 x 坐标。

*Y*<br/>
像素的 y 坐标。

### <a name="return-value"></a>返回值

像素的红色、绿色、蓝色 （RGB） 值。 如果像素在当前剪切区域之外，则返回值CLR_INVALID。

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage：获取像素地址

检索像素的确切地址。

```cpp
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
像素的 x 坐标。

*Y*<br/>
像素的 y 坐标。

### <a name="remarks"></a>备注

地址根据像素的坐标、位图的间距和每像素的位确定。

对于每像素小于 8 位的格式，此方法返回包含像素的字节的地址。 例如，如果图像格式为每像素 4 位，请`GetPixelAddress`返回字节中第一个像素的地址，并且必须计算每个字节 2 个像素。

> [!NOTE]
> 此方法仅支持 DIB 部分位图。

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage：获取透明颜色

检索调色板中透明颜色的索引位置。

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>返回值

透明颜色的索引。

## <a name="cimagegetwidth"></a><a name="getwidth"></a>CImage：获取宽度

检索图像的宽度（以像素为单位）。

```
int GetWidth() const throw();
```

### <a name="return-value"></a>返回值

位图的宽度（以像素为单位）。

## <a name="cimageisdibsection"></a><a name="isdibsection"></a>图片：：IsDIB节

确定附加位图是否为 DIB 部分。

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>返回值

如果附加的位图是 DIB 部分，则为 TRUE。 否则，FALSE。

### <a name="remarks"></a>备注

如果位图不是 DIB 部分，则无法使用以下`CImage`仅支持 DIB 部分位图的方法：

- [获取位](#getbits)

- [获取颜色表](#getcolortable)

- [获取最大颜色表条目](#getmaxcolortableentries)

- [获取间距](#getpitch)

- [获取像素地址](#getpixeladdress)

- [IsIndexed](#isindexed)

- [设置颜色表](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a>CImage：已编制索引

确定位图的像素是否映射到调色板。

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>返回值

如果已编制索引，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

仅当位图为 8 位（256 种颜色）或更少时，此方法才返回 TRUE。

> [!NOTE]
> 此方法仅支持 DIB 部分位图。

## <a name="cimageisnull"></a><a name="isnull"></a>C图像：：IsNull

确定当前是否加载位图。

```
bool IsNull() const throw();
```

### <a name="remarks"></a>备注

如果当前未加载位图，则此方法返回 TRUE;如果当前未加载位图，则此方法将返回 TRUE。否则 FALSE。

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a>CImage：是支持透明度的

指示应用程序是否支持透明位图。

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>返回值

如果当前平台支持透明度，则非零。 否则 0。

### <a name="remarks"></a>备注

如果返回值是非零且支持透明度，则调用[AlphaBlend、](#alphablend)[透明 Blt](#transparentblt)或[Draw](#draw)将处理透明颜色。

## <a name="cimageload"></a><a name="load"></a>CImage：加载

加载图像。

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>参数

*pszFileName*<br/>
指向要加载的图像文件名称的字符串的指针。

*pStream*<br/>
指向要加载的图像文件名称的流的指针。

### <a name="return-value"></a>返回值

标准 HRESULT。

### <a name="remarks"></a>备注

加载*pszFileName*或*pStream*指定的图像。

有效图像类型为 BMP、GIF、JPEG、PNG 和 TIFF。

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a>CImage：：从资源加载

从 BITMAP 资源加载映像。

```cpp
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>参数

*hInstance*<br/>
处理包含要加载的映像的模块实例。

*psz 资源名称*<br/>
指向包含要加载的映像的资源名称的字符串的指针。

*nID资源*<br/>
要加载的资源的 ID。

### <a name="remarks"></a>备注

资源必须为 BITMAP 类型。

## <a name="cimagemaskblt"></a><a name="maskblt"></a>图片：：面具

使用指定的蒙版和栅格操作组合源和目标位图的颜色数据。

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
以逻辑单位表示目标矩形左上角的 x 坐标。

*yDest*<br/>
以逻辑单位表示目标矩形左上角的 y 坐标。

*nD最大宽度*<br/>
目标矩形和源位图的宽度（以逻辑单位为单位）。

*nDestHeight*<br/>
目标矩形和源位图的高度（以逻辑单位为单位）。

*xSrc*<br/>
源位图左上角的逻辑 x 坐标。

*伊斯尔克*<br/>
源位图左上角的逻辑 y 坐标。

*hbmMask*<br/>
处理单色蒙版位图与源设备上下文中的颜色位图结合使用。

*x蒙斯*<br/>
*hbmMask*参数指定的蒙版位图的水平像素偏移量。

*yMask*<br/>
*hbmMask*参数指定的蒙版位图的垂直像素偏移量。

*德沃罗普*<br/>
指定该方法用于控制源和目标数据组合的前景和后台三元栅格操作代码。 后台栅格操作代码存储在此值的高阶字的高阶字节中;前景栅格操作代码存储在此值的高阶字的低阶字节中;此值的低阶字将被忽略，并且应为零。 有关此方法上下文中的前景和背景的讨论，请参阅`MaskBlt`Windows SDK。 有关常见栅格操作代码的列表，请参阅`BitBlt`Windows SDK。

*整流*<br/>
对结构的`RECT`引用，标识目标。

*点Src*<br/>
指示`POINT`源矩形左上角的结构。

*点掩码*<br/>
指示`POINT`蒙版位图左上角的结构。

*点 Dest*<br/>
对以逻辑单位`POINT`标识目标矩形左上角的结构的引用。

### <a name="return-value"></a>返回值

如果成功，则非零，否则为 0。

### <a name="remarks"></a>备注

此方法仅适用于 Windows NT，版本 4.0 及更高版本。

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage：：操作员 HBITMAP

使用此运算符获取`CImage`对象的附加 Windows GDI 句柄。 此运算符是强制转换运算符，支持直接使用 HBITMAP 对象。

## <a name="cimageplgblt"></a><a name="plgblt"></a>图片：:PlgBlt

在目标设备上下文中执行从源设备上下文中的矩形到并行四字形的位块传输。

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
指向逻辑空间中三个点的数组的指针，用于标识目标平行四边形的三个角。 源矩形的左上角映射到此数组中的第一个点，右上角映射到此数组中的第二个点，左下角映射到第三个点。 源矩形的右下角映射到平行四边形中的隐式第四点。

*hbmMask*<br/>
用于遮盖源矩形颜色的可选单色位图的句柄。

*xSrc*<br/>
源矩形左上角的 x 坐标（以逻辑单位为单位）。

*伊斯尔克*<br/>
源矩形左上角的 y 坐标（以逻辑单位为单位）。

*nSrcWidth*<br/>
源矩形的宽度（以逻辑单位为单位）。

*nSrcHeight*<br/>
源矩形的高度（以逻辑单位为单位）。

*x蒙斯*<br/>
单色位图左上角的 x 坐标。

*yMask*<br/>
单色位图左上角的 y 坐标。

*雷克斯尔*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，指定源矩形的坐标。

*点掩码*<br/>
指示蒙版位图左上角的[POINT](/windows/win32/api/windef/ns-windef-point)结构。

### <a name="return-value"></a>返回值

如果成功，则非零，否则为 0。

### <a name="remarks"></a>备注

如果*hbmMask*标识了有效的单色位图，`PlgBit`则使用此位图来遮盖源矩形中的颜色数据位。

此方法仅适用于 Windows NT，版本 4.0 及更高版本。 有关详细信息，请参阅 Windows SDK 中的[PlgBlt。](/windows/win32/api/wingdi/nf-wingdi-plgblt)

## <a name="cimagereleasedc"></a><a name="releasedc"></a>CImage：释放DC

释放设备上下文。

```cpp
void ReleaseDC() const throw();
```

### <a name="remarks"></a>备注

由于一次只能选择一个位图到设备上下文中，因此必须调用`ReleaseDC` [GetDC](#getdc)的每个调用。

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a>CImage：：发布GDIPlus

释放 GDI+ 使用的资源。

```cpp
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>备注

必须调用此方法以释放由全局`CImage`对象分配的资源。 请参阅[CImage：CImage](#cimage)。

## <a name="cimagesave"></a><a name="save"></a>CImage：：保存

将映像保存到磁盘上的指定流或文件。

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

*吉德文件类型*<br/>
要将映像保存为 的文件类型。 可以是以下值之一：

- `ImageFormatBMP`未压缩位图图像。

- `ImageFormatPNG`便携式网络图形 （PNG） 压缩图像。

- `ImageFormatJPEG`JPEG 压缩图像。

- `ImageFormatGIF`GIF 压缩图像。

> [!NOTE]
> 有关常量的完整列表，请参阅 Windows SDK 中**的图像文件格式常量**。

### <a name="return-value"></a>返回值

标准 HRESULT。

### <a name="remarks"></a>备注

调用此函数以使用指定的名称和类型保存图像。 如果未包含*guidFileType*参数，则文件名的文件扩展名的文件扩展名将用于确定图像格式。 如果未提供扩展，则图像将以 BMP 格式保存。

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a>CImage：设置颜色表

为 DIB 部分的调色板中一系列条目设置红色、绿色、蓝色 （RGB） 颜色值。

```cpp
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>参数

*i第一颜色*<br/>
要设置的第一个条目的颜色表索引。

*n 颜色*<br/>
要设置的颜色表条目数。

*普尔格格颜色*<br/>
指向[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)结构数组的指针，用于设置颜色表条目。

### <a name="remarks"></a>备注

此方法仅支持 DIB 部分位图。

## <a name="cimagesetpixel"></a><a name="setpixel"></a>CImage：设置像素

在位图中给定位置设置像素的颜色。

```cpp
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
要设置的像素的水平位置。

*Y*<br/>
要设置的像素的垂直位置。

*颜色*<br/>
设置像素的颜色。

### <a name="remarks"></a>备注

如果像素坐标位于所选剪切区域之外，则此方法将失败。

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage：：设置像素索引

将像素颜色设置到调色板中*iIndex*处的颜色。

```cpp
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>参数

*x*<br/>
要设置的像素的水平位置。

*Y*<br/>
要设置的像素的垂直位置。

*iIndex*<br/>
调色板中颜色的索引。

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage：SetPixelRGB

将*x*和*y*指定位置的像素设置为红色、绿色、蓝色 （RGB） 图像中由*r、g*和*b*表示的颜色。 *g*

```cpp
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

*Y*<br/>
要设置的像素的垂直位置。

*r*<br/>
红色的强度。

*G*<br/>
绿色的强度。

*B*<br/>
蓝色的强度。

### <a name="remarks"></a>备注

红色、绿色和蓝色参数分别由介于 0 和 255 之间的数字表示。 如果将所有三个参数设置为零，则组合生成的颜色为黑色。 如果将所有三个参数设置为 255，则组合生成的颜色为白色。

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage：：设置透明色

将给定索引位置的颜色设置为透明。

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>参数

*i 透明色*<br/>
要设置为透明的颜色的索引（在调色板中）。 如果 -1，则不将任何颜色设置为透明。

### <a name="return-value"></a>返回值

以前设置为透明的颜色的索引。

## <a name="cimagestretchblt"></a><a name="stretchblt"></a>C图像：拉伸Blt

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
以逻辑单位表示目标矩形左上角的 x 坐标。

*yDest*<br/>
以逻辑单位表示目标矩形左上角的 y 坐标。

*nD最大宽度*<br/>
目标矩形的宽度（以逻辑单位为单位）。

*nDestHeight*<br/>
目标矩形的高度（以逻辑单位为单位）。

*德沃罗普*<br/>
要执行的栅格操作。 栅格操作代码精确定义如何组合源、目标和模式（由当前选择的画笔定义）以形成目标。 有关其他栅格操作代码及其说明的列表，请参阅 Windows SDK 中的[BitBlt。](/windows/win32/api/wingdi/nf-wingdi-bitblt)

*整流*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，标识目标。

*xSrc*<br/>
源矩形左上角的 x 坐标（以逻辑单位为单位）。

*伊斯尔克*<br/>
源矩形左上角的 y 坐标（以逻辑单位为单位）。

*nSrcWidth*<br/>
源矩形的宽度（以逻辑单位为单位）。

*nSrcHeight*<br/>
源矩形的高度（以逻辑单位为单位）。

*雷克斯尔*<br/>
对结构的`RECT`引用，标识源。

### <a name="return-value"></a>返回值

如果成功，则非零，否则为 0。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[拉伸 Blt。](/windows/win32/api/wingdi/nf-wingdi-stretchblt)

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a>图片：：透明布拉特

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
以逻辑单位表示目标矩形左上角的 x 坐标。

*yDest*<br/>
以逻辑单位表示目标矩形左上角的 y 坐标。

*nD最大宽度*<br/>
目标矩形的宽度（以逻辑单位为单位）。

*nDestHeight*<br/>
目标矩形的高度（以逻辑单位为单位）。

*cr透明*<br/>
要视为透明源位图中的颜色。 默认情况下，CLR_INVALID，指示应使用当前设置为图像透明颜色的颜色。

*整流*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，标识目标。

*xSrc*<br/>
源矩形左上角的 x 坐标（以逻辑单位为单位）。

*伊斯尔克*<br/>
源矩形左上角的 y 坐标（以逻辑单位为单位）。

*nSrcWidth*<br/>
源矩形的宽度（以逻辑单位为单位）。

*nSrcHeight*<br/>
源矩形的高度（以逻辑单位为单位）。

*雷克斯尔*<br/>
对结构的`RECT`引用，标识源。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE，否则为 FALSE。

### <a name="remarks"></a>备注

`TransparentBlt`支持每像素 4 位和 8 位/像素的源位图。 使用[CImage：：AlphaBlend](#alphablend)指定具有透明度的 32 位/像素位图。

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

[MMXSwarm 样品](../../overview/visual-cpp-samples.md)<br/>
[简单图像示例](../../overview/visual-cpp-samples.md)<br/>
[设备无关位图](/windows/win32/gdi/device-independent-bitmaps)<br/>
[创建DIB节](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)<br/>
[设备无关位图](/windows/win32/gdi/device-independent-bitmaps)<br/>
[创建DIB节](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
