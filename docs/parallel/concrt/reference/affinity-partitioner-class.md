---
title: "affinity_partitioner 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppl/concurrency::affinity_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "affinity_partitioner 类"
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# affinity_partitioner 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`affinity_partitioner` 类类似于 `static_partitioner` 类，但是，它按映射 subranges 其选择提高缓存关联到辅助线程。  它可以显着提高性能，当循环重新实现在设置时的相同数据和数据放入缓存。  请注意必须使用同一 `affinity_partitioner` 对象与执行中的特定数据并行循环的后续迭代，受益于数据位置。  
  
## 语法  
  
```  
class affinity_partitioner;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[affinity\_partitioner::affinity\_partitioner 构造函数](../Topic/affinity_partitioner::affinity_partitioner%20Constructor.md)|构造 `affinity_partitioner` 对象。|  
|[affinity\_partitioner::~affinity\_partitioner 析构函数](../Topic/affinity_partitioner::~affinity_partitioner%20Destructor.md)|销毁一个 `affinity_partitioner` 对象。|  
  
## 继承层次结构  
 `affinity_partitioner`  
  
## 要求  
 **标头：**ppl.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)