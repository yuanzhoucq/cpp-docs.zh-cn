---
title: "CCRTAllocator Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCRTAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCRTAllocator class"
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CCRTAllocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用CRT内存实例，此选件类用于管理内存的方法。  
  
## 语法  
  
```  
  
class ATL::CCRTAllocator  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCRTAllocator::Allocate](../Topic/CCRTAllocator::Allocate.md)|（静态）调用此方法分配内存。|  
|[CCRTAllocator::Free](../Topic/CCRTAllocator::Free.md)|（静态）调用此方法以释放内存。|  
|[CCRTAllocator::Reallocate](../Topic/CCRTAllocator::Reallocate.md)|（静态）调用此方法分配内存。|  
  
## 备注  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) 本选件类提供CRT内存分配例程。  使用COM实例，重复类别，[CComAllocator](../../atl/reference/ccomallocator-class.md)，提供相同的方法。  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CComAllocator Class](../../atl/reference/ccomallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)