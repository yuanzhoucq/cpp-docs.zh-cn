---
title: "CComHeapPtr Class | Microsoft Docs"
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
  - "ATL::CComHeapPtr"
  - "ATL.CComHeapPtr<T>"
  - "ATL::CComHeapPtr<T>"
  - "CComHeapPtr"
  - "ATL.CComHeapPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComHeapPtr class"
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComHeapPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

托管堆指针的智能指针选件类。  
  
## 语法  
  
```  
  
      template<  
   typename T  
> class CComHeapPtr :  
   public CHeapPtr< T, CComAllocator >  
```  
  
#### 参数  
 `T`  
 在堆中存储的对象类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComHeapPtr::CComHeapPtr](../Topic/CComHeapPtr::CComHeapPtr.md)|构造函数。|  
  
## 备注  
 `CComHeapPtr` 从 `CHeapPtr`，但是，使用 [CComAllocator](../../atl/reference/ccomallocator-class.md) 派生分配内存使用COM实例。  有关可用的方法参见 [CHeapPtr](../../atl/reference/cheapptr-class.md) 和 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)。  
  
## 继承层次结构  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)  
  
 `CComHeapPtr`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrBase Class](../../atl/reference/cheapptrbase-class.md)   
 [CComAllocator Class](../../atl/reference/ccomallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)