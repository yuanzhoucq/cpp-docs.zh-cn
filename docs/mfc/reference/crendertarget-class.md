---
title: "CRenderTarget 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRenderTarget"
  - "afxrendertarget/CRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRenderTarget 类"
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRenderTarget 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1RenderTarget 的包装。  
  
## 语法  
  
```  
class CRenderTarget : public CObject;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRenderTarget::CRenderTarget](../Topic/CRenderTarget::CRenderTarget.md)|构造 CRenderTarget 对象。|  
|[CRenderTarget::~CRenderTarget](../Topic/CRenderTarget::~CRenderTarget.md)|该析构函数。  当呈现器目标对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRenderTarget::Attach](../Topic/CRenderTarget::Attach.md)|将现有的呈现器目标接口附加到该对象|  
|[CRenderTarget::BeginDraw](../Topic/CRenderTarget::BeginDraw.md)|启动在此呈现目标上绘图。|  
|[CRenderTarget::Clear](../Topic/CRenderTarget::Clear.md)|清除指定颜色的绘图区域。|  
|[CRenderTarget::COLORREF\_TO\_D2DCOLOR](../Topic/CRenderTarget::COLORREF_TO_D2DCOLOR.md)|将 GDI 颜色和 alpha 值转换为 D2D1\_COLOR\_F 对象。|  
|[CRenderTarget::CreateCompatibleRenderTarget](../Topic/CRenderTarget::CreateCompatibleRenderTarget.md)|在与当前呈现器目标兼容的中间屏幕外绘图期间，创建新的位图呈现器目标以供使用。|  
|[CRenderTarget::Destroy](../Topic/CRenderTarget::Destroy.md)|删除一个或多个资源|  
|[CRenderTarget::Detach](../Topic/CRenderTarget::Detach.md)|将呈现器目标接口从该对象分离|  
|[CRenderTarget::DrawBitmap](../Topic/CRenderTarget::DrawBitmap.md)|绘制由指定的 IDWriteTextLayout 对象描述的格式化文本。|  
|[CRenderTarget::DrawEllipse](../Topic/CRenderTarget::DrawEllipse.md)|使用指定的笔画样式绘制指定的椭圆边框。|  
|[CRenderTarget::DrawGeometry](../Topic/CRenderTarget::DrawGeometry.md)|使用指定的笔画样式绘制指定的几何图形边框。|  
|[CRenderTarget::DrawGlyphRun](../Topic/CRenderTarget::DrawGlyphRun.md)|绘制指定的字形。|  
|[CRenderTarget::DrawLine](../Topic/CRenderTarget::DrawLine.md)|使用指定的笔画样式在两个指定点之间绘制一条线。|  
|[CRenderTarget::DrawRectangle](../Topic/CRenderTarget::DrawRectangle.md)|绘制具有指定的尺寸和笔画样式的矩形边框。|  
|[CRenderTarget::DrawRoundedRectangle](../Topic/CRenderTarget::DrawRoundedRectangle.md)|使用指定的笔画样式绘制指定的圆角矩形边框。|  
|[CRenderTarget::DrawText](../Topic/CRenderTarget::DrawText.md)|使用由 IDWriteTextFormat 对象提供的格式信息绘制指定的文本。|  
|[CRenderTarget::DrawTextLayout](../Topic/CRenderTarget::DrawTextLayout.md)|绘制由指定的 IDWriteTextLayout 对象描述的格式化文本。|  
|[CRenderTarget::EndDraw](../Topic/CRenderTarget::EndDraw.md)|结束呈现器目标上的绘图操作，并指示当前错误状态和关联的标记。|  
|[CRenderTarget::FillEllipse](../Topic/CRenderTarget::FillEllipse.md)|绘制指定椭圆的内部。|  
|[CRenderTarget::FillGeometry](../Topic/CRenderTarget::FillGeometry.md)|绘制指定几何图形的内部。|  
|[CRenderTarget::FillMesh](../Topic/CRenderTarget::FillMesh.md)|绘制指定网格的内部。|  
|[CRenderTarget::FillOpacityMask](../Topic/CRenderTarget::FillOpacityMask.md)|将由指定的位图描述的不透明蒙板应用到画笔，然后使用该画笔绘制呈现器目标的区域。|  
|[CRenderTarget::FillRectangle](../Topic/CRenderTarget::FillRectangle.md)|绘制指定矩形的内部。|  
|[CRenderTarget::FillRoundedRectangle](../Topic/CRenderTarget::FillRoundedRectangle.md)|绘制指定圆角矩形的内部。|  
|[CRenderTarget::Flush](../Topic/CRenderTarget::Flush.md)|执行所有挂起的绘图命令。|  
|[CRenderTarget::GetAntialiasMode](../Topic/CRenderTarget::GetAntialiasMode.md)|检索非文本绘图操作的当前抗锯齿模式。|  
|[CRenderTarget::GetDpi](../Topic/CRenderTarget::GetDpi.md)|返回该呈现器目标的每英寸点数 \(DPI\)|  
|[CRenderTarget::GetMaximumBitmapSize](../Topic/CRenderTarget::GetMaximumBitmapSize.md)|获取呈现器目标支持的任意一个位图尺寸的最大大小，以依赖于设备的单位（像素）表示。|  
|[CRenderTarget::GetPixelFormat](../Topic/CRenderTarget::GetPixelFormat.md)|检索该呈现器目标的像素格式和 alpha 模式|  
|[CRenderTarget::GetPixelSize](../Topic/CRenderTarget::GetPixelSize.md)|返回该呈现器目标的大小（以设备像素为单位）|  
|[CRenderTarget::GetRenderTarget](../Topic/CRenderTarget::GetRenderTarget.md)|返回 ID2D1RenderTarget 接口|  
|[CRenderTarget::GetSize](../Topic/CRenderTarget::GetSize.md)|返回该呈现器目标的大小（以与设备无关的像素为单位）|  
|[CRenderTarget::GetTags](../Topic/CRenderTarget::GetTags.md)|获取用于后续绘图操作的标签。|  
|[CRenderTarget::GetTextAntialiasMode](../Topic/CRenderTarget::GetTextAntialiasMode.md)|获取文本和字形绘图操作的当前抗锯齿模式。|  
|[CRenderTarget::GetTextRenderingParams](../Topic/CRenderTarget::GetTextRenderingParams.md)|检索该呈现器目标的当前文本呈现选项。|  
|[CRenderTarget::GetTransform](../Topic/CRenderTarget::GetTransform.md)|将指定的转换应用到将替换现有转换的呈现器目标。  所有后续的绘图操作将在转换后的空间中进行。|  
|[CRenderTarget::IsSupported](../Topic/CRenderTarget::IsSupported.md)|指示该呈现器目标是否支持指定的属性|  
|[CRenderTarget::IsValid](../Topic/CRenderTarget::IsValid.md)|检查资源有效性|  
|[CRenderTarget::PopAxisAlignedClip](../Topic/CRenderTarget::PopAxisAlignedClip.md)|从呈现器目标中删除最后一个轴对齐的剪辑。  在调用此方法之后，该剪辑将不再应用于后续的绘图操作。|  
|[CRenderTarget::PopLayer](../Topic/CRenderTarget::PopLayer.md)|停止将绘图操作重定向到由最后一个 PushLayer 调用指定的层。|  
|[CRenderTarget::PushAxisAlignedClip](../Topic/CRenderTarget::PushAxisAlignedClip.md)|从呈现器目标中删除最后一个轴对齐的剪辑。  在调用此方法之后，该剪辑将不再应用于后续的绘图操作。|  
|[CRenderTarget::PushLayer](../Topic/CRenderTarget::PushLayer.md)|将指定的层添加到呈现器目标，以便呈现器目标接收到所有后续的绘图操作，直到调用 PopLayer。|  
|[CRenderTarget::RestoreDrawingState](../Topic/CRenderTarget::RestoreDrawingState.md)|将呈现器目标的绘图状态设置为指定的 ID2D1DrawingStateBlock 的绘图状态。|  
|[CRenderTarget::SaveDrawingState](../Topic/CRenderTarget::SaveDrawingState.md)|将当前绘图状态保存到指定的 ID2D1DrawingStateBlock。|  
|[CRenderTarget::SetAntialiasMode](../Topic/CRenderTarget::SetAntialiasMode.md)|设置该呈现器目标的抗锯齿模式。  应用于所有后续绘图操作（不包括文本和字形绘图操作）的抗锯齿模式。|  
|[CRenderTarget::SetDpi](../Topic/CRenderTarget::SetDpi.md)|设置该呈现器目标的每英寸点数 \(DPI\)|  
|[CRenderTarget::SetTags](../Topic/CRenderTarget::SetTags.md)|指定用于后续绘图操作的标签。|  
|[CRenderTarget::SetTextAntialiasMode](../Topic/CRenderTarget::SetTextAntialiasMode.md)|指定用于后续文本和字形绘图操作的抗锯齿模式。|  
|[CRenderTarget::SetTextRenderingParams](../Topic/CRenderTarget::SetTextRenderingParams.md)|指定要应用于所有后续文本和字形绘图操作的文本呈现选项。|  
|[CRenderTarget::SetTransform](../Topic/CRenderTarget::SetTransform.md)|已重载。  将指定的转换应用到将替换现有转换的呈现器目标。  所有后续的绘图操作将在转换后的空间中进行。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CRenderTarget::VerifyResource](../Topic/CRenderTarget::VerifyResource.md)|验证 CD2DResource 对象有效性；如果该对象不存在，则创建该对象。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CRenderTarget::operator ID2D1RenderTarget\*](../Topic/CRenderTarget::operator%20ID2D1RenderTarget*.md)|返回 ID2D1RenderTarget 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CRenderTarget::m\_lstResources](../Topic/CRenderTarget::m_lstResources.md)|指向 CD2DResource 对象的指针列表。|  
|[CRenderTarget::m\_pRenderTarget](../Topic/CRenderTarget::m_pRenderTarget.md)|指向 ID2D1RenderTarget 对象的指针。|  
|[CRenderTarget::m\_pTextFormatDefault](../Topic/CRenderTarget::m_pTextFormatDefault.md)|指向包含默认文本格式的 CD2DTextFormat 对象的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)