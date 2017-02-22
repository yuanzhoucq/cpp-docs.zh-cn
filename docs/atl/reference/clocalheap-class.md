---
title: "CLocalHeap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CLocalHeap"
  - "ATL::CLocalHeap"
  - "CLocalHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLocalHeap class"
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CLocalHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用Win32本地堆函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CLocalHeap : public IAtlMemMgr  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CLocalHeap::Allocate](../Topic/CLocalHeap::Allocate.md)|调用此方法分配内存块。|  
|[CLocalHeap::Free](../Topic/CLocalHeap::Free.md)|调用此方法可释放该内存管理器分配的内存块。|  
|[CLocalHeap::GetSize](../Topic/CLocalHeap::GetSize.md)|调用的已分配大小内存分配由此内存管理器的此方法获取。|  
|[CLocalHeap::Reallocate](../Topic/CLocalHeap::Reallocate.md)|调用此方法分配此内存管理器分配的内存。|  
  
## 备注  
 使用Win32本地堆函数，`CLocalHeap` 实现内存分配的分配函数。  
  
> [!NOTE]
>  本地堆函数比其他内存管理函数慢，并且不提供了多种功能。  因此，新应用程序应使用 [堆函数](http://msdn.microsoft.com/library/windows/desktop/aa366711)。  这些可在 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 选件类。  
  
## 示例  
 为 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)参见示例。  
  
## 继承层次结构  
 `IAtlMemMgr`  
  
 `CLocalHeap`  
  
## 要求  
 **Header:** atlmem.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)