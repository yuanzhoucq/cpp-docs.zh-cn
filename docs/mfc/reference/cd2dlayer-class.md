---
title: "CD2DLayer 类 | Microsoft Docs"
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
  - "afxrendertarget/CD2DLayer"
  - "CD2DLayer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DLayer 类"
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DLayer 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Layer 的包装。  
  
## 语法  
  
```  
class CD2DLayer : public CD2DResource;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DLayer::CD2DLayer](../Topic/CD2DLayer::CD2DLayer.md)|构造 CD2DLayer 对象。|  
|[CD2DLayer::~CD2DLayer](../Topic/CD2DLayer::~CD2DLayer.md)|该析构函数。  当 D2D 层对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DLayer::Attach](../Topic/CD2DLayer::Attach.md)|将现有的资源接口附加到该对象|  
|[CD2DLayer::Create](../Topic/CD2DLayer::Create.md)|创建 CD2DLayer。  （重写 [CD2DResource::Create](../Topic/CD2DResource::Create.md)。）|  
|[CD2DLayer::Destroy](../Topic/CD2DLayer::Destroy.md)|销毁 CD2DLayer 对象。  （重写 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)。）|  
|[CD2DLayer::Detach](../Topic/CD2DLayer::Detach.md)|将资源接口从该对象分离|  
|[CD2DLayer::Get](../Topic/CD2DLayer::Get.md)|返回 ID2D1Layer 接口|  
|[CD2DLayer::GetSize](../Topic/CD2DLayer::GetSize.md)|返回该呈现器目标的大小（以与设备无关的像素为单位）|  
|[CD2DLayer::IsValid](../Topic/CD2DLayer::IsValid.md)|检查资源有效性（重写 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)。）|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DLayer::operator ID2D1Layer\*](../Topic/CD2DLayer::operator%20ID2D1Layer*.md)|返回 ID2D1Layer 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DLayer::m\_pLayer](../Topic/CD2DLayer::m_pLayer.md)|存储指向 ID2D1Layer 对象的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DLayer](../../mfc/reference/cd2dlayer-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)