---
title: "CBitmapRenderTarget 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CBitmapRenderTarget"
  - "CBitmapRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBitmapRenderTarget 类"
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# CBitmapRenderTarget 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1BitmapRenderTarget 的包装。  
  
## 语法  
  
```  
class CBitmapRenderTarget : public CRenderTarget;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CBitmapRenderTarget::CBitmapRenderTarget](../Topic/CBitmapRenderTarget::CBitmapRenderTarget.md)|构造 CBitmapRenderTarget 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CBitmapRenderTarget::Attach](../Topic/CBitmapRenderTarget::Attach.md)|将现有的呈现器目标接口附加到该对象|  
|[CBitmapRenderTarget::Detach](../Topic/CBitmapRenderTarget::Detach.md)|将呈现器目标接口从该对象分离|  
|[CBitmapRenderTarget::GetBitmap](../Topic/CBitmapRenderTarget::GetBitmap.md)|检索此呈现起目标的位图。  对于绘图操作，可以使用返回的位图。|  
|[CBitmapRenderTarget::GetBitmapRenderTarget](../Topic/CBitmapRenderTarget::GetBitmapRenderTarget.md)|返回 ID2D1BitmapRenderTarget 接口|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget\*](../Topic/CBitmapRenderTarget::operator%20ID2D1BitmapRenderTarget*.md)|返回 ID2D1BitmapRenderTarget 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CBitmapRenderTarget::m\_pBitmapRenderTarget](../Topic/CBitmapRenderTarget::m_pBitmapRenderTarget.md)|指向 ID2D1BitmapRenderTarget 对象的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CBitmapRenderTarget](../../mfc/reference/cbitmaprendertarget-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)