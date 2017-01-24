---
title: "CD2DMesh 类 | Microsoft Docs"
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
  - "afxrendertarget/CD2DMesh"
  - "CD2DMesh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DMesh 类"
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DMesh 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Mesh 的包装。  
  
## 语法  
  
```  
class CD2DMesh : public CD2DResource;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DMesh::CD2DMesh](../Topic/CD2DMesh::CD2DMesh.md)|构造 CD2DMesh 对象。|  
|[CD2DMesh::~CD2DMesh](../Topic/CD2DMesh::~CD2DMesh.md)|该析构函数。  当 D2D 网格对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DMesh::Attach](../Topic/CD2DMesh::Attach.md)|将现有的资源接口附加到该对象|  
|[CD2DMesh::Create](../Topic/CD2DMesh::Create.md)|创建 CD2DMesh。  （重写 [CD2DResource::Create](../Topic/CD2DResource::Create.md)。）|  
|[CD2DMesh::Destroy](../Topic/CD2DMesh::Destroy.md)|销毁 CD2DMesh 对象。  （重写 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)。）|  
|[CD2DMesh::Detach](../Topic/CD2DMesh::Detach.md)|将资源接口从该对象分离|  
|[CD2DMesh::Get](../Topic/CD2DMesh::Get.md)|返回 ID2D1Mesh 接口|  
|[CD2DMesh::IsValid](../Topic/CD2DMesh::IsValid.md)|检查资源有效性（重写 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)。）|  
|[CD2DMesh::Open](../Topic/CD2DMesh::Open.md)|打开用于填充的网格。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DMesh::operator ID2D1Mesh\*](../Topic/CD2DMesh::operator%20ID2D1Mesh*.md)|返回 ID2D1Mesh 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DMesh::m\_pMesh](../Topic/CD2DMesh::m_pMesh.md)|指向 ID2D1Mesh 的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DMesh](../../mfc/reference/cd2dmesh-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)