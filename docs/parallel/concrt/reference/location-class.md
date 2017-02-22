---
title: "location 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::location"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "location 类"
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# location 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

硬件的抽象物理位置。  
  
## 语法  
  
```  
class location;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[location::location 构造函数](../Topic/location::location%20Constructor.md)|已重载。  构造 `location` 对象。|  
|[location::~location 析构函数](../Topic/location::~location%20Destructor.md)|销毁 `location` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[location::current 方法](../Topic/location::current%20Method.md)|返回表示调用线程执行的最具体的位置的 `location` 对象。|  
|[location::from\_numa\_node 方法](../Topic/location::from_numa_node%20Method.md)|返回表示特定 NUMA 节点的 `location` 对象。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[location::operator\!\= 运算符](../Topic/location::operator!=%20Operator.md)|确定两个 `location` 对象是否表示不同的位置。|  
|[location::operator\= 运算符](../Topic/location::operator=%20Operator.md)|将另一 `location` 对象的内容分配到此对象中。|  
|[location::operator\=\= 运算符](../Topic/location::operator==%20Operator.md)|确定两个 `location` 对象是否表示相同的位置。|  
  
## 继承层次结构  
 `location`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)