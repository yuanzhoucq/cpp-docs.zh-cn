---
title: "&lt;allocators&gt; | Microsoft Docs"
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
  - "stdext::<allocators>"
  - "allocators/stdext::allocators"
  - "<allocators>"
  - "stdext.<allocators>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocators 标头"
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;allocators&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

帮助定义分配和释放。基于节点的容器存储区的多个模板。  
  
## 语法  
  
```  
#include <allocators>  
```  
  
## 备注  
 \<分配\> 程序标题提供用于选择基于节点的容器来管理策略的、指派程序模板。  对于使用这些模板的使用，还提供了多个同步不同的筛选器。管理策略专门适合各种不同的多线程方案 \(包括取消\)。  与内存管理策略设置为已知内存使用模式和要求，同步特定应用程序通常可以提高速度或缩小应用程序的总内存要求。  
  
 分配程序模板实现使用可自定义或替换提供的其他管理策略的可重用组件。  
  
 基于节点的容器中标准 C\+\+ 库 \(std::list、std::set、std::multiset、std::map 和 std::multimap\) 中存储这些文件在单独节点的元素。  特定容器类型的所有节点大小相同，因此，一般内存管理器的灵活性不是必需的。  由于每个存储区的大小在编译时已知，内存管理器可能更简单且更快。  
  
 如果使用未基于节点的容器 \(如标准 C\+\+ 库 std::vector 容器 std::deque 和 std::basic\_string\)，alllocator 模板将正常工作，但是，无法提供稍好默认分配程序的任何性能改进。  
  
 分配程序是描述一对象管理存储区分配和释放对象和数组的一个指定类型的对象的模板类。  若干容器模板类使用将程序对象在标准 C\+\+ 库中。  
  
 分配程序是此类型的模板：  
  
 `template<class`  `Type` `>`  
  
 `class allocator;`  
  
 如果模板参数 `Type` 是分配程序实例的托管类型。  标准 C\+\+ 库提供默认模板，在 [\<memory\>](../standard-library/memory.md)[allocator](../standard-library/allocator-class.md)分配程序，类定义。  \<分配\> 程序标题提供以下分配程序：  
  
-   [allocator\_newdel](../standard-library/allocator-newdel-class.md)  
  
-   [allocator\_unbounded](../standard-library/allocator-unbounded-class.md)  
  
-   [allocator\_fixed\_size](../standard-library/allocator-fixed-size-class.md)  
  
-   [allocator\_variable\_size](../standard-library/allocator-variable-size-class.md)  
  
-   [allocator\_suballoc](../standard-library/allocator-suballoc-class.md)  
  
-   [allocator\_chunklist](../standard-library/allocator-chunklist-class.md)  
  
 在创建容器，如以下代码示例时，请使用将程序中合适的实例化的第二个类型参数。  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`  
  
 \_List0 分配了 `allocator_chunklist` 和默认筛选器同步的节点。  
  
 除默认访问级别以外，使用宏 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 创建同步具有筛选器的分配器模板：  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`  
  
 `std::list<int, alloc<int> > _List1;`  
  
 \_Lst1 分配了 `allocator_chunklist` 和 [synchronization\_per\_thread](../standard-library/sync-per-thread-class.md) 同步筛选器的节点。  
  
 块分配程序是缓存或筛选器。  缓存是 std::size\_t 采用类型的参数的模板类。  它定义分配和释放一个范围的存储区分配块的一个程序。  使用 `new`运算符，则必须获得内存，但是，不需要调用另一个单独调用运算符 `new` 每个块。  可以，例如，从较大的块或缓存释放块的 Helper 后续重新发布的。  
  
 对于无法编译的编译器重新 std::size\_t 参数的值实例化是何时使用了模板参数\_Sz 的值传递到缓存的成员函数不绑定分配和解除分配。  
  
 \<分配\> 程序提供以下缓存模板：  
  
-   [cache\_freelist](../standard-library/cache-freelist-class.md)  
  
-   [cache\_suballoc](../standard-library/cache-suballoc-class.md)  
  
-   [cache\_chunklist](../standard-library/cache-chunklist-class.md)  
  
 筛选器是实现它的成员函数使用另一个块分配程序传递给它用作模板参数块分配程序。  筛选器最常见的形式是同步筛选器，将同步策略控制到另一个块分配程序实例的成员函数访问。\<分配\> 程序提供以下筛选器：同步  
  
-   [synchronization\_none](../standard-library/sync-none-class.md)  
  
-   [synchronization\_per\_container](../standard-library/sync-per-container-class.md)  
  
-   [synchronization\_per\_thread](../standard-library/sync-per-thread-class.md)  
  
-   [synchronization\_shared](../standard-library/sync-shared-class.md)  
  
 \<分配\> 程序也提供筛选器，[rts\_alloc](../standard-library/rts-alloc-class.md)容纳多个块分配程序实例并确定使用哪个实例对于分配或释放在运行时 \(而非编译时\)  它用于不能重新编译的编译器。  
  
 同步策略确定分配程序实例如何处理从多个线程并发分配和解除分配请求。  最简单的策略是直接传递所有请求传递给基础缓存对象，将同步到管理用户。  更复杂的策略是 mutex 可以使用序列化到基础缓存对象的访问。  
  
 如果编译器支持编译单线程和多线程应用，单线程应用程序的默认筛选器同步为 `sync_none`;对于其他所有情况是 `sync_shared`。  
  
 缓存模板 `cache_freelist` 采用确定在自由列表将存储元素的最大数字的最大类参数。  
  
 \<分配\> 程序提供以下最大类：  
  
