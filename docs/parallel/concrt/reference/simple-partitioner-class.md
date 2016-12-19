---
title: "simple_partitioner 类 | Microsoft Docs"
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
  - "ppl/concurrency::simple_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "simple_partitioner 类"
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
caps.latest.revision: 8
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# simple_partitioner 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`simple_partitioner` 类表示 `parallel_for`重复的静态分区该范围。  分区程序将此范围转换为区块这样每个区块具有块范围指定迭代的至少数。  
  
## 语法  
  
```  
class simple_partitioner;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[simple\_partitioner::simple\_partitioner 构造函数](../Topic/simple_partitioner::simple_partitioner%20Constructor.md)|构造 `simple_partitioner` 对象。|  
|[simple\_partitioner::~simple\_partitioner 析构函数](../Topic/simple_partitioner::~simple_partitioner%20Destructor.md)|销毁 `simple_partitioner` 对象。|  
  
## 继承层次结构  
 `simple_partitioner`  
  
## 要求  
 **标头：**ppl.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)