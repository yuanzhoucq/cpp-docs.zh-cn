---
title: "allocator_base 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators.allocator_base"
  - "stdext.allocators.allocator_base"
  - "allocator_base"
  - "allocators/stdext::allocator_base"
  - "stdext::allocator_base"
  - "stdext::allocators::allocator_base"
  - "allocators/stdext::allocators::allocator_base"
  - "allocators::allocator_base"
  - "stdext.allocator_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_base 类"
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# allocator_base 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义基类和常用函数需要从同步筛选器创建一个用户定义的分配器。  
  
## 语法  
  
```  
template <class Type, class Sync> class allocator_base  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`Type`|由分配器分配元素类型。|  
|`Sync`|分配器的同步策略有 [sync\_none 类](../standard-library/sync-none-class.md)、[sync\_per\_container 类](../standard-library/sync-per-container-class.md)、[sync\_per\_thread 类](../standard-library/sync-per-thread-class.md) 或 [sync\_shared 类](../standard-library/sync-shared-class.md)。|  
  
### 构造函数  
  
|||  
|-|-|  
|[allocator\_base](../Topic/allocator_base::allocator_base.md)|构造 `allocator_base` 类型的对象。|  
  
### TypeDefs  
  
|||  
|-|-|  
|[const\_pointer](../Topic/allocator_base::const_pointer.md)|提供指向由分配器管理的对象类型的常量指针的类型。|  
|[const\_reference](../Topic/allocator_base::const_reference.md)|提供对由分配器管理的对象类型的常量引用的类型。|  
|[difference\_type](../Topic/allocator_base::difference_type.md)|有符号的整型，可以表示指向由分配器管理的对象类型的指针值之间的差异。|  
|[指针](../Topic/allocator_base::pointer.md)|提供指向由分配器管理的对象类型的指针的类型。|  
|[引用](../Topic/allocator_base::reference.md)|提供指向对分配器管理的对象类型的引用的类型。|  
|[size\_type](../Topic/allocator_base::size_type.md)|无符号整型，可以表示模板类 `allocator_base` 的对象可以分配的任何序列的长度。|  
|[value\_type](../Topic/allocator_base::value_type.md)|由分配器管理的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[\_Charalloc](../Topic/allocator_base::_Charalloc.md)|为 `char` 类型的数组分配存储。|  
|[\_Chardealloc](../Topic/allocator_base::_Chardealloc.md)|为包含 `char` 类型元素的数组释放存储。|  
|[地址](../Topic/allocator_base::address.md)|查找指定了其值的对象的地址。|  
|[allocate](../Topic/allocator_base::allocate.md)|分配大小足以存储至少某个指定数量的元素的内存块。|  
|[构造](../Topic/allocator_base::construct.md)|在使用指定值初始化的指定地址处构造特定类型的对象。|  
|[释放](../Topic/allocator_base::deallocate.md)|从指定位置开始从存储中释放指定数量的的对象。|  
|[销毁](../Topic/allocator_base::destroy.md)|调用对象析构函数而不释放存储对象的内存。|  
|[max\_size](../Topic/allocator_base::max_size.md)|在可用内存用完之前，返回可以由类分配器的对象分配的类型 `Type` 的元素数。|  
  
## 要求  
 **标头：** \<allocators\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<allocators\>](../standard-library/allocators-header.md)