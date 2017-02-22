---
title: "CComHeap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComHeap"
  - "ATL.CComHeap"
  - "ATL::CComHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComHeap class"
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CComHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用COM内存分配的分配函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CComHeap : public IAtlMemMgr  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComHeap::Allocate](../Topic/CComHeap::Allocate.md)|调用此方法分配内存块。|  
|[CComHeap::Free](../Topic/CComHeap::Free.md)|调用此方法可释放该内存管理器分配的内存块。|  
|[CComHeap::GetSize](../Topic/CComHeap::GetSize.md)|调用的已分配大小内存分配由此内存管理器的此方法获取。|  
|[CComHeap::Reallocate](../Topic/CComHeap::Reallocate.md)|调用此方法分配此内存管理器分配的内存。|  
  
## 备注  
 使用COM分配功能，包括 [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)、 [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)、 [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)和 [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)，`CComHeap` 实现内存分配的分配函数。  可以分配的最大数量内存等于 **INT\_MAX** \(2147483647个字节）。  
  
## 示例  
 为 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)参见示例。  
  
## 继承层次结构  
 `IAtlMemMgr`  
  
 `CComHeap`  
  
## 要求  
 **Header:** ATLComMem.h  
  
## 请参阅  
 [DynamicConsumer示例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)