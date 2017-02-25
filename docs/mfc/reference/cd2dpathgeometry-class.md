---
title: "CD2DPathGeometry 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DPathGeometry"
  - "CD2DPathGeometry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DPathGeometry 类"
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DPathGeometry 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1PathGeometry 的包装。  
  
## 语法  
  
```  
class CD2DPathGeometry : public CD2DGeometry;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DPathGeometry::CD2DPathGeometry](../Topic/CD2DPathGeometry::CD2DPathGeometry.md)|构造 CD2DPathGeometry 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DPathGeometry::Attach](../Topic/CD2DPathGeometry::Attach.md)|将现有的资源接口附加到该对象|  
|[CD2DPathGeometry::Create](../Topic/CD2DPathGeometry::Create.md)|创建 CD2DPathGeometry。  （重写 [CD2DResource::Create](../Topic/CD2DResource::Create.md)。）|  
|[CD2DPathGeometry::Destroy](../Topic/CD2DPathGeometry::Destroy.md)|销毁 CD2DPathGeometry 对象。  （重写 [CD2DGeometry::Destroy](../Topic/CD2DGeometry::Destroy.md)。）|  
|[CD2DPathGeometry::Detach](../Topic/CD2DPathGeometry::Detach.md)|将资源接口从该对象分离|  
|[CD2DPathGeometry::GetFigureCount](../Topic/CD2DPathGeometry::GetFigureCount.md)|检索路径几何图形中图形的数量。|  
|[CD2DPathGeometry::GetSegmentCount](../Topic/CD2DPathGeometry::GetSegmentCount.md)|检索路径几何图形中的段数。|  
|[CD2DPathGeometry::Open](../Topic/CD2DPathGeometry::Open.md)|检索用于使用图形和线段填充路径几何图形的几何图形接收器。|  
|[CD2DPathGeometry::Stream](../Topic/CD2DPathGeometry::Stream.md)|将该路径几何图形的内容复制到指定的 ID2D1GeometrySink。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DPathGeometry::m\_pPathGeometry](../Topic/CD2DPathGeometry::m_pPathGeometry.md)|指向 ID2D1PathGeometry 的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
 [CD2DPathGeometry](../../mfc/reference/cd2dpathgeometry-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)