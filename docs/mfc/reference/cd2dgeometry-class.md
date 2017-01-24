---
title: "CD2DGeometry 类 | Microsoft Docs"
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
  - "CD2DGeometry"
  - "afxrendertarget/CD2DGeometry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DGeometry 类"
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DGeometry 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Geometry 的包装。  
  
## 语法  
  
```  
class CD2DGeometry : public CD2DResource;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DGeometry::CD2DGeometry](../Topic/CD2DGeometry::CD2DGeometry.md)|构造 CD2DGeometry 对象。|  
|[CD2DGeometry::~CD2DGeometry](../Topic/CD2DGeometry::~CD2DGeometry.md)|该析构函数。  当 D2D 几何图形对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DGeometry::Attach](../Topic/CD2DGeometry::Attach.md)|将现有的资源接口附加到该对象|  
|[CD2DGeometry::CombineWithGeometry](../Topic/CD2DGeometry::CombineWithGeometry.md)|将此几何图形与指定的几何图形合并，并将该结果存储在 ID2D1SimplifiedGeometrySink 中。|  
|[CD2DGeometry::CompareWithGeometry](../Topic/CD2DGeometry::CompareWithGeometry.md)|描述此几何图形与指定的几何图形之间的交集。  使用指定的拼合容差进行比较。|  
|[CD2DGeometry::ComputeArea](../Topic/CD2DGeometry::ComputeArea.md)|在几何图形由指定的矩阵转化并使用指定的公差单一化之后，计算该几何图形的面积。|  
|[CD2DGeometry::ComputeLength](../Topic/CD2DGeometry::ComputeLength.md)|假定将每条线段铺成一条线，然后计算该几何图形的长度。|  
|[CD2DGeometry::ComputePointAtLength](../Topic/CD2DGeometry::ComputePointAtLength.md)|在几何图形由指定的矩阵转化并使用指定的公差单一化之后，计算在该几何图形的指定距离处的点和正切向量。|  
|[CD2DGeometry::Destroy](../Topic/CD2DGeometry::Destroy.md)|销毁 CD2DGeometry 对象。  （重写 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)。）|  
|[CD2DGeometry::Detach](../Topic/CD2DGeometry::Detach.md)|将资源接口从该对象分离|  
|[CD2DGeometry::FillContainsPoint](../Topic/CD2DGeometry::FillContainsPoint.md)|指示在提供指定的拼合容差时，由几何图形填充的区域是否会包含指定的点。|  
|[CD2DGeometry::Get](../Topic/CD2DGeometry::Get.md)|返回 ID2D1Geometry 接口|  
|[CD2DGeometry::GetBounds](../Topic/CD2DGeometry::GetBounds.md)||  
|[CD2DGeometry::GetWidenedBounds](../Topic/CD2DGeometry::GetWidenedBounds.md)|在几何图形由指定的笔画宽度和样式加宽并使用指定的矩阵转化之后，获取该几何图形的边界。|  
|[CD2DGeometry::IsValid](../Topic/CD2DGeometry::IsValid.md)|检查资源有效性（重写 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)。）|  
|[CD2DGeometry::Outline](../Topic/CD2DGeometry::Outline.md)|计算该几何形状的边框，并将该结果写入 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::Simplify](../Topic/CD2DGeometry::Simplify.md)|创建只包含线条和（可选）三次贝塞尔曲线的几何图形的简化版本，并将该结果写入 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::StrokeContainsPoint](../Topic/CD2DGeometry::StrokeContainsPoint.md)|确定该几何图形的笔划是否包含指定点（提供指定的笔划粗细、样式和转换）。|  
|[CD2DGeometry::Tessellate](../Topic/CD2DGeometry::Tessellate.md)|在几何图形使用指定的矩阵转化并使用指定的公差单一化之后，创建一组涵盖该几何图形的以顺时针顺序环绕的三角形。|  
|[CD2DGeometry::Widen](../Topic/CD2DGeometry::Widen.md)|在该几何图形由指定的矩阵转换并使用指定的公差单一化之后，通过指定的笔画加宽该几何图形，并将该结果写入 ID2D1SimplifiedGeometrySink。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DGeometry::operator ID2D1Geometry\*](../Topic/CD2DGeometry::operator%20ID2D1Geometry*.md)|返回 ID2D1Geometry 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DGeometry::m\_pGeometry](../Topic/CD2DGeometry::m_pGeometry.md)|指向 ID2D1Geometry 的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)