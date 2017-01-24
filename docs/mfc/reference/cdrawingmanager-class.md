---
title: "CDrawingManager Class | Microsoft Docs"
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
  - "CDrawingManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDrawingManager class"
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
caps.latest.revision: 30
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDrawingManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDrawingManager` 选件类实现复杂绘图算法。  
  
## 语法  
  
```  
class CDrawingManager : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDrawingManager::CDrawingManager](../Topic/CDrawingManager::CDrawingManager.md)|构造 `CDrawingManager` 对象。|  
|`CDrawingManager::~CDrawingManager`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDrawingManager::CreateBitmap\_32](../Topic/CDrawingManager::CreateBitmap_32.md)|创建应用程序可以编写访问为直接的32位设备无关位图\(DIB）。|  
|[CDrawingManager::DrawAlpha](../Topic/CDrawingManager::DrawAlpha.md)|显示具有透明或半透明的像素的位图。|  
|[CDrawingManager::DrawRotated](../Topic/CDrawingManager::DrawRotated.md)|由\+\/\-旋转90度在给定矩形内的源DC内容|  
|[CDrawingManager::DrawEllipse](../Topic/CDrawingManager::DrawEllipse.md)|绘制用所提供的加载和边框颜色的一个椭圆。|  
|[CDrawingManager::DrawGradientRing](../Topic/CDrawingManager::DrawGradientRing.md)|绘制环并用颜色渐变填充它。|  
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](../Topic/CDrawingManager::DrawLine,%20CDrawingManager::DrawLineA.md)|绘制线条。|  
|[CDrawingManager::DrawRect](../Topic/CDrawingManager::DrawRect.md)|绘制用所提供的加载和边框颜色的一个矩形。|  
|[CDrawingManager::DrawShadow](../Topic/CDrawingManager::DrawShadow.md)|绘制矩形区域的阴影。|  
|[CDrawingManager::Fill4ColorsGradient](../Topic/CDrawingManager::Fill4ColorsGradient.md)|有两种颜色渐变填充矩形区域。|  
|[CDrawingManager::FillGradient](../Topic/CDrawingManager::FillGradient.md)|用指定的颜色渐变填充矩形区域。|  
|[CDrawingManager::FillGradient2](../Topic/CDrawingManager::FillGradient2.md)|用指定的颜色渐变填充矩形区域。  渐变的颜色变化的方向还指定。|  
|[CDrawingManager::GrayRect](../Topic/CDrawingManager::GrayRect.md)|用指定的灰色颜色填充矩形。|  
|[CDrawingManager::HighlightRect](../Topic/CDrawingManager::HighlightRect.md)|显示矩形区域。|  
|[CDrawingManager::HLStoRGB\_ONE](../Topic/CDrawingManager::HLStoRGB_ONE.md)|将HLS表示的颜色为RGB表示形式。|  
|[CDrawingManager::HLStoRGB\_TWO](../Topic/CDrawingManager::HLStoRGB_TWO.md)|将HLS表示的颜色为RGB表示形式。|  
|[CDrawingManager::HSVtoRGB](../Topic/CDrawingManager::HSVtoRGB.md)|将HSV表示的颜色为RGB表示形式。|  
|[CDrawingManager::HuetoRGB](../Topic/CDrawingManager::HuetoRGB.md)|转换颜色值转换为，红色、绿色还是蓝色分量的帮助器方法。|  
|[CDrawingManager::MirrorRect](../Topic/CDrawingManager::MirrorRect.md)|翻转矩形区域。|  
|[CDrawingManager::PixelAlpha](../Topic/CDrawingManager::PixelAlpha.md)|确定半透明的像素的最终颜色的帮助器方法。|  
|[CDrawingManager::PrepareShadowMask](../Topic/CDrawingManager::PrepareShadowMask.md)|创建可用作阴影的位图。|  
|[CDrawingManager::RGBtoHSL](../Topic/CDrawingManager::RGBtoHSL.md)|将RGB表示的颜色为HSL表示。|  
|[CDrawingManager::RGBtoHSV](../Topic/CDrawingManager::RGBtoHSV.md)|将RGB表示的颜色为HSV表示。|  
|[CDrawingManager::SetAlphaPixel](../Topic/CDrawingManager::SetAlphaPixel.md)|为在位图的一部分透明的像素的帮助器方法。|  
|[CDrawingManager::SetPixel](../Topic/CDrawingManager::SetPixel.md)|将位图的一个像素到指定颜色的帮助器方法。|  
|[CDrawingManager::SmartMixColors](../Topic/CDrawingManager::SmartMixColors.md)|可以基于体重比的两种颜色。|  
  
## 备注  
 `CDrawingManager` 选件类提供了绘制的阴影、颜色渐变和显示的矩形的功能。  它还执行Alpha混合。  可以使用此选件类直接更改应用程序的用户界面。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)  
  
## 要求  
 **标头:** afxdrawmanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)