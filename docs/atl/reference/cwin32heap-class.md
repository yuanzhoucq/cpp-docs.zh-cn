---
title: "CWin32Heap Class | Microsoft Docs"
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
  - "ATL::CWin32Heap"
  - "ATL.CWin32Heap"
  - "CWin32Heap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWin32Heap class"
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWin32Heap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用Win32堆分配函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CWin32Heap : public IAtlMemMgr  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWin32Heap::CWin32Heap](../Topic/CWin32Heap::CWin32Heap.md)|构造函数。|  
|[CWin32Heap::~CWin32Heap](../Topic/CWin32Heap::~CWin32Heap.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWin32Heap::Allocate](../Topic/CWin32Heap::Allocate.md)|从堆对象分配内存块。|  
|[CWin32Heap::Attach](../Topic/CWin32Heap::Attach.md)|附加到现有的堆的堆对象。|  
|[CWin32Heap::Detach](../Topic/CWin32Heap::Detach.md)|分离从现有堆的堆对象。|  
|[CWin32Heap::Free](../Topic/CWin32Heap::Free.md)|释放从堆上分配的内存。|  
|[CWin32Heap::GetSize](../Topic/CWin32Heap::GetSize.md)|要返回的范围内存块从堆分配对象。|  
|[CWin32Heap::Reallocate](../Topic/CWin32Heap::Reallocate.md)|重新分配内存块从堆对象的。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CWin32Heap::m\_bOwnHeap](../Topic/CWin32Heap::m_bOwnHeap.md)|使用的标志确定堆处理的当前所有权。|  
|[CWin32Heap::m\_hHeap](../Topic/CWin32Heap::m_hHeap.md)|对于堆对象的句柄。|  
  
## 备注  
 使用Win32堆分配函数，包括 [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597) 和 [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701)，`CWin32Heap` 执行内存分配方法。  与其他堆选件类，`CWin32Heap`，在赋值之前，需要有效的堆句柄提供内存:其他选件类默认为使用处理堆。  句柄可发送给构造函数或写入 [CWin32Heap::Attach](../Topic/CWin32Heap::Attach.md) 方法。  有关更多详细信息参见 [CWin32Heap::CWin32Heap](../Topic/CWin32Heap::CWin32Heap.md) 方法。  
  
## 示例  
 为 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)参见示例。  
  
## 继承层次结构  
 `IAtlMemMgr`  
  
 `CWin32Heap`  
  
## 要求  
 **Header:** atlmem.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)