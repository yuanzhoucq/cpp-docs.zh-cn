---
title: "CHwndRenderTarget 类 | Microsoft Docs"
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
  - "CHwndRenderTarget"
  - "afxrendertarget/CHwndRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHwndRenderTarget 类"
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHwndRenderTarget 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1HwndRenderTarget 的包装。  
  
## 语法  
  
```  
class CHwndRenderTarget : public CRenderTarget;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHwndRenderTarget::CHwndRenderTarget](../Topic/CHwndRenderTarget::CHwndRenderTarget.md)|从 HWND 构造 CHwndRenderTarget 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHwndRenderTarget::Attach](../Topic/CHwndRenderTarget::Attach.md)|将现有的呈现器目标接口附加到该对象|  
|[CHwndRenderTarget::CheckWindowState](../Topic/CHwndRenderTarget::CheckWindowState.md)|指示与此呈现器目标关联的 HWND 是否已封闭。|  
|[CHwndRenderTarget::Create](../Topic/CHwndRenderTarget::Create.md)|创建与此窗口关联的呈现器目标。|  
|[CHwndRenderTarget::Detach](../Topic/CHwndRenderTarget::Detach.md)|将呈现器目标接口从该对象分离|  
|[CHwndRenderTarget::GetHwnd](../Topic/CHwndRenderTarget::GetHwnd.md)|返回与此呈现器目标关联的 HWND。|  
|[CHwndRenderTarget::GetHwndRenderTarget](../Topic/CHwndRenderTarget::GetHwndRenderTarget.md)|返回 ID2D1HwndRenderTarget 接口。|  
|[CHwndRenderTarget::ReCreate](../Topic/CHwndRenderTarget::ReCreate.md)|重新创建与该窗口关联的呈现器目标|  
|[CHwndRenderTarget::Resize](../Topic/CHwndRenderTarget::Resize.md)|将呈现器目标的大小更改为指定的像素大小。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget\*](../Topic/CHwndRenderTarget::operator%20ID2D1HwndRenderTarget*.md)|返回 ID2D1HwndRenderTarget 接口。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CHwndRenderTarget::m\_pHwndRenderTarget](../Topic/CHwndRenderTarget::m_pHwndRenderTarget.md)|指向 ID2D1HwndRenderTarget 对象的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)