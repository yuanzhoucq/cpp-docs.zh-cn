---
title: "CHeapPtrBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CHeapPtrBase"
  - "ATL::CHeapPtrBase"
  - "CHeapPtrBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtrBase class"
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHeapPtrBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类窗体进行一些智能堆指针选件类的基础。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T,  
class Allocator= CCRTAllocator   
> class CHeapPtrBase  
```  
  
#### 参数  
 `T`  
 在堆中存储的对象类型。  
  
 `Allocator`  
 对于使用的内存分配选件类。  默认情况下CRT实例用于分配和释放内存。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHeapPtrBase::~CHeapPtrBase](../Topic/CHeapPtrBase::~CHeapPtrBase.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHeapPtrBase::AllocateBytes](../Topic/CHeapPtrBase::AllocateBytes.md)|调用此方法分配内存。|  
|[CHeapPtrBase::Attach](../Topic/CHeapPtrBase::Attach.md)|调用此方法将现有指针的所有权。|  
|[CHeapPtrBase::Detach](../Topic/CHeapPtrBase::Detach.md)|调用此方法释放指针的所有权。|  
|[CHeapPtrBase::Free](../Topic/CHeapPtrBase::Free.md)|调用此方法删除点的对象。`CHeapPtrBase`。|  
|[CHeapPtrBase::ReallocateBytes](../Topic/CHeapPtrBase::ReallocateBytes.md)|调用此方法分配内存。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CHeapPtrBase::operator T\*](../Topic/CHeapPtrBase::operator%20T*.md)|转换运算符。|  
|[CHeapPtrBase::operator &](../Topic/CHeapPtrBase::operator%20&.md)|& 运算符。|  
|[CHeapPtrBase::operator \-\>](../Topic/CHeapPtrBase::operator%20-%3E.md)|指向成员的指针运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CHeapPtrBase::m\_pData](../Topic/CHeapPtrBase::m_pData.md)|指针数据成员变量。|  
  
## 备注  
 此选件类窗体进行一些智能堆指针选件类的基础。  派生类，例如，[CHeapPtr](../../atl/reference/cheapptr-class.md) 和 [CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，添加其构造函数和运算符。  为实现示例参见以下选件类。  
  
## 要求  
 **Header:** atlcore.h  
  
## 请参阅  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CComHeapPtr Class](../../atl/reference/ccomheapptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)