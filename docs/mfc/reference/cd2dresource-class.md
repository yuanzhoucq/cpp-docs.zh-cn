---
title: "CD2DResource 类 | Microsoft Docs"
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
  - "afxrendertarget/CD2DResource"
  - "CD2DResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DResource 类"
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DResource 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为创建和管理 D2D 资源（例如画笔、层和文本）提供接口的抽象类。  
  
## 语法  
  
```  
class CD2DResource : public CObject;  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DResource::CD2DResource](../Topic/CD2DResource::CD2DResource.md)|构造 CD2DResource 对象。|  
|[CD2DResource::~CD2DResource](../Topic/CD2DResource::~CD2DResource.md)|该析构函数。  当 D2D 源对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DResource::Create](../Topic/CD2DResource::Create.md)|创建 CD2DResource。|  
|[CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)|销毁 CD2DResource 对象。|  
|[CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)|检查资源有效性|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DResource::IsAutoDestroy](../Topic/CD2DResource::IsAutoDestroy.md)|检查自动销毁标志。|  
|[CD2DResource::ReCreate](../Topic/CD2DResource::ReCreate.md)|重新创建 CD2DResource。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DResource::m\_bIsAutoDestroy](../Topic/CD2DResource::m_bIsAutoDestroy.md)|资源将由所有者销毁 （CRenderTarget）|  
|[CD2DResource::m\_pParentTarget](../Topic/CD2DResource::m_pParentTarget.md)|指向父级 CRenderTarget 的指针|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)