---
title: "rts_alloc 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::rts_alloc"
  - "allocators/stdext::rts_alloc"
  - "rts_alloc"
  - "stdext.rts_alloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rts_alloc 类"
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# rts_alloc 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

rts\_alloc 模板类描述一种[筛选器](../standard-library/allocators-header.md)，它具有缓存实例数组，并确定运行时（而非编译时）用于分配和解除分配的实例。  
  
## 语法  
  
```  
template <class Cache> class rts_alloc  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Cache`|数组中包含的缓存实例的类型。  这可能是 [cache\_chunklist 类](../standard-library/cache-chunklist-class.md)、[cache\_freelist](../standard-library/cache-freelist-class.md) 或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
## 备注  
 此模板类持有多个块分配器实例，并确定运行时（而非编译时）用于分配或解除分配的实例。  它与不能编译重新绑定的编译器一起使用。  
  
### 成员函数  
  
|||  
|-|-|  
|[allocate](../Topic/rts_alloc::allocate.md)|分配内存块。|  
|[释放](../Topic/rts_alloc::deallocate.md)|从指定位置开始从存储中释放指定数量的的对象。|  
|[等于](../Topic/rts_alloc::equals.md)|比较两个缓存是否相等。|  
  
## 要求  
 **标头：**\<allocators\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md)   
 [\<allocators\>](../standard-library/allocators-header.md)