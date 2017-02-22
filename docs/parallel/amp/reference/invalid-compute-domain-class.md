---
title: "invalid_compute_domain 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::invalid_compute_domain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_compute_domain 类"
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# invalid_compute_domain 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

当运行时无法通过使用在  [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md)调用站点处指定的计算域启动内核时，将引发的异常。  
  
## 语法  
  
```  
class invalid_compute_domain : public runtime_exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[invalid\_compute\_domain::invalid\_compute\_domain 构造函数](../Topic/invalid_compute_domain::invalid_compute_domain%20Constructor.md)|初始化 `invalid_compute_domain` 类的新实例。|  
  
## 继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `invalid_compute_domain`  
  
## 要求  
 **标头：**amprt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)