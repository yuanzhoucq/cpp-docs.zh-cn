---
title: "auto_partitioner 类 | Microsoft Docs"
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
  - "ppl/concurrency::auto_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_partitioner 类"
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
caps.latest.revision: 8
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_partitioner 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`auto_partitioner` 类表示默认方法 `parallel_for`、 `parallel_for_each` 和 `parallel_transform` 使用进行分区它们重复的大小。  分区窃取为负载平衡的 employes 范围此方法以及每次重复取消。  
  
## 语法  
  
```  
class auto_partitioner;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[auto\_partitioner::auto\_partitioner 构造函数](../Topic/auto_partitioner::auto_partitioner%20Constructor.md)|构造 `auto_partitioner` 对象。|  
|[auto\_partitioner::~auto\_partitioner 析构函数](../Topic/auto_partitioner::~auto_partitioner%20Destructor.md)|销毁 `auto_partitioner` 对象。|  
  
## 继承层次结构  
 `auto_partitioner`  
  
## 要求  
 **标头：**ppl.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)