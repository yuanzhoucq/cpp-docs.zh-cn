---
title: "CD2DRadialGradientBrush 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DRadialGradientBrush"
  - "afxrendertarget/CD2DRadialGradientBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DRadialGradientBrush 类"
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CD2DRadialGradientBrush 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1RadialGradientBrush 的包装。  
  
## 语法  
  
```  
class CD2DRadialGradientBrush : public CD2DGradientBrush;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](../Topic/CD2DRadialGradientBrush::CD2DRadialGradientBrush.md)|构造 CD2DLinearGradientBrush 对象。|  
|[CD2DRadialGradientBrush::~CD2DRadialGradientBrush](../Topic/CD2DRadialGradientBrush::~CD2DRadialGradientBrush.md)|该析构函数。  当 D2D 径向渐变画笔对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DRadialGradientBrush::Attach](../Topic/CD2DRadialGradientBrush::Attach.md)|将现有的资源接口附加到该对象|  
|[CD2DRadialGradientBrush::Create](../Topic/CD2DRadialGradientBrush::Create.md)|创建 CD2DRadialGradientBrush。  （重写 [CD2DResource::Create](../Topic/CD2DResource::Create.md)。）|  
|[CD2DRadialGradientBrush::Destroy](../Topic/CD2DRadialGradientBrush::Destroy.md)|销毁 CD2DRadialGradientBrush 对象。  （重写 [CD2DGradientBrush::Destroy](../Topic/CD2DGradientBrush::Destroy.md)。）|  
|[CD2DRadialGradientBrush::Detach](../Topic/CD2DRadialGradientBrush::Detach.md)|将资源接口从该对象分离|  
|[CD2DRadialGradientBrush::Get](../Topic/CD2DRadialGradientBrush::Get.md)|返回 ID2D1RadialGradientBrush 接口|  
|[CD2DRadialGradientBrush::GetCenter](../Topic/CD2DRadialGradientBrush::GetCenter.md)|检索该渐变椭圆的中心|  
|[CD2DRadialGradientBrush::GetGradientOriginOffset](../Topic/CD2DRadialGradientBrush::GetGradientOriginOffset.md)|检索该渐变原点相对于此渐变椭圆中心的偏移|  
|[CD2DRadialGradientBrush::GetRadiusX](../Topic/CD2DRadialGradientBrush::GetRadiusX.md)|检索该渐变椭圆的 x 半径|  
|[CD2DRadialGradientBrush::GetRadiusY](../Topic/CD2DRadialGradientBrush::GetRadiusY.md)|检索该渐变椭圆的 y 半径|  
|[CD2DRadialGradientBrush::SetCenter](../Topic/CD2DRadialGradientBrush::SetCenter.md)|指定画笔坐标空间中的渐变椭圆的中心|  
|[CD2DRadialGradientBrush::SetGradientOriginOffset](../Topic/CD2DRadialGradientBrush::SetGradientOriginOffset.md)|指定该渐变原点相对于此渐变椭圆中心的偏移|  
|[CD2DRadialGradientBrush::SetRadiusX](../Topic/CD2DRadialGradientBrush::SetRadiusX.md)|指定画笔坐标空间中的渐变椭圆的 x 半径|  
|[CD2DRadialGradientBrush::SetRadiusY](../Topic/CD2DRadialGradientBrush::SetRadiusY.md)|指定画笔坐标空间中的渐变椭圆的 y 半径|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush\*](../Topic/CD2DRadialGradientBrush::operator%20ID2D1RadialGradientBrush*.md)|返回 ID2D1RadialGradientBrush 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DRadialGradientBrush::m\_pRadialGradientBrush](../Topic/CD2DRadialGradientBrush::m_pRadialGradientBrush.md)|指向 ID2D1RadialGradientBrush 的指针。|  
|[CD2DRadialGradientBrush::m\_RadialGradientBrushProperties](../Topic/CD2DRadialGradientBrush::m_RadialGradientBrushProperties.md)|画笔渐变的中心、渐变原点偏移和 x 轴半径及 y 轴半径。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 [CD2DRadialGradientBrush](../../mfc/reference/cd2dradialgradientbrush-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)