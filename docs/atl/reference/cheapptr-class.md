---
title: "CHeapPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CHeapPtr"
  - "CHeapPtr"
  - "ATL.CHeapPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtr class"
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHeapPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

托管堆指针的智能指针选件类。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
typename T,  
class Allocator= CCRTAllocator  
> class CHeapPtr :  
public CHeapPtrBase< T, Allocator>  
```  
  
#### 参数  
 `T`  
 在堆中存储的对象类型。  
  
 `Allocator`  
 对于使用的内存分配选件类。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHeapPtr::CHeapPtr](../Topic/CHeapPtr::CHeapPtr.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHeapPtr::Allocate](../Topic/CHeapPtr::Allocate.md)|调用此方法分配堆中的内存存储在对象中。|  
|[CHeapPtr::Reallocate](../Topic/CHeapPtr::Reallocate.md)|调用此方法分配堆中的内存。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CHeapPtr::operator \=](../Topic/CHeapPtr::operator%20=.md)|赋值运算符。|  
  
## 备注  
 默认情况下`CHeapPtr` 从 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) 派生并使用CRT实例\(在 [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)\)分配和释放内存。  选件类 [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) 能用于构造列表堆指针。  请参见 [CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，使用COM内存分配例程。  
  
## 继承层次结构  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 `CHeapPtr`  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [CHeapPtrBase Class](../../atl/reference/cheapptrbase-class.md)   
 [CCRTAllocator Class](../../atl/reference/ccrtallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)