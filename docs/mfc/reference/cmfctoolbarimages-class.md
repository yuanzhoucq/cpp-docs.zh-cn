---
title: "CMFCToolBarImages Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarImages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarImages class"
ms.assetid: d4e50518-9ffc-406f-9996-f79e5cd38155
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCToolBarImages Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在工具栏的图形。  `CMFCToolBarImages` 选件类管理从文件加载的从应用程序资源或工具栏图像。  
  
## 语法  
  
```  
class CMFCToolBarImages : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarImages::CMFCToolBarImages](../Topic/CMFCToolBarImages::CMFCToolBarImages.md)|构造 `CMFCToolBarImages` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarImages::AdaptColors](../Topic/CMFCToolBarImages::AdaptColors.md)||  
|[CMFCToolBarImages::AddIcon](../Topic/CMFCToolBarImages::AddIcon.md)|将图标添加到工具栏图像。|  
|[CMFCToolBarImages::AddImage](../Topic/CMFCToolBarImages::AddImage.md)|添加一个位图到工具栏图像。|  
|[CMFCToolBarImages::CleanUp](../Topic/CMFCToolBarImages::CleanUp.md)||  
|[CMFCToolBarImages::Clear](../Topic/CMFCToolBarImages::Clear.md)|释放分配到此对象的系统资源。|  
|[CMFCToolBarImages::ConvertTo32Bits](../Topic/CMFCToolBarImages::ConvertTo32Bits.md)|将带下划线位图为32个bpp图像。|  
|[CMFCToolBarImages::CopyImageToClipboard](../Topic/CMFCToolBarImages::CopyImageToClipboard.md)||  
|[CMFCToolBarImages::CopyTo](../Topic/CMFCToolBarImages::CopyTo.md)||  
|[CMFCToolBarImages::CreateFromImageList](../Topic/CMFCToolBarImages::CreateFromImageList.md)|初始化从图像的工具栏图像列表\([CImageList Class](../../mfc/reference/cimagelist-class.md)）。|  
|[CMFCToolBarImages::CreateRegionFromImage](../Topic/CMFCToolBarImages::CreateRegionFromImage.md)||  
|[CMFCToolBarImages::DeleteImage](../Topic/CMFCToolBarImages::DeleteImage.md)|删除具有从工具栏图像的指定索引的图像，如果将工具栏图像包含用户定义的图像。|  
|[CMFCToolBarImages::Draw](../Topic/CMFCToolBarImages::Draw.md)|绘制一个工具栏图像\(按钮）。|  
|[CMFCToolBarImages::DrawEx](../Topic/CMFCToolBarImages::DrawEx.md)||  
|[CMFCToolBarImages::EnableRTL](../Topic/CMFCToolBarImages::EnableRTL.md)||  
|[CMFCToolBarImages::EndDrawImage](../Topic/CMFCToolBarImages::EndDrawImage.md)|在绘制后，释放系统资源工具栏图像。|  
|[CMFCToolBarImages::ExtractIcon](../Topic/CMFCToolBarImages::ExtractIcon.md)|返回具有从工具栏图像的指定图像索引的图标。|  
|[CMFCToolBarImages::FillDitheredRect](../Topic/CMFCToolBarImages::FillDitheredRect.md)|加载一个矩形使用具有工具栏背景色的画笔。|  
|[CMFCToolBarImages::GetAlwaysLight](../Topic/CMFCToolBarImages::GetAlwaysLight.md)||  
|[CMFCToolBarImages::GetBitsPerPixel](../Topic/CMFCToolBarImages::GetBitsPerPixel.md)|返回带下划线的图像的当前分辨率。|  
|[CMFCToolBarImages::GetCount](../Topic/CMFCToolBarImages::GetCount.md)|返回图像的数目工具栏上的。|  
|[CMFCToolBarImages::GetDisabledImageAlpha](../Topic/CMFCToolBarImages::GetDisabledImageAlpha.md)|返回为禁用图像的alpha通道值。|  
|[CMFCToolBarImages::GetFadedImageAlpha](../Topic/CMFCToolBarImages::GetFadedImageAlpha.md)||  
|[CMFCToolBarImages::GetImageSize](../Topic/CMFCToolBarImages::GetImageSize.md)|检索任何在内存工具栏图像的大小\(源范围\)存储，或者在屏幕上工具栏图像的大小\(目标范围\)绘制。|  
|[CMFCToolBarImages::GetImageWell](../Topic/CMFCToolBarImages::GetImageWell.md)|将处理返回到包含所有工具栏图像的位图。|  
|[CMFCToolBarImages::GetImageWellLight](../Topic/CMFCToolBarImages::GetImageWellLight.md)||  
|[CMFCToolBarImages::GetLastImageRect](../Topic/CMFCToolBarImages::GetLastImageRect.md)||  
|[CMFCToolBarImages::GetLightPercentage](../Topic/CMFCToolBarImages::GetLightPercentage.md)||  
|[CMFCToolBarImages::GetMapTo3DColors](../Topic/CMFCToolBarImages::GetMapTo3DColors.md)||  
|[CMFCToolBarImages::GetMask](../Topic/CMFCToolBarImages::GetMask.md)||  
|[CMFCToolBarImages::GetResourceOffset](../Topic/CMFCToolBarImages::GetResourceOffset.md)|返回指定的资源ID.的图像索引|  
|[CMFCToolBarImages::GetScale](../Topic/CMFCToolBarImages::GetScale.md)|返回带下划线的图像当前缩放比例。|  
|[CMFCToolBarImages::GetTransparentColor](../Topic/CMFCToolBarImages::GetTransparentColor.md)||  
|[CMFCToolBarImages::GrayImages](../Topic/CMFCToolBarImages::GrayImages.md)|灰色使它们的工具栏图像看上去禁用。|  
|[CMFCToolBarImages::Is32BitTransparencySupported](../Topic/CMFCToolBarImages::Is32BitTransparencySupported.md)|确定操作系统是否支持32位alpha混合。|  
|[CMFCToolBarImages::IsPreMultiplyAutoCheck](../Topic/CMFCToolBarImages::IsPreMultiplyAutoCheck.md)||  
|[CMFCToolBarImages::IsRTL](../Topic/CMFCToolBarImages::IsRTL.md)|确定从右向左的\(RTL\)是否支持启用。|  
|[CMFCToolBarImages::IsReadOnly](../Topic/CMFCToolBarImages::IsReadOnly.md)|确定工具栏图像是否为只读。|  
|[CMFCToolBarImages::IsScaled](../Topic/CMFCToolBarImages::IsScaled.md)|指示是否加下划线的图像缩放。|  
|[CMFCToolBarImages::IsUserImagesList](../Topic/CMFCToolBarImages::IsUserImagesList.md)|确定此设置工具栏图像是否包含用户定义的图像。|  
|[CMFCToolBarImages::IsValid](../Topic/CMFCToolBarImages::IsValid.md)|确定此设置工具栏图像是否包含有效的工具栏图像。|  
|[CMFCToolBarImages::Load](../Topic/CMFCToolBarImages::Load.md)|加载工具栏图像从系统资源或文件。|  
|[CMFCToolBarImages::LoadStr](../Topic/CMFCToolBarImages::LoadStr.md)||  
|[CMFCToolBarImages::MapFromSysColor](../Topic/CMFCToolBarImages::MapFromSysColor.md)||  
|[CMFCToolBarImages::MapTo3dColors](../Topic/CMFCToolBarImages::MapTo3dColors.md)||  
|[CMFCToolBarImages::MapToSysColor](../Topic/CMFCToolBarImages::MapToSysColor.md)||  
|[CMFCToolBarImages::MapToSysColorAlpha](../Topic/CMFCToolBarImages::MapToSysColorAlpha.md)||  
|[CMFCToolBarImages::Mirror](../Topic/CMFCToolBarImages::Mirror.md)|水平镜像所有工具栏图像。|  
|[CMFCToolBarImages::MirrorBitmap](../Topic/CMFCToolBarImages::MirrorBitmap.md)|水平镜像位图。|  
|[CMFCToolBarImages::MirrorBitmapVert](../Topic/CMFCToolBarImages::MirrorBitmapVert.md)||  
|[CMFCToolBarImages::MirrorVert](../Topic/CMFCToolBarImages::MirrorVert.md)||  
|[CMFCToolBarImages::OnSysColorChange](../Topic/CMFCToolBarImages::OnSysColorChange.md)||  
|[CMFCToolBarImages::PrepareDrawImage](../Topic/CMFCToolBarImages::PrepareDrawImage.md)|分配需要绘制工具栏图像在指定范围的资源。|  
|[CMFCToolBarImages::Save](../Topic/CMFCToolBarImages::Save.md)|;如果属性设置工具栏图像包含用户定义的图像，在文件存储工具栏图像。|  
|[CMFCToolBarImages::SetAlwaysLight](../Topic/CMFCToolBarImages::SetAlwaysLight.md)||  
|[CMFCToolBarImages::SetDisabledImageAlpha](../Topic/CMFCToolBarImages::SetDisabledImageAlpha.md)|设置为禁用图像的alpha通道值。|  
|[CMFCToolBarImages::SetFadedImageAlpha](../Topic/CMFCToolBarImages::SetFadedImageAlpha.md)||  
|[CMFCToolBarImages::SetImageSize](../Topic/CMFCToolBarImages::SetImageSize.md)|设置工具栏图像\(源范围\)的大小。|  
|[CMFCToolBarImages::SetLightPercentage](../Topic/CMFCToolBarImages::SetLightPercentage.md)||  
|[CMFCToolBarImages::SetMapTo3DColors](../Topic/CMFCToolBarImages::SetMapTo3DColors.md)||  
|[CMFCToolBarImages::SetPreMultiplyAutoCheck](../Topic/CMFCToolBarImages::SetPreMultiplyAutoCheck.md)||  
|[CMFCToolBarImages::SetSingleImage](../Topic/CMFCToolBarImages::SetSingleImage.md)||  
|[CMFCToolBarImages::SetTransparentColor](../Topic/CMFCToolBarImages::SetTransparentColor.md)|设置工具栏图像的透明的颜色。|  
|[CMFCToolBarImages::SmoothResize](../Topic/CMFCToolBarImages::SmoothResize.md)|成功调整带下划线的图像。|  
|[CMFCToolBarImages::UpdateImage](../Topic/CMFCToolBarImages::UpdateImage.md)|更新位图的用户定义的工具栏图像。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarImages::PreMultiplyAlpha](../Topic/CMFCToolBarImages::PreMultiplyAlpha.md)||  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarImages::m\_bDisableTrueColorAlpha](../Topic/CMFCToolBarImages::m_bDisableTrueColorAlpha.md)|`TRUE`，如果truecolor alpha混合\(32位颜色\)被禁用。|  
  
## 备注  
 工具栏图像完整的位图 `CMFCToolbarImages` 托管包含一个或多个小的工具栏图像\(按钮\)的固定大小。  
  
## 示例  
 通过在 `CMFCToolBarImages` 选件类，中的各种方法下面的示例演示如何配置 `CMFCToolBarImages` 对象。  此示例演示如何设置工具栏图像的大小，加载图像，并设置图像的透明的颜色。  此代码段是 [Visual Studio演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#32](../../mfc/codesnippet/CPP/cmfctoolbarimages-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#33](../../mfc/codesnippet/CPP/cmfctoolbarimages-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md)  
  
## 要求  
 **标头:** afxtoolbarimages.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)