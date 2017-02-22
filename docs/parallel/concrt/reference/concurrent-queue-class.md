---
title: "concurrent_queue 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concurrent_queue/concurrency::concurrent_queue"
  - "concurrent_queue/Concurrency::concurrent_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_queue 类"
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# concurrent_queue 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`concurrent_queue` 类是允许对其元素进行先进先出访问的序列容器类。  它允许组有限并发安全操作，例如 `push` 和 `try_pop`。  
  
## 语法  
  
```  
template<  
   typename _Ty,  
   class _Ax  
>  
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;  
```  
  
#### 参数  
 `_Ty`  
 要存储在队列中的元素的数据类型。  
  
 `_Ax`  
 表示存储分配器对象的类型，该对象封装有关为该并发队列分配和解除分配内存的详细信息。  该参数是可选的并且默认值为 `allocator<``_Ty``>`。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|`allocator_type`|表示适用于并发队列的分配器类的类型。|  
|`const_iterator`|表示并发队列中的元素上的非线程安全 `const` 迭代器的类型。|  
|`const_reference`|提供对存储在并发队列中的 `const` 元素的引用从而读取和执行 `const` 操作的类型。|  
|`difference_type`|提供并发队列中两个元素之间符号距离的类型。|  
|`iterator`|表示并发队列中的元素上的非线程安全迭代器的类型。|  
|`reference`|提供对存储在并发队列中的元素的引用的类型。|  
|`size_type`|计算并发队列中元素数量的类型。|  
|`value_type`|表示存储在并发队列中的数据类型的类型。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[concurrent\_queue::concurrent\_queue 构造函数](../Topic/concurrent_queue::concurrent_queue%20Constructor.md)|已重载。  构造并发队列。|  
|[concurrent\_queue::~concurrent\_queue 析构函数](../Topic/concurrent_queue::~concurrent_queue%20Destructor.md)|销毁并发队列。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[concurrent\_queue::clear 方法](../Topic/concurrent_queue::clear%20Method.md)|清除并发队列，销毁所有当前已排入队列的元素。  此方法不是并发安全方法。|  
|[concurrent\_queue::empty 方法](../Topic/concurrent_queue::empty%20Method.md)|测试在调用此方法时并发队列是否为空。  此方法是并发安全方法。|  
|[concurrent\_queue::get\_allocator 方法](../Topic/concurrent_queue::get_allocator%20Method.md)|返回用于构造并发队列的分配器副本。  此方法是并发安全方法。|  
|[concurrent\_queue::push 方法](../Topic/concurrent_queue::push%20Method.md)|已重载。  将项排入到并发队列的结尾处。  此方法是并发安全方法。|  
|[concurrent\_queue::try\_pop 方法](../Topic/concurrent_queue::try_pop%20Method.md)|如果存在项，从队列中取消排队项目。  此方法是并发安全方法。|  
|[concurrent\_queue::unsafe\_begin 方法](../Topic/concurrent_queue::unsafe_begin%20Method.md)|已重载。  返回指向并发队列开头的类型 `iterator` 或 `const_iterator` 的迭代器。  此方法不是并发安全方法。|  
|[concurrent\_queue::unsafe\_end 方法](../Topic/concurrent_queue::unsafe_end%20Method.md)|已重载。  返回指向并发队列末尾的类型 `iterator` 或 `const_iterator` 的迭代器。  此方法不是并发安全方法。|  
|[concurrent\_queue::unsafe\_size 方法](../Topic/concurrent_queue::unsafe_size%20Method.md)|返回队列中的项数。  此方法不是并发安全方法。|  
  
## 备注  
 有关更多信息，请参见 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 继承层次结构  
 `concurrent_queue`  
  
## 要求  
 **标头：**concurrent\_queue.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)