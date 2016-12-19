---
title: "unique_ptr 类 | Microsoft Docs"
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
  - "unique_ptr"
  - "std.unique_ptr"
  - "std::unique_ptr"
  - "memory/std::unique_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unique_ptr 类"
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
caps.latest.revision: 22
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unique_ptr 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存储指向拥有的对象或数组的指针。  此对象\/数组仅由 `unique_ptr` 拥有。  `unique_ptr` 被销毁后，此对象\/数组也将被销毁。  
  
## 语法  
  
```  
template< class T, class Del = default_delete<T> >  
    class unique_ptr {  
public:  
    unique_ptr( );  
    unique_ptr( nullptr_t Nptr );  
    explicit unique_ptr( pointer Ptr );  
    unique_ptr( pointer Ptr,  
        typename conditional<is_reference<Del>::value,   
            Del,  
            typename add_reference<const Del>::type>::type Deleter);  
    unique_ptr (pointer Ptr,  
        typename remove_reference<Del>::type&& Deleter);  
    unique_ptr (unique_ptr&& Right);  
    template<class T2, Class Del2> unique_ptr( unique_ptr<T2, Del2>&& Right );  
    unique_ptr( const unique_ptr& Right    ) = delete;  
    unique_ptr& operator=(const unique_ptr& Right     ) = delete;  
};  
  
```  
  
```  
//Specialization for arrays:  
template <class T, class D> class unique_ptr<T[], D>   
{   public:       
     typedef pointer;  
     typedef T element_type;  
     typedef D deleter_type;  
  
     constexpr unique_ptr() noexcept;  
     template <class U> explicit unique_ptr(U p) noexcept;  
     template <class U> unique_ptr(U p, see below d) noexcept;  
     template <class U> unique_ptr(U p, see below d) noexcept;  
     unique_ptr(unique_ptr&& u) noexcept;  
     constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }  
     template <class U, class E>  
       unique_ptr(unique_ptr<U, E>&& u) noexcept;  
  
     ~unique_ptr();  
  
     unique_ptr& operator=(unique_ptr&& u) noexcept;  
     template <class U, class E>  
       unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;  
     unique_ptr& operator=(nullptr_t) noexcept;  
  
     T& operator[](size_t i) const;  
     pointer get() const noexcept;  
     deleter_type& get_deleter() noexcept;  
     const deleter_type& get_deleter() const noexcept;  
     explicit operator bool() const noexcept;  
  
     pointer release() noexcept;  
     void reset(pointer p = pointer()) noexcept;  
     void reset(nullptr_t = nullptr) noexcept;  
     template <class U> void reset(U p) noexcept = delete;  
     void swap(unique_ptr& u) noexcept;  
  
    // disable copy from lvalue  
     unique_ptr(const unique_ptr&) = delete;  
     unique_ptr& operator=(const unique_ptr&) = delete;  
   };  
 }  
  
```  
  
#### 参数  
 `Right`  
 `unique_ptr`。  
  
 `Nptr`  
 类型为 `rvalue` 的 `std::nullptr_t`。  
  
 `Ptr`  
 `pointer`。  
  
 `Deleter`  
 绑定到 `deleter` 的 `unique_ptr` 函数。  
  
## 异常  
 `unique_ptr` 不生成异常。  
  
## 备注  
 `unique_ptr` 类取代 `auto_ptr`，并可用作 STL 容器的元素。  
  
 使用 [make\_unique](../Topic/make_unique.md) Helper 函数可高效创建 `unique_ptr` 的新实例。  
  
 `unique_ptr` 唯一管理资源。  每个 `unique_ptr` 对象均存储一个指向其拥有的对象的指针，或存储一个 null 指针。  资源仅可由最多一个 `unique_ptr` 对象拥有；  当拥有特定资源的 `unique_ptr` 对象被销毁后，资源将释放。  可以移动 `unique_ptr` 对象，但不能复制它；  有关详细信息，请参阅[规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 资源通过调用 `deleter` 类型的已存储 `Del` 对象来释放，此对象知道如何为特定 `unique_ptr` 分配资源。  默认 `deleter` `default_delete``<T>` 假定 `_Ptr` 指向的资源通过 `new` 分配，并且此资源可通过调用 `delete _``Ptr` 释放。  （部分专用化 `unique_ptr<T[]>` 管理通过 `new[]` 分配的数组对象，并具有经过专用化以调用 delete\[\] `deleter` 的默认 `default_delete<T[]>` `_Ptr`。）  
  
 指向拥有的资源的存储指针 `stored_ptr` 具有类型 `pointer`。  如果已定义，此为 `Del::pointer`，如果未定义，则为 `T *` 。  如果 `deleter` 无状态，则存储的 `stored_deleter` 对象 `deleter` 不占用任何空间。  请注意，`Del` 可以为引用类型。  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[unique\_ptr::unique\_ptr](../Topic/unique_ptr::unique_ptr.md)|`unique_ptr` 有七个构造函数。|  
  
### Typedef  
  
|||  
|-|-|  
|[deleter\_type](../Topic/deleter_type.md)|模板参数 `Del` 的同义词。|  
|[element\_type](../Topic/element_type.md)|模板参数 `T``.` 的同义词。|  
|[指针](../Topic/pointer.md)|如果已定义，为 `Del::pointer` 的同义词，否则为 `T *` 的同义词。|  
  
### 成员函数  
  
|||  
|-|-|  
|[unique\_ptr::get](../Topic/unique_ptr::get.md)|返回 `stored_ptr`。|  
|[unique\_ptr::get\_deleter](../Topic/unique_ptr::get_deleter.md)|返回对 `stored_deleter` 的引用。|  
|[unique\_ptr::release](../Topic/unique_ptr::release.md)|将 `pointer()` 存储在 `stored_ptr` 中并返回其先前内容。|  
|[unique\_ptr::reset](../Topic/unique_ptr::reset.md)|释放当前拥有的资源并接受新资源。|  
|[unique\_ptr::swap](../Topic/unique_ptr::swap.md)|使用提供的 `deleter` 交换资源和 `unique_ptr`。|  
  
### 运算符  
  
|||  
|-|-|  
|`operator bool`|此运算符返回可转换为 `bool` 的类型的值。  当 `bool` 时，转换为 `true` 的结果为 `get() != pointer()`，否则为 `false`。|  
|`operator->`|此成员函数返回 `stored_ptr``.`。|  
|`operator*`|此成员函数返回 \*`stored_ptr``.`。|  
|[unique\_ptr operator\=](../Topic/unique_ptr%20operator=.md)|将 `unique_ptr` （或 `pointer-type`）的值赋给当前 `unique_ptr`。|  
  
## 要求  
 **标头：**\<memory\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<memory\>](../standard-library/memory.md)