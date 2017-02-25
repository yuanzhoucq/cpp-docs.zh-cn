---
title: "CD2DGeometrySink 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DGeometrySink"
  - "CD2DGeometrySink"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DGeometrySink 类"
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CD2DGeometrySink 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1GeometrySink 的包装。  
  
## 语法  
  
```  
class CD2DGeometrySink;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DGeometrySink::CD2DGeometrySink](../Topic/CD2DGeometrySink::CD2DGeometrySink.md)|从 CD2DPathGeometry 对象构造 CD2DGeometrySink 对象。|  
|[CD2DGeometrySink::~CD2DGeometrySink](../Topic/CD2DGeometrySink::~CD2DGeometrySink.md)|该析构函数。  当 D2D 几何图形接收器对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DGeometrySink::AddArc](../Topic/CD2DGeometrySink::AddArc.md)|将一段弧添加到路径几何图形|  
|[CD2DGeometrySink::AddBezier](../Topic/CD2DGeometrySink::AddBezier.md)|在当前点与指定的终点之间创建一条三次方贝塞尔曲线。|  
|[CD2DGeometrySink::AddBeziers](../Topic/CD2DGeometrySink::AddBeziers.md)|创建一系列三次方贝塞尔曲线，并将其添加到几何图形接收器。|  
|[CD2DGeometrySink::AddLine](../Topic/CD2DGeometrySink::AddLine.md)|在当前点与指定的终点之间创建一条线段，然后将其添加到几何图形接收器。|  
|[CD2DGeometrySink::AddLines](../Topic/CD2DGeometrySink::AddLines.md)|创建一系列使用指定点的线条，并将其添加到几何图形接收器。|  
|[CD2DGeometrySink::AddQuadraticBezier](../Topic/CD2DGeometrySink::AddQuadraticBezier.md)|在当前点与指定的终点之间创建一条二次贝塞尔曲线。|  
|[CD2DGeometrySink::AddQuadraticBeziers](../Topic/CD2DGeometrySink::AddQuadraticBeziers.md)|将一系列二次贝赛尔线段添加为单个调用中的数组。|  
|[CD2DGeometrySink::BeginFigure](../Topic/CD2DGeometrySink::BeginFigure.md)|在指定点开始新图形。|  
|[CD2DGeometrySink::Close](../Topic/CD2DGeometrySink::Close.md)|关闭几何图形接收器|  
|[CD2DGeometrySink::EndFigure](../Topic/CD2DGeometrySink::EndFigure.md)|结束当前图像；也可以选择将其关闭。|  
|[CD2DGeometrySink::Get](../Topic/CD2DGeometrySink::Get.md)|返回 ID2D1GeometrySink 接口|  
|[CD2DGeometrySink::IsValid](../Topic/CD2DGeometrySink::IsValid.md)|检查几何图形接收器有效性|  
|[CD2DGeometrySink::SetFillMode](../Topic/CD2DGeometrySink::SetFillMode.md)|指定用于确定在此几何图形接收器描述的几何图形内的那些点以及在其之外的那些点的方法。|  
|[CD2DGeometrySink::SetSegmentFlags](../Topic/CD2DGeometrySink::SetSegmentFlags.md)|指定要应用于添加到该几何图形接收器的新线段的笔画和联接选项。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DGeometrySink::operator ID2D1GeometrySink\*](../Topic/CD2DGeometrySink::operator%20ID2D1GeometrySink*.md)|返回 ID2D1GeometrySink 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DGeometrySink::m\_pSink](../Topic/CD2DGeometrySink::m_pSink.md)|指向 ID2D1GeometrySink 的指针。|  
  
## 继承层次结构  
 [CD2DGeometrySink](../../mfc/reference/cd2dgeometrysink-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)