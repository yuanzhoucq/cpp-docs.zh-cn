---
title: "CCRTHeap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CCRTHeap"
  - "ATL.CCRTHeap"
  - "CCRTHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCRTHeap class"
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CCRTHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用CRT堆函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## 语法  
  
```  
  
class CCRTHeap : public IAtlMemMgr  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCRTHeap::Allocate](../Topic/CCRTHeap::Allocate.md)|调用此方法分配内存块。|  
|[CCRTHeap::Free](../Topic/CCRTHeap::Free.md)|调用此方法可释放该内存管理器分配的内存块。|  
|[CCRTHeap::GetSize](../Topic/CCRTHeap::GetSize.md)|调用的已分配大小内存分配由此内存管理器的此方法获取。|  
|[CCRTHeap::Reallocate](../Topic/CCRTHeap::Reallocate.md)|调用此方法分配此内存管理器分配的内存。|  
  
## 备注  
 使用CRT堆函数，包括 [malloc](../../c-runtime-library/reference/malloc.md)、 [免](../../c-runtime-library/reference/free.md)、 [realloc](../../c-runtime-library/reference/realloc.md)和 [\_msize](../../c-runtime-library/reference/msize.md)，`CCRTHeap` 实现内存分配的分配函数。  
  
## 示例  
 为 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)参见示例。  
  
## 继承层次结构  
 `IAtlMemMgr`  
  
 `CCRTHeap`  
  
## 要求  
 **Header:** atlmem.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)