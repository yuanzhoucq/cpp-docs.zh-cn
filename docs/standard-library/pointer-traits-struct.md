---
title: "pointer_traits 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::pointer_traits::element_type"
  - "memory/std::pointer_traits::pointer"
  - "memory/std::pointer_traits"
  - "memory/std::pointer_traits::difference_type"
  - "memory/std::pointer_traits::rebind"
  - "xmemory0/std::pointer_traits::element_type"
  - "xmemory0/std::pointer_traits::pointer"
  - "xmemory0/std::pointer_traits"
  - "xmemory0/std::pointer_traits::difference_type"
  - "xmemory0/std::pointer_traits::rebind"
dev_langs: 
  - "C++"
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
caps.latest.revision: 13
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pointer_traits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供模板类 `allocator_traits` 对象所需的用于通过指针类型 `Ptr` 描述分配器的信息。  
  
## 语法  
  
```cpp  
template<class Ptr>  
    struct pointer_traits;  
```  
  
## 备注  
 Ptr 可以是类型 `Ty *` 或具有以下属性的类到原始的指针。  
  
```  
template<class Ty, class... Rest>  
    struct Ptr  
    { // describes a pointer type usable by allocators  
    typedef Ptr pointer;  
    typedef T1 element_type; // optional  
    typedef T2 difference_type; // optional  
    template<class Other>  
        using rebind = typename Ptr<Other, Rest...>; // optional  
  
    static pointer pointer_to(element_type& obj); // optional  
    };  
```  
  
> [!WARNING]
>  在 C\+\+ 标准指定 `rebind` 模板成员用作别名时，Visual C\+\+ 实现重新为 `struct`。  
  
### Typedef  
  
|Name|说明|  
|----------|--------|  
|`typedef T2 difference_type`|类型 `T2` 是 `Ptr::difference_type`，如果该类型存在，则为 `ptrdiff_t`。  如果 `Ptr` 的原始指针，是一个类型为 `ptrdiff_t`。|  
|`typedef T1 element_type`|类型 `T1` 是 `Ptr::element_type`，如果该类型存在，则为 `Ty`。  如果 `Ptr` 的原始指针，是一个类型为 `Ty`。|  
|`typedef Ptr pointer`|类型为 `Ptr`。|  
  
### 结构  
  
|Name|说明|  
|----------|--------|  
|`pointer_traits::rebind`|基础类型指针尝试转换为指定类型。|  
  
### 方法  
  
|Name|说明|  
|----------|--------|  
|[pointer\_traits::pointer\_to 方法](../Topic/pointer_traits::pointer_to%20Method.md)|转换为 `Ptr`类的对象的任何引用。|  
  
## 要求  
 **页眉:** \<内存\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<memory\>](../standard-library/memory.md)   
 [allocator\_traits 类](../standard-library/allocator-traits-class.md)