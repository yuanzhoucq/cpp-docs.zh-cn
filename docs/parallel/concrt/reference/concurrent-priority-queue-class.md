---
title: "concurrent_priority_queue 类 | Microsoft Docs"
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
  - "concurrent_priority_queue/concurrency::concurrent_priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_priority_queue 类"
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
caps.latest.revision: 9
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# concurrent_priority_queue 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`concurrent_priority_queue` 类是允许多个线程同时推送和弹出项的容器 。  项目在用作模板参数，取决于功能符提供的优先级排序中弹出。  
  
## 语法  
  
```  
template <  
   typename _Ty,  
   typename _Compare=std::less<_Ty>,  
   typename _Ax = std::allocator<_Ty>  
>  
, typename _Ax = std::allocator<_Ty> > class concurrent_priority_queue;  
```  
  
#### 参数  
 `_Ty`  
 要存储在优先级队列中的元素的数据类型。  
  
 `_Compare`  
 提供函数对象，可以比较优先级队列中两个排序键以确定两个元素值的相对顺序。  该参数是可选的并且二元谓词 `less<``_Ty``>`为默认值。  
  
 `_Ax`  
 表示存储分配器对象的类型，该对象封装有关为并发优先级队列分配和解除分配内存的详细信息。  该参数是可选的并且默认值为 `allocator<``_Ty``>`。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`allocator_type`|表示适用于并发优先级队列的分配器类的类型。|  
|`const_reference`|表示对类型元素的常数引用的类型应在一种并发优先级队列中。|  
|`reference`|表示对类型元素的引用的类型应在一种并发优先级队列中。|  
|`size_type`|计算并发优先级队列中元素数量的类型。|  
|`value_type`|表示存储在并发优先级队列中的数据类型的类型。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[concurrent\_priority\_queue::concurrent\_priority\_queue 构造函数](../Topic/concurrent_priority_queue::concurrent_priority_queue%20Constructor.md)|已重载。  构造并发优先级队列。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[concurrent\_priority\_queue::clear 方法](../Topic/concurrent_priority_queue::clear%20Method.md)|清除并发优先级中的所有元素。  此方法不是并发安全方法。|  
|[concurrent\_priority\_queue::empty 方法](../Topic/concurrent_priority_queue::empty%20Method.md)|测试在调用此方法时并发主队列是否为空。  此方法是并发安全方法。|  
|[concurrent\_priority\_queue::get\_allocator 方法](../Topic/concurrent_priority_queue::get_allocator%20Method.md)|返回用于构造并发主队列的分配器副本。  此方法是并发安全方法。|  
|[concurrent\_priority\_queue::push 方法](../Topic/concurrent_priority_queue::push%20Method.md)|已重载。  添加元素到并发优先级队列。  此方法是并发安全方法。|  
|[concurrent\_priority\_queue::size 方法](../Topic/concurrent_priority_queue::size%20Method.md)|返回当前在队列中的元素数。  此方法是并发安全方法。|  
|[concurrent\_priority\_queue::swap 方法](../Topic/concurrent_priority_queue::swap%20Method.md)|交换两种并发优先队列内容。  此方法不是并发安全方法。|  
|[concurrent\_priority\_queue::try\_pop 方法](../Topic/concurrent_priority_queue::try_pop%20Method.md)|如果队列，非空，移除并从位于队列的优先级最高的元素。  此方法是并发安全方法。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[concurrent\_priority\_queue::operator\= 运算符](../Topic/concurrent_priority_queue::operator=%20Operator.md)|已重载。  将另一 `concurrent_priority_queue` 对象的内容分配到此对象中。  此方法不是并发安全方法。|  
  
## 备注  
 有关 `concurrent_priority_queue` 类的详细信息，请参见 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 继承层次结构  
 `concurrent_priority_queue`  
  
## 要求  
 **头文件：**concurrent\_priority\_queue.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)