---
title: "allocator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::allocator"
  - "allocator"
  - "memory/std::allocator"
  - "std.allocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator 类"
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# allocator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述一个对象，用于管理 **Type** 类对象数组的存储分配和释放。 类 **allocator** 的对象是标准 C\+\+ 库中多个容器模板类的构造函数中指定的默认分配器对象。  
  
## 语法  
  
```  
  
template <class   
Type  
>  
class allocator  
  
```  
  
#### 参数  
 *类型*  
 为其分配或释放存储的对象的类型。  
  
## 备注  
 所有标准模板库容器都具有一个默认为 **allocator** 的模板参数。 通过使用自定义分配器构造容器可控制该容器的元素的分配和释放。  
  
 例如，分配器对象可能会在私有堆上或共享内存中分配存储，或者可能针对小型或大型对象大小进行优化。 它可能还会通过它提供的类型定义靠指定通过管理共享内存或执行自动垃圾回收的特殊访问器对象访问元素。 因此，使用分配器对象分配存储的类应使用这些类型来声明指针和引用对象，如同标准 C\+\+ 库中的容器一样。  
  
 **（仅限 C\_\+\+98\/03）**从 allocator 类派生时，必须提供 [rebind](../Topic/allocator::rebind.md) 结构，其 `_Other` typedef 引用新派生的类。  
  
 因此，分配器定义以下类型：  
  
-   [pointer](../Topic/allocator::pointer.md) 的行为类似指向 **Type** 的指针。  
  
-   [const\_pointer](../Topic/allocator::const_pointer.md) 的行为类似指向 **Type** 的常量指针。  
  
-   [reference](../Topic/allocator::reference.md) 的行为类似于对 **Type** 的引用。  
  
-   [const\_reference](../Topic/allocator::const_reference.md) 的行为类似于对 **Type** 的常量引用。  
  
 这些 **Type** 指定指针和引用必须对分配的元素采用的形式。 （对于所有分配器对象，[allocator::pointer](../Topic/allocator::pointer.md) 不一定与 **Type**\* 相同，即使它对于类 **allocator** 具有此明显定义。）  
  
 **C\+\+11 及更高版本：**若要在分配器中实现移动操作，请使用最小分配器接口并实现复制构造函数、\=\= 和 \!\= 运算符、分配和释放。 有关详细信息及示例，请参阅[分配器](../standard-library/allocators.md)  
  
## 成员  
  
### 构造函数  
  
|||  
|-|-|  
|[分配器](../Topic/allocator::allocator.md)|用于创建 `allocator` 对象的构造函数。|  
  
### Typedef  
  
|||  
|-|-|  
|[const\_pointer](../Topic/allocator::const_pointer.md)|提供指向由分配器管理的对象类型的常量指针的类型。|  
|[const\_reference](../Topic/allocator::const_reference.md)|提供对由分配器管理的对象类型的常量引用的类型。|  
|[difference\_type](../Topic/allocator::difference_type.md)|有符号的整型，可以表示指向由分配器管理的对象类型的指针值之间的差异。|  
|[指针](../Topic/allocator::pointer.md)|提供指向由分配器管理的对象类型的指针的类型。|  
|[reference](../Topic/allocator::reference.md)|提供指向对分配器管理的对象类型的引用的类型。|  
|[size\_type](../Topic/allocator::size_type.md)|无符号整型，可以表示模板类 `allocator` 的对象可以分配的任何序列的长度。|  
|[value\_type](../Topic/allocator::value_type.md)|由分配器管理的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[地址](../Topic/allocator::address.md)|查找指定了其值的对象的地址。|  
|[allocate](../Topic/allocator::allocate.md)|分配大小足以存储至少某个指定数量的元素的内存块。|  
|[构造](../Topic/allocator::construct.md)|在使用指定值初始化的指定地址处构造特定类型的对象。|  
|[释放](../Topic/allocator::deallocate.md)|从指定位置开始从存储中释放指定数量的的对象。|  
|[销毁](../Topic/allocator::destroy.md)|调用对象析构函数而不释放存储对象的内存。|  
|[max\_size](../Topic/allocator::max_size.md)|返回在可用内存用完之前，可以由类 `allocator` 的对象分配的类型 `Type` 的元素数。|  
|[重新绑定](../Topic/allocator::rebind.md)|实现分配器以便使一种类型的对象可以为另一种类型的对象分配存储的结构。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\=](../Topic/allocator::operator=.md)|将一个 `allocator` 对象分配给另一个 `allocator` 对象。|  
  
## 要求  
 **标头：**\<memory\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)