-   [max\_none](../standard-library/max-none-class.md)  
  
-   [max\_unbounded](../standard-library/max-unbounded-class.md)  
  
-   [max\_fixed\_size](../standard-library/max-fixed-size-class.md)  
  
-   [max\_variable\_size](../standard-library/max-variable-size-class.md)  
  
### 宏  
  
|||  
|-|-|  
|[ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md)|为分布程序模板类。|  
|[CACHE\_CHUNKLIST](../Topic/CACHE_CHUNKLIST%20\(%3Callocators%3E\).md)|提供 `stdext::allocators::cache_chunklist<sizeof(Type)>`。|  
|[CACHE\_FREELIST](../Topic/CACHE_FREELIST%20\(%3Callocators%3E\).md)|提供 `stdext::allocators::cache_freelist<sizeof(Type), max>`。|  
|[CACHE\_SUBALLOC](../Topic/CACHE_SUBALLOC%20\(%3Callocators%3E\).md)|提供 `stdext::allocators::cache_suballoc<sizeof(Type)>`。|  
|[SYNC\_DEFAULT](../Topic/SYNC_DEFAULT%20\(%3Callocators%3E\).md)|给定同步筛选器。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Callocators%3E\).md)|测试指定类的分配器对象之间的不等性。|  
|[operator\=\=](../Topic/operator==%20\(%3Callocators%3E\).md)|测试指定类的分配器对象之间的相等性。|  
  
### 类  
  
|||  
|-|-|  
|[allocator\_base](../standard-library/allocator-base-class.md)|定义命令的基类\) 和常用函数创建从同步筛选器的一个用户定义的赋值程序。|  
|[allocator\_chunklist](../standard-library/allocator-chunklist-class.md)|描述管理存储区分配和释放对象使用的 [cache\_chunklist](../standard-library/cache-chunklist-class.md)一缓存类型的对象。|  
|[allocator\_fixed\_size](../standard-library/allocator-fixed-size-class.md)|描述管理存储区分配和释放 `Type` 类型的对象使用一个使用 [max\_fixed\_size](../standard-library/max-fixed-size-class.md)缓存管理的长度的 [cache\_freelist](../standard-library/cache-freelist-class.md) 类型的对象。|  
|[allocator\_newdel](../standard-library/allocator-newdel-class.md)|实现使用 `operator delete` 释放内存块和 `operator new` 分配存储区分配的一个程序。|  
|[allocator\_suballoc](../standard-library/allocator-suballoc-class.md)|描述管理存储区分配和释放 `Type` 类型的对象使用的缓存类型 [cache\_suballoc](../standard-library/cache-suballoc-class.md)的对象。|  
|[allocator\_unbounded](../standard-library/allocator-unbounded-class.md)|描述管理存储区分配和释放 `Type` 类型的对象使用一个使用 [max\_unbounded](../standard-library/max-unbounded-class.md)缓存管理的长度的 [cache\_freelist](../standard-library/cache-freelist-class.md) 类型的对象。|  
|[allocator\_variable\_size](../standard-library/allocator-variable-size-class.md)|描述管理存储区分配和释放 `Type` 类型的对象使用一个使用 [max\_variable\_size](../standard-library/max-variable-size-class.md)缓存管理的长度的 [cache\_freelist](../standard-library/cache-freelist-class.md) 类型的对象。|  
|[cache\_chunklist](../standard-library/cache-chunklist-class.md)|定义分配和释放一个范围的存储区分配块的一个程序。|  
|[cache\_freelist](../standard-library/cache-freelist-class.md)|定义分配和释放一个范围的存储区分配块的一个程序。|  
|[cache\_suballoc](../standard-library/cache-suballoc-class.md)|定义分配和释放一个范围的存储区分配块的一个程序。|  
|[freelist](../standard-library/freelist-class.md)|管理存储区的列表。|  
|[max\_fixed\_size](../standard-library/max-fixed-size-class.md)|描述一个类最大限制。对象固定的最大长度的 [freelist](../standard-library/freelist-class.md) 一个对象。|  
|[max\_none](../standard-library/max-none-class.md)|描述一类对象最大限制到一个最大长度的 [freelist](../standard-library/freelist-class.md) 对象零。|  
|[max\_unbounded](../standard-library/max-unbounded-class.md)|描述未限制 [freelist](../standard-library/freelist-class.md) 对象的最大长度的较大类对象。|  
|[max\_variable\_size](../standard-library/max-variable-size-class.md)|描述一个类最大限制大致为对象生成比例为分配的存储区域的数量最大长度的 [freelist](../standard-library/freelist-class.md) 一个对象。|  
|[rts\_alloc](../standard-library/rts-alloc-class.md)|保留缓存实例的 rts\_alloc 模板类描述 [筛选器](../standard-library/allocators-header.md) 并确定使用哪个实例用于分配和解除分配在运行时 \(而非编译时\)|  
|[synchronization\_none](../standard-library/sync-none-class.md)|描述未提供这样的同步筛选器。|  
|[synchronization\_per\_container](../standard-library/sync-per-container-class.md)|说明为每个分配程序对象提供单独缓存一个同步对象的筛选器。|  
|[synchronization\_per\_thread](../standard-library/sync-per-thread-class.md)|说明为每个线程提供一个单独的缓存对象的同步筛选器。|  
|[synchronization\_shared](../standard-library/sync-shared-class.md)|描述使用 mutex 控制到缓存对象的访问。所有分配程序共享的同步筛选器。|  
  
## 要求  
 **页眉：** \<分配程序\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)