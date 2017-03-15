---
title: "allocator_traits 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::allocator_traits"
  - "memory/std::allocator_traits::propagate_on_container_move_assignment"
  - "memory/std::allocator_traits::const_pointer"
  - "memory/std::allocator_traits::propagate_on_container_swap"
  - "memory/std::allocator_traits::propagate_on_container_copy_assignment"
  - "memory/std::allocator_traits::difference_type"
  - "memory/std::allocator_traits::allocator_type"
  - "memory/std::allocator_traits::value_type"
  - "memory/std::allocator_traits::pointer"
  - "memory/std::allocator_traits::size_type"
  - "memory/std::allocator_traits::const_void_pointer"
  - "memory/std::allocator_traits::void_pointer"
dev_langs: 
  - "C++"
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# allocator_traits 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类描述对象向 *分配程序类型*。  分配程序类型是描述一发行程序对象用于管理的存储分配使用的任何类型。  具体而言，用于任何分配程序类型 `Alloc`，您可以使用 `allocator_traits<Alloc>` 将程序启用由容器所需的所有信息。  有关更多信息，请参见 [allocator 类](../standard-library/allocator-class.md)默认。  
  
## 语法  
  
```cpp  
template<class Alloc>  
    class allocator_traits;  
```  
  
### Typedef  
  
|Name|说明|  
|----------|--------|  
|`allocator_traits::allocator_type`|此类型是的同义词。`Alloc`模板参数|  
|`allocator_traits::const_pointer`|如果该类型的标准格式，此类型是 `Alloc::const_pointer`;否则，此类型是 `pointer_traits<pointer>::rebind<const value_type>`。|  
|`allocator_traits::const_void_pointer`|如果该类型的标准格式，此类型是 `Alloc::const_void_pointer`;否则，此类型是 `pointer_traits<pointer>::rebind<const void>`。|  
|`allocator_traits::difference_type`|如果该类型的标准格式，此类型是 `Alloc::difference_type`;否则，此类型是 `pointer_traits<pointer>::difference_type`。|  
|`allocator_traits::pointer`|如果该类型的标准格式，此类型是 `Alloc::pointer`;否则，此类型是 `value_type *`。|  
|`allocator_traits::propagate_on_container_copy_assignment`|如果该类型的标准格式，此类型是 `Alloc::propagate_on_container_copy_assignment`;否则，此类型是 `false_type`。|  
|`allocator_traits::propagate_on_container_move_assignment`|如果该类型的标准格式，此类型是 `Alloc::propagate_on_container_move_assignment`;否则，此类型是 `false_type`。  如果类型应用，将程序启用容器复制其在移动分配的存储分配程序。|  
|`allocator_traits::propagate_on_container_swap`|如果该类型的标准格式，此类型是 `Alloc::propagate_on_container_swap`;否则，此类型是 `false_type`。  如果类型应用，将程序启用容器交换其在交换的存储分配程序。|  
|`allocator_traits::size_type`|如果该类型的标准格式，此类型是 `Alloc::size_type`;否则，此类型是 `make_unsigned<difference_type>::type`。|  
|`allocator_traits::value_type`|此类型是的同义词。`Alloc::value_type`|  
|`allocator_traits::void_pointer`|如果该类型的标准格式，此类型是 `Alloc::void_pointer`;否则，此类型是 `pointer_traits<pointer>::rebind<void>`。|  
  
### 静态方法  
 以下静态方法对特定分配程序参数的相应方法。  
  
|Name|说明|  
|----------|--------|  
|[allocator\_traits::allocate 方法](../Topic/allocator_traits::allocate%20Method.md)|使用特定分配程序参数，分配内存的静态方法。|  
|[allocator\_traits::construct 方法](../Topic/allocator_traits::construct%20Method.md)|使用的指定分配程序构造对象的静态方法。|  
|[allocator\_traits::deallocate 方法](../Topic/allocator_traits::deallocate%20Method.md)|使用的指定分配程序释放对象指定数量的静态方法。|  
|[allocator\_traits::destroy 方法](../Topic/allocator_traits::destroy%20Method.md)|使用的指定分配程序调用对象的析构函数，而不释放其内存的静态方法。|  
|[allocator\_traits::max\_size 方法](../Topic/allocator_traits::max_size%20Method.md)|使用的指定分配程序确定对象的最大数字可以赋予的静态方法。|  
|[allocator\_traits::select\_on\_container\_copy\_construction 方法](../Topic/allocator_traits::select_on_container_copy_construction%20Method.md)|调用指定的分布程序的 `select_on_container_copy_construction` 的静态方法。|  
  
## 要求  
 **页眉:** \<内存\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<memory\>](../standard-library/memory.md)   
 [pointer\_traits 结构](../standard-library/pointer-traits-struct.md)   
 [scoped\_allocator\_adaptor 类](../standard-library/scoped-allocator-adaptor-class.md)