---
title: "CD2DSolidColorBrush 类 | Microsoft Docs"
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
  - "CD2DSolidColorBrush"
  - "afxrendertarget/CD2DSolidColorBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DSolidColorBrush 类"
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DSolidColorBrush 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1SolidColorBrush 的包装。  
  
## 语法  
  
```  
class CD2DSolidColorBrush : public CD2DBrush;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DSolidColorBrush::CD2DSolidColorBrush](../Topic/CD2DSolidColorBrush::CD2DSolidColorBrush.md)|已重载。  构造 CD2DSolidColorBrush 对象。|  
|[CD2DSolidColorBrush::~CD2DSolidColorBrush](../Topic/CD2DSolidColorBrush::~CD2DSolidColorBrush.md)|该析构函数。  当 D2D 实心画笔对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DSolidColorBrush::Attach](../Topic/CD2DSolidColorBrush::Attach.md)|将现有的资源接口附加到该对象|  
|[CD2DSolidColorBrush::Create](../Topic/CD2DSolidColorBrush::Create.md)|创建 CD2DSolidColorBrush。  （重写 [CD2DResource::Create](../Topic/CD2DResource::Create.md)。）|  
|[CD2DSolidColorBrush::Destroy](../Topic/CD2DSolidColorBrush::Destroy.md)|销毁 CD2DSolidColorBrush 对象。  （重写 [CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md)。）|  
|[CD2DSolidColorBrush::Detach](../Topic/CD2DSolidColorBrush::Detach.md)|将资源接口从该对象分离|  
|[CD2DSolidColorBrush::Get](../Topic/CD2DSolidColorBrush::Get.md)|返回 ID2D1SolidColorBrush 接口|  
|[CD2DSolidColorBrush::GetColor](../Topic/CD2DSolidColorBrush::GetColor.md)|检索该纯色画笔的颜色|  
|[CD2DSolidColorBrush::SetColor](../Topic/CD2DSolidColorBrush::SetColor.md)|指定此纯色画笔的颜色|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush\*](../Topic/CD2DSolidColorBrush::operator%20ID2D1SolidColorBrush*.md)|返回 ID2D1SolidColorBrush 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DSolidColorBrush::m\_colorSolid](../Topic/CD2DSolidColorBrush::m_colorSolid.md)|画笔纯色。|  
|[CD2DSolidColorBrush::m\_pSolidColorBrush](../Topic/CD2DSolidColorBrush::m_pSolidColorBrush.md)|存储指向 ID2D1SolidColorBrush 对象的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)