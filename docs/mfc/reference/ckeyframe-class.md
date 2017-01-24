---
title: "CKeyFrame 类 | Microsoft Docs"
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
  - "afxanimationcontroller/CKeyFrame"
  - "CKeyFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CKeyFrame 类"
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CKeyFrame 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示动画关键帧。  
  
## 语法  
  
```  
class CKeyFrame : public CBaseKeyFrame;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CKeyFrame::CKeyFrame](../Topic/CKeyFrame::CKeyFrame.md)|已重载。  构造取决于其他关键帧的关键帧。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CKeyFrame::AddToStoryboard](../Topic/CKeyFrame::AddToStoryboard.md)|将关键帧添加到情节提要。  （重写 [CBaseKeyFrame::AddToStoryboard](../Topic/CBaseKeyFrame::AddToStoryboard.md)。）|  
|[CKeyFrame::AddToStoryboardAfterTransition](../Topic/CKeyFrame::AddToStoryboardAfterTransition.md)|将关键帧添加到转换后的情节提要。|  
|[CKeyFrame::AddToStoryboardAtOffset](../Topic/CKeyFrame::AddToStoryboardAtOffset.md)|将关键帧添加到偏移位置的情节提要。|  
|[CKeyFrame::GetExistingKeyframe](../Topic/CKeyFrame::GetExistingKeyframe.md)|返回指向此关键帧所依赖的关键帧的指针。|  
|[CKeyFrame::GetOffset](../Topic/CKeyFrame::GetOffset.md)|返回其他关键帧的偏移。|  
|[CKeyFrame::GetTransition](../Topic/CKeyFrame::GetTransition.md)|返回指向此关键帧所依赖的转换的指针。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CKeyFrame::m\_offset](../Topic/CKeyFrame::m_offset.md)|指定此关键帧从存储在 m\_pExistingKeyFrame 中的关键帧产生的偏移。|  
|[CKeyFrame::m\_pExistingKeyFrame](../Topic/CKeyFrame::m_pExistingKeyFrame.md)|存储指向现有关键帧的指针。  将此关键帧添加到具有现有关键帧的 m\_offset 的情节提要。|  
|[CKeyFrame::m\_pTransition](../Topic/CKeyFrame::m_pTransition.md)|存储指向从此关键帧开始的转换的指针。|  
  
## 备注  
 此类实现动画关键帧。  关键帧表示情节提要中时间的某一时刻，并可用于指定转换的开始时间和结束时间。  关键帧以其他关键帧为基础，并从该关键帧发生偏移（以秒为单位），或者以某个转换为基础，并表示该转换结束时间中的某一时刻。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
 [CKeyFrame](../../mfc/reference/ckeyframe-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)