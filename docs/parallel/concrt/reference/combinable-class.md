---
title: "combinable 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppl/concurrency::combinable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "combinable 类"
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# combinable 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`combinable<T>` 对象旨在提供数据的线程私有副本，以在并行算法期间执行无锁线程本地子计算。  在并行操作结束时，线程私有 sub\-computation 则可以合并到最终结果。  该类可替代共享变量使用，如果在该共享变量上可能存在大量争用，则可能会使性能提高。  
  
## 语法  
  
```  
template<  
   typename _Ty  
>  
class combinable;  
```  
  
#### 参数  
 `_Ty`  
 最终合并的结果的数据类型。  类型必须具有复制构造函数和默认构造函数。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[combinable::combinable 构造函数](../Topic/combinable::combinable%20Constructor.md)|已重载。  构造新的 `combinable` 对象。|  
|[combinable::~combinable 析构函数](../Topic/combinable::~combinable%20Destructor.md)|销毁 `combinable` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[combinable::clear 方法](../Topic/combinable::clear%20Method.md)|清除先前用法中的所有中间计算结果。|  
|[combinable::combine 方法](../Topic/combinable::combine%20Method.md)|通过调用提供的 combine 仿函数从本地线程子计算的集合中计算生成最终值。|  
|[combinable::combine\_each 方法](../Topic/combinable::combine_each%20Method.md)|通过调用为每个线程本地 sub\-computation 提供 combine 仿函根据线程本地 sub\-computations 集计算最终值。  最终结果由函数对象累积。|  
|[combinable::local 方法](../Topic/combinable::local%20Method.md)|已重载。  返回对线程私有子计算的引用。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[combinable::operator\= 运算符](../Topic/combinable::operator=%20Operator.md)|从另一 `combinable` 对象分配到 `combinable` 对象。|  
  
## 备注  
 有关更多信息，请参见 [并行容器和对象](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 继承层次结构  
 `combinable`  
  
## 要求  
 **标头：**ppl.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)