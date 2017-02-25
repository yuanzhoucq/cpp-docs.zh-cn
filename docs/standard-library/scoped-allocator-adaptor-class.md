---
title: "scoped_allocator_adaptor 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.scoped_allocator_adaptor"
  - "scoped_allocator_adaptor"
  - "scoped_allocator/std::scoped_allocator_adaptor"
  - "std::scoped_allocator_adaptor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scoped_allocator_adaptor 类"
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# scoped_allocator_adaptor 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示分配程序嵌套。  
  
## 语法  
  
```cpp  
template<class Outer, class... Inner>  
    class scoped_allocator_adaptor;  
```  
  
## 备注  
 模板类封装一个或多个分配程序嵌套。  此类具有每个 `outer_allocator_type`类型，`Outer`的同义词一个最外层的分配器，即 `scoped_allocator_adaptor` 对象的公共基。  使用`Outer` 容器将使用分配的内存。  您可以通过调用 `outer_allocator`获取对此分配程序基对象的引用。  
  
 嵌套的其余部分具有类型 `inner_allocator_type`。  一种内部分配程序用于将元素分配的内存在容器中。  您可以通过调用 `inner_allocator`获取对此类型存储的对象的引用。  如果 `Inner...` 不为空，`inner_allocator_type` 具有类型 `scoped_allocator_adaptor<Inner...>`，这样，`inner_allocator` 指定一个成员对象。  否则，`inner_allocator_type` 具有类型 `scoped_allocator_adaptor<Outer>`，这样，`inner_allocator` 指定整个对象。  
  
 嵌套的行为，就好像它具有任意深度，复制其最内层的封装的分配器。需要。  
  
 不可见接口来帮助部分介绍此模板类行为的几个概念。  一个 *最外层的分配器* 干预所有调用构造并销毁方法。  它是由 `OUTERMOST(X)`定义的，`OUTERMOST(X)` 是有效递归函数之一。  
  
-   如果 `X.outer_allocator()` 是" WellFormed "则 `OUTERMOST(X)` 为 `OUTERMOST(X.outer_allocator())`。  
  
-   否则，`OUTERMOST(X)` 为 `X`。  
  
 三种类型为博览会定义：  
  
|类型|说明|  
|--------|--------|  
|`Outermost`|`OUTERMOST(*this)` 的类型。|  
|`Outermost_traits`|`allocator_traits<Outermost>`|  
|`Outer_traits`|`allocator_traits<Outer>`|  
  
### 构造函数  
  
|Name|说明|  
|----------|--------|  
|[scoped\_allocator\_adaptor::scoped\_allocator\_adaptor 构造函数](../Topic/scoped_allocator_adaptor::scoped_allocator_adaptor%20Constructor.md)|构造 `scoped_allocator_adaptor` 对象。|  
  
### Typedef  
  
|Name|说明|  
|----------|--------|  
|`const_pointer`|此类型是的同义词程序与分配 `Outer``const_pointer`。|  
|`const_void_pointer`|此类型是的同义词程序与分配 `Outer``const_void_pointer`。|  
|`difference_type`|此类型是的同义词程序与分配 `Outer``difference_type`。|  
|`inner_allocator_type`|此类型是的同义词适配器嵌套的 `scoped_allocator_adaptor<Inner...>`的类型。|  
|`outer_allocator_type`|此类型是的同义词基本分配程序 `Outer`的类型。|  
|`pointer`|此类型是的同义词 `pointer` 与分配程序 `Outer`。|  
|`propagate_on_container_copy_assignment`|类型应用，只有当应用 `Outer_traits::propagate_on_container_copy_assignment` 或 `inner_allocator_type::propagate_on_container_copy_assignment` 应用。|  
|`propagate_on_container_move_assignment`|类型应用，只有当应用 `Outer_traits::propagate_on_container_move_assignment` 或 `inner_allocator_type::propagate_on_container_move_assignment` 应用。|  
|`propagate_on_container_swap`|类型应用，只有当应用 `Outer_traits::propagate_on_container_swap` 或 `inner_allocator_type::propagate_on_container_swap` 应用。|  
|`size_type`|此类型是的同义词 `size_type` 与分配程序 `Outer`。|  
|`value_type`|此类型是的同义词 `value_type` 与分配程序 `Outer`。|  
|`void_pointer`|此类型是的同义词 `void_pointer` 与分配程序 `Outer`。|  
  
### 结构  
  
|Name|说明|  
|----------|--------|  
|[scoped\_allocator\_adaptor::rebind 结构](../Topic/scoped_allocator_adaptor::rebind%20Struct.md)|定义类型 `Outer::rebind<Other>::other` 作为 `scoped_allocator_adaptor<Other, Inner...>`的同义词。|  
  
### 方法  
  
|Name|说明|  
|----------|--------|  
|[scoped\_allocator\_adaptor::allocate 方法](../Topic/scoped_allocator_adaptor::allocate%20Method.md)|使用 `Outer` 分配程序，分配内存。|  
|[scoped\_allocator\_adaptor::construct 方法](../Topic/scoped_allocator_adaptor::construct%20Method.md)|构造对象。|  
|[scoped\_allocator\_adaptor::deallocate 方法](../Topic/scoped_allocator_adaptor::deallocate%20Method.md)|使用 extern 分配器，释放对象。|  
|[scoped\_allocator\_adaptor::destroy 方法](../Topic/scoped_allocator_adaptor::destroy%20Method.md)|销毁一指定的对象。|  
|[scoped\_allocator\_adaptor::inner\_allocator 方法](../Topic/scoped_allocator_adaptor::inner_allocator%20Method.md)|检索对 `inner_allocator_type`类型的对象的引用。|  
|[scoped\_allocator\_adaptor::max\_size 方法](../Topic/scoped_allocator_adaptor::max_size%20Method.md)|确定可由分配外部程序分配的对象的最大数量。|  
|[scoped\_allocator\_adaptor::outer\_allocator 方法](../Topic/scoped_allocator_adaptor::outer_allocator%20Method.md)|检索对 `outer_allocator_type`类型的对象的引用。|  
|[scoped\_allocator\_adaptor::select\_on\_container\_copy\_construction 方法](../Topic/scoped_allocator_adaptor::select_on_container_copy_construction%20Method.md)|创建带有调用的初始化每个存储的分配器对象的新的 `scoped_allocator_adaptor` 对象对应的每个分配程序的 `select_on_container_copy_construction`。|  
  
## 要求  
 **页眉：** \<scoped\_allocator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)