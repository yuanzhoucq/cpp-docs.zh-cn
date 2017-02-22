---
title: "improper_lock 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::improper_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_lock 类"
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# improper_lock 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

，当锁不正确时，获取描述异常引发此类。  
  
## 语法  
  
```  
class improper_lock : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[improper\_lock::improper\_lock 构造函数](../Topic/improper_lock::improper_lock%20Constructor.md)|已重载。  构造 `improper_lock exception`。|  
  
## 备注  
 通常，当尝试在相同上下文上递归获取非重入锁定时会引发该异常。  
  
## 继承层次结构  
 `exception`  
  
 `improper_lock`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [critical\_section 类](../../../parallel/concrt/reference/critical-section-class.md)   
 [reader\_writer\_lock 类](../../../parallel/concrt/reference/reader-writer-lock-class.md)