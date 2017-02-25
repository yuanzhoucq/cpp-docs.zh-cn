---
title: "CD2DGradientBrush 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DGradientBrush"
  - "afxrendertarget/CD2DGradientBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DGradientBrush 类"
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DGradientBrush 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CD2DLinearGradientBrush 和 CD2DRadialGradientBrush 类的基类。  
  
## 语法  
  
```  
class CD2DGradientBrush : public CD2DBrush;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DGradientBrush::CD2DGradientBrush](../Topic/CD2DGradientBrush::CD2DGradientBrush.md)|构造 CD2DGradientBrush 对象。|  
|[CD2DGradientBrush::~CD2DGradientBrush](../Topic/CD2DGradientBrush::~CD2DGradientBrush.md)|该析构函数。  当 D2D 渐变画笔对象被销毁时调用。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DGradientBrush::Destroy](../Topic/CD2DGradientBrush::Destroy.md)|销毁 CD2DGradientBrush 对象。  （重写 [CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md)。）|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DGradientBrush::m\_arGradientStops](../Topic/CD2DGradientBrush::m_arGradientStops.md)|D2D1\_GRADIENT\_STOP 结构的数组。|  
|[CD2DGradientBrush::m\_colorInterpolationGamma](../Topic/CD2DGradientBrush::m_colorInterpolationGamma.md)|在其中执行渐变停止点之间的颜色内插的空间。|  
|[CD2DGradientBrush::m\_extendMode](../Topic/CD2DGradientBrush::m_extendMode.md)|\[0，1\] 规范化范围之外该渐变的行为。|  
|[CD2DGradientBrush::m\_pGradientStops](../Topic/CD2DGradientBrush::m_pGradientStops.md)|指向 D2D1\_GRADIENT\_STOP 结构的数组的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)