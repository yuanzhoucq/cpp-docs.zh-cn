---
title: "CD2DBrush 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DBrush"
  - "afxrendertarget/CD2DBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DBrush 类"
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DBrush 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Brush 的包装。  
  
## 语法  
  
```  
class CD2DBrush : public CD2DResource;  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DBrush::CD2DBrush](../Topic/CD2DBrush::CD2DBrush.md)|构造 CD2DBrush 对象。|  
|[CD2DBrush::~CD2DBrush](../Topic/CD2DBrush::~CD2DBrush.md)|该析构函数。  当 D2D 画笔对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DBrush::Attach](../Topic/CD2DBrush::Attach.md)|将现有的资源接口附加到该对象|  
|[CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md)|销毁 CD2DBrush 对象。  （重写 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)。）|  
|[CD2DBrush::Detach](../Topic/CD2DBrush::Detach.md)|将资源接口从该对象分离|  
|[CD2DBrush::Get](../Topic/CD2DBrush::Get.md)|返回 ID2D1Brush 接口|  
|[CD2DBrush::GetOpacity](../Topic/CD2DBrush::GetOpacity.md)|获取此画笔的不透明度|  
|[CD2DBrush::GetTransform](../Topic/CD2DBrush::GetTransform.md)|获取该呈现器目标的当前转换。|  
|[CD2DBrush::IsValid](../Topic/CD2DBrush::IsValid.md)|检查资源有效性（重写 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)。）|  
|[CD2DBrush::SetOpacity](../Topic/CD2DBrush::SetOpacity.md)|设置此画笔的不透明度|  
|[CD2DBrush::SetTransform](../Topic/CD2DBrush::SetTransform.md)|将指定的转换应用到将替换现有转换的呈现器目标。  所有后续的绘图操作将在转换后的空间中进行|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DBrush::operator ID2D1Brush\*](../Topic/CD2DBrush::operator%20ID2D1Brush*.md)|返回 ID2D1Brush 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DBrush::m\_pBrush](../Topic/CD2DBrush::m_pBrush.md)|存储指向 ID2D1Brush 对象的指针。|  
|[CD2DBrush::m\_pBrushProperties](../Topic/CD2DBrush::m_pBrushProperties.md)|画笔属性。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)