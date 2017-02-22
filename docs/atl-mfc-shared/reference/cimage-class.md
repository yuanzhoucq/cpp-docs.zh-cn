---
title: "CImage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CImage"
  - "ATL.CImage"
  - "ATL::CImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".gif 文件, ATL and MFC support"
  - " [C++], ATL and MFC support for"
  - "CImage class"
  - "gif 文件, ATL and MFC support"
  - "图像 [C++], ATL and MFC support for"
  - "jpeg 文件"
  - "PNG 文件, ATL and MFC support"
  - "transparent color"
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CImage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CImage` 在JPEG、GIF、BMP和可移植网络映像\(PNG\)格式提供增强的位图支持，包括能够加载和保存图像。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CImage  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CImage::CImage](../Topic/CImage::CImage.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CImage::AlphaBlend](../Topic/CImage::AlphaBlend.md)|显示具有透明或半透明的像素的位图。|  
|[CImage::Attach](../Topic/CImage::Attach.md)|附加 `HBITMAP` 到 `CImage` 对象。  可以使用与非DIB部分位图或DIB部分位图。|  
|[CImage::BitBlt](../Topic/CImage::BitBlt.md)|将源设备上下文的位图到此当前设备上下文。|  
|[CImage::Create](../Topic/CImage::Create.md)|创建DIB部分位图并将它附加到以前构造的 `CImage` 对象。|  
|[CImage::CreateEx](../Topic/CImage::CreateEx.md)|创建DIB部分位图\(带有参数\)并将它附加到以前构造的 `CImage` 对象。|  
|[CImage::Destroy](../Topic/CImage::Destroy.md)|分离 `CImage` 对象的位图和销毁位图。|  
|[CImage::Detach](../Topic/CImage::Detach.md)|分离 `CImage` 对象的位图。|  
|[CImage::Draw](../Topic/CImage::Draw.md)|将源矩形的位图到目标矩形。  **Draw** 拉伸或压缩位图如果需要，以适应目标矩形的尺寸和处理alpha混合和透明的颜色。|  
|[CImage::GetBits](../Topic/CImage::GetBits.md)|检索指向位图的实际像素值。|  
|[CImage::GetBPP](../Topic/CImage::GetBPP.md)|检索每像素的位数。|  
|[CImage::GetColorTable](../Topic/CImage::GetColorTable.md)|从项的大小颜色表中检索红色，绿色，蓝色\(RGB\)颜色值。|  
|[CImage::GetDC](../Topic/CImage::GetDC.md)|检索当前位图中选择的设备上下文。|  
|[CImage::GetExporterFilterString](../Topic/CImage::GetExporterFilterString.md)|查找可用的图像格式及其说明。|  
|[CImage::GetHeight](../Topic/CImage::GetHeight.md)|检索当前图像的高度\(以像素为单位）。|  
|[CImage::GetImporterFilterString](../Topic/CImage::GetImporterFilterString.md)|查找可用的图像格式及其说明。|  
|[CImage::GetMaxColorTableEntries](../Topic/CImage::GetMaxColorTableEntries.md)|在颜色表中检索项的最大数目。|  
|[CImage::GetPitch](../Topic/CImage::GetPitch.md)|检索当前图像的间距，以字节为单位）。|  
|[CImage::GetPixel](../Topic/CImage::GetPixel.md)|检索 *x* 和 *y*指定的像素的颜色。|  
|[CImage::GetPixelAddress](../Topic/CImage::GetPixelAddress.md)|检索给定像素的地址。|  
|[CImage::GetTransparentColor](../Topic/CImage::GetTransparentColor.md)|检索该透明颜色的位置在颜色表中。|  
|[CImage::GetWidth](../Topic/CImage::GetWidth.md)|检索当前图像的宽度\(以像素为单位）。|  
|[CImage::IsDIBSection](../Topic/CImage::IsDIBSection.md)|确定附加的位图是否为DIB部分。|  
|[CImage::IsIndexed](../Topic/CImage::IsIndexed.md)|指示位图的颜色映射到标记的调色板。|  
|[CImage::IsNull](../Topic/CImage::IsNull.md)|指示源位图当前是否正在加载。|  
|[CImage::IsTransparencySupported](../Topic/CImage::IsTransparencySupported.md)|指示应用程序是否支持透明位图和对于Windows 2000或更高版本编译的。|  
|[CImage::Load](../Topic/CImage::Load.md)|从指定的文件加载图像。|  
|[CImage::LoadFromResource](../Topic/CImage::LoadFromResource.md)|从指定的资源加载图像。|  
|[CImage::MaskBlt](../Topic/CImage::MaskBlt.md)|使用指定的掩码和光栅操作，将颜色数据进行源和目标位图。|  
|[CImage::PlgBlt](../Topic/CImage::PlgBlt.md)|在源设备上下文执行从矩形的位块传输到一个平行四边形在目标设备上下文。|  
|[CImage::ReleaseDC](../Topic/CImage::ReleaseDC.md)|释放检索与 [CImage::GetDC](../Topic/CImage::GetDC.md)的设备上下文。|  
|[CImage::ReleaseGDIPlus](../Topic/CImage::ReleaseGDIPlus.md)|释放GDI\+使用的资源。  必须调用释放全局 `CImage` 对象创建的资源。|  
|[CImage::Save](../Topic/CImage::Save.md)|保存图像，指定类型。  **保存** 不能指定图像选项。|  
|[CImage::SetColorTable](../Topic/CImage::SetColorTable.md)|在部分DIB的颜色表中将项范围的红色，绿色，蓝色RGB\)颜色值。|  
|[CImage::SetPixel](../Topic/CImage::SetPixel.md)|设置像素在指定坐标到指定的颜色。|  
|[CImage::SetPixelIndexed](../Topic/CImage::SetPixelIndexed.md)|设置像素在指定坐标为颜色在调色板的指定索引。|  
|[CImage::SetPixelRGB](../Topic/CImage::SetPixelRGB.md)|设置像素在指定坐标到指定的红色，绿色，蓝色\(RGB\)值。|  
|[CImage::SetTransparentColor](../Topic/CImage::SetTransparentColor.md)|设置被视为透明的颜色的索引。  仅在调色板的一种颜色可以透明。|  
|[CImage::StretchBlt](../Topic/CImage::StretchBlt.md)|将源矩形的位图到目标矩形，拉伸或压缩位图以适应目标矩形的尺寸，如果需要。|  
|[CImage::TransparentBlt](../Topic/CImage::TransparentBlt.md)|复制具有透明的颜色的位图从源设备上下文到此当前设备上下文。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CImage::operator HBITMAP](../Topic/CImage::operator%20HBITMAP.md)|返回Windows处理附加到 `CImage` 对象。|  
  
## 备注  
 `CImage` 采用设备无关位图\(DIB\)部分的位图;但是，您可以使用 [创建](../Topic/CImage::Create.md) 或 [CImage::Load](../Topic/CImage::Load.md) 仅使用DIB部分。  使用 [附加](../Topic/CImage::Attach.md)，可以将非DIB部分位图到 `CImage` 对象，另一方面，但不能使用以下 `CImage` 方法，支持DIB只有部分位图:  
  
-   [GetBits](../Topic/CImage::GetBits.md)  
  
-   [GetColorTable](../Topic/CImage::GetColorTable.md)  
  
-   [GetMaxColorTableEntries](../Topic/CImage::GetMaxColorTableEntries.md)  
  
-   [GetPitch](../Topic/CImage::GetPitch.md)  
  
-   [GetPixelAddress](../Topic/CImage::GetPixelAddress.md)  
  
-   [IsIndexed](../Topic/CImage::IsIndexed.md)  
  
-   [SetColorTable](../Topic/CImage::SetColorTable.md)  
  
 若要确定附加的位图是否为DIB部分，请调用 [IsDibSection](../Topic/CImage::IsDIBSection.md)**.**  
  
> [!NOTE]
>  在Visual Studio .NET中**Note** 2003中，此选件类使 `CImage` 对象的数量的计数创建。  只要计数转到0，函数 [GdiplusShutdown](_gdiplus_func_gdiplusshutdown_) 自动调用释放GDI\+使用的资源。  这样可确保始终正确地直接或间接地销毁DLL创建的所有 `CImage` 对象，并 **GdiplusShutdown** 不会从 `DllMain`调用。  
  
> [!NOTE]
>  使用在DLL的全局 `CImage` 对象不建议使用。  如果在DLL需要使用全局 `CImage` 对象，请调用 [CImage::ReleaseGDIPlus](../Topic/CImage::ReleaseGDIPlus.md) 显式释放GDI\+使用的资源。  
  
 `CImage` 不能选择到新 [CDC](../../mfc/reference/cdc-class.md)。  `CImage` 创建其图像自己的 **HDC**。  由于 `HBITMAP` 可以一次只能选择到一 **HDC**，`HBITMAP` 与 `CImage` 不能选择到另一 **HDC**。  如果需要 `CDC`，从 `CImage` 中检索 **HDC** 并为其 [CDC::FromHandle](../Topic/CDC::FromHandle.md)。  
  
## 示例  
 [!code-cpp[NVC_ATLMFC_Utilities#70](../../atl-mfc-shared/codesnippet/CPP/cimage-class_1.cpp)]  
  
 当在MFC项目时使用 `CImage`，请注意在项目中哪些成员函数需要指向 [CBitmap](../../mfc/reference/cbitmap-class.md) 对象。  如果要使用这样的功能的 `CImage`，如 [CMenu::AppendMenu](../Topic/CMenu::AppendMenu.md)，使用 [CBitmap::FromHandle](../Topic/CBitmap::FromHandle.md)，将您的 `CImage``HBITMAP`和使用返回的 `CBitmap*`。  
  
## 示例  
 [!code-cpp[NVC_ATLMFC_Utilities#71](../../atl-mfc-shared/codesnippet/CPP/cimage-class_2.cpp)]  
  
 通过 `CImage`，您可以访问DIB部分的实际位的。  可以使用 `CImage` 对象的任何位置前面使用Win32 HBITMAP或DIB部分。  
  
> [!NOTE]
>  下面 `CImage` 方法在其用法的限制:  
  
|方法|限制|  
|--------|--------|  
|[PlgBlt](../Topic/CImage::PlgBlt.md)|仅使用Windows NT 4.0或更高版本一起使用。  在运行于Windows 95 \/98或更高版本的应用程序将不起作用。|  
|[MaskBlt](../Topic/CImage::MaskBlt.md)|仅使用Windows NT 4.0或更高版本一起使用。  在运行于Windows 95 \/98或更高版本的应用程序将不起作用。|  
|[AlphaBlend](../Topic/CImage::AlphaBlend.md)|仅使用Windows 2000、Windows 98和更高版本的系统一起使用。|  
|[TransparentBlt](../Topic/CImage::TransparentBlt.md)|仅使用Windows 2000、Windows 98和更高版本的系统一起使用。|  
|[绘制](../Topic/CImage::Draw.md)|支持与Windows 2000、Windows 98和新版本的系统的透明度。|  
  
 请参见 [与以前的操作系统的CImage限制](../../mfc/cimage-limitations-with-earlier-operating-systems.md) 有关这些方法的限制的更多详细信息。  
  
 可以使用从MFC或ATL的 `CImage`。  
  
> [!NOTE]
>  使用 `CImage`时，将创建一个项目，必须定义 `CString`，在包括 `atlimage.h`之前。  如果您的项目使用ATL，不使用MFC，请包括 `atlstr.h`，在包括 `atlimage.h`之前。  如果您的项目使用MFC \(或者，如果它是使用MFC的一个ATL项目支持\)，请包括 `afxstr.h`，在包括 `atlimage.h`之前。  
>   
>  同样，在包括 `atlimpl.cpp`之前，必须包括 `atlimage.h`。  若要轻松地完成此操作，请包括 `atlimage.h` 在您的 `stdafx.h`。  
  
## 要求  
 **Header:** atlimage.h  
  
## 请参阅  
 [MMXSwarm示例](../../top/visual-cpp-samples.md)   
 [SimpleImage示例](../../top/visual-cpp-samples.md)   
 [Device\-Independent Bitmaps](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)