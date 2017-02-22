---
title: "CDCRenderTarget 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CDCRenderTarget"
  - "CDCRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDCRenderTarget 类"
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# CDCRenderTarget 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1DCRenderTarget 的包装。  
  
## 语法  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDCRenderTarget::CDCRenderTarget](../Topic/CDCRenderTarget::CDCRenderTarget.md)|构造 CDCRenderTarget 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDCRenderTarget::Attach](../Topic/CDCRenderTarget::Attach.md)|将现有的呈现器目标接口附加到该对象|  
|[CDCRenderTarget::BindDC](../Topic/CDCRenderTarget::BindDC.md)|将呈现器目标绑定到该呈现器目标要向其发出绘图命令的设备上下文|  
|[CDCRenderTarget::Create](../Topic/CDCRenderTarget::Create.md)|创建 CDCRenderTarget。|  
|[CDCRenderTarget::Detach](../Topic/CDCRenderTarget::Detach.md)|将呈现器目标接口从该对象分离|  
|[CDCRenderTarget::GetDCRenderTarget](../Topic/CDCRenderTarget::GetDCRenderTarget.md)|返回 ID2D1DCRenderTarget 接口|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget\*](../Topic/CDCRenderTarget::operator%20ID2D1DCRenderTarget*.md)|返回 ID2D1DCRenderTarget 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDCRenderTarget::m\_pDCRenderTarget](../Topic/CDCRenderTarget::m_pDCRenderTarget.md)|指向 ID2D1DCRenderTarget 对象的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)