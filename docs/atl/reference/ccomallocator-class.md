---
title: "CComAllocator Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComAllocator"
  - "ATL::CComAllocator"
  - "CComAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAllocator class"
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComAllocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用COM内存实例，此选件类用于管理内存的方法。  
  
## 语法  
  
```  
  
class CComAllocator  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CComAllocator::Allocate](../Topic/CComAllocator::Allocate.md)|调用此静态方法分配内存。|  
|[CComAllocator::Free](../Topic/CComAllocator::Free.md)|调用此静态方法释放由分配的内存。|  
|[CComAllocator::Reallocate](../Topic/CComAllocator::Reallocate.md)|调用此静态方法分配内存。|  
  
## 备注  
 [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) 本选件类提供COM内存分配例程。  使用CRT实例，重复类别，[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)，提供相同的方法。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CComHeapPtr Class](../../atl/reference/ccomheapptr-class.md)   
 [CCRTAllocator Class](../../atl/reference/ccrtallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)