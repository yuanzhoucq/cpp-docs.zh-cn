---
title: "CGlobalHeap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CGlobalHeap"
  - "ATL::CGlobalHeap"
  - "CGlobalHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGlobalHeap class"
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CGlobalHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用Win32全局堆函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CGlobalHeap : public IAtlMemMgr  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CGlobalHeap::Allocate](../Topic/CGlobalHeap::Allocate.md)|调用此方法分配内存块。|  
|[CGlobalHeap::Free](../Topic/CGlobalHeap::Free.md)|调用此方法可释放该内存管理器分配的内存块。|  
|[CGlobalHeap::GetSize](../Topic/CGlobalHeap::GetSize.md)|调用的已分配大小内存分配由此内存管理器的此方法获取。|  
|[CGlobalHeap::Reallocate](../Topic/CGlobalHeap::Reallocate.md)|调用此方法分配此内存管理器分配的内存。|  
  
## 备注  
 使用Win32全局堆函数，`CGlobalHeap` 实现内存分配的分配函数。  
  
> [!NOTE]
>  全局堆函数比其他内存管理函数慢，并且不提供了多种功能。  因此，新应用程序应使用 [堆函数](http://msdn.microsoft.com/library/windows/desktop/aa366711)。  这些可在 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 选件类。  DDE和剪贴板功能仍然使用全局函数。  
  
## 示例  
 为 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)参见示例。  
  
## 继承层次结构  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## 要求  
 **Header:** atlmem.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)