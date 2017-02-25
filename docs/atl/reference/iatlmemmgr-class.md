---
title: "IAtlMemMgr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAtlMemMgr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlMemMgr class"
  - "内存, 管理"
  - "内存, memory manager"
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# IAtlMemMgr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示界面内存管理器。  
  
## 语法  
  
```  
  
__interface __declspec( uuid( "654F7EF5-CFDF-4df9-A450-6C6A13C622C0" )) IAtlMemMgr  
  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[分配](../Topic/IAtlMemMgr::Allocate.md)|调用此方法分配内存块。|  
|[自由](../Topic/IAtlMemMgr::Free.md)|调用此方法可释放内存块。|  
|[GetSize](../Topic/IAtlMemMgr::GetSize.md)|调用此方法检索分配的内存块范围。|  
|[重新分配](../Topic/IAtlMemMgr::Reallocate.md)|调用此方法分配内存块。|  
  
## 备注  
 此接口由 [CComHeap](../../atl/reference/ccomheap-class.md)、 [CCRTHeap](../../atl/reference/ccrtheap-class.md)、 [CLocalHeap](../../atl/reference/clocalheap-class.md)、 [CGlobalHeap](../../atl/reference/cglobalheap-class.md)或 [CWin32Heap](../../atl/reference/cwin32heap-class.md)实现。  
  
> [!NOTE]
>  本地资源文件和全局堆函数比其他内存管理函数慢不提供了多种功能。  因此，新应用程序应使用 [堆函数](http://msdn.microsoft.com/library/windows/desktop/aa366711)。  这些可在 [CWin32Heap](../../atl/reference/cwin32heap-class.md) 选件类。  
  
## 示例  
 [!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/CPP/iatlmemmgr-class_1.cpp)]  
  
## 要求  
 **Header:** atlmem.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)