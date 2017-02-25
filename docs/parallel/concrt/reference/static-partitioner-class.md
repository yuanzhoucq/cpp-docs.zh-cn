---
title: "static_partitioner 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppl/concurrency::static_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "static_partitioner 类"
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# static_partitioner 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`static_partitioner` 类表示 `parallel_for`重复的静态分区该范围。  ，尽管具有辅助可用于该 underyling 的计划程序，分区程序将此范围转换为许多区块。  
  
## 语法  
  
```  
class static_partitioner;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[static\_partitioner::static\_partitioner 构造函数](../Topic/static_partitioner::static_partitioner%20Constructor.md)|构造 `static_partitioner` 对象。|  
|[static\_partitioner::~static\_partitioner 析构函数](../Topic/static_partitioner::~static_partitioner%20Destructor.md)|销毁 `static_partitioner` 对象。|  
  
## 继承层次结构  
 `static_partitioner`  
  
## 要求  
 **标头：**ppl.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)