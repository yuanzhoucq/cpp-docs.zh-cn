---
title: "condition_variable_any 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "condition_variable/std::condition_variable_any"
dev_langs: 
  - "C++"
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# condition_variable_any 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用类 `condition_variable_any` 等待有任何 `mutex` 类型的事件。  
  
## 语法  
  
```  
class condition_variable_any;  
```  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[condition\_variable\_any::condition\_variable\_any 构造函数](../Topic/condition_variable_any::condition_variable_any%20Constructor.md)|构造 `condition_variable_any` 对象。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[condition\_variable\_any::notify\_all 方法](../Topic/condition_variable_any::notify_all%20Method.md)|将等待 `condition_variable_any` 对象的所有线程解除阻塞。|  
|[condition\_variable\_any::notify\_one 方法](../Topic/condition_variable_any::notify_one%20Method.md)|将等待 `condition_variable_any` 对象的其中一个线程解除阻塞。|  
|[condition\_variable\_any::wait 方法](../Topic/condition_variable_any::wait%20Method.md)|阻塞线程。|  
|[condition\_variable\_any::wait\_for 方法](../Topic/condition_variable_any::wait_for%20Method.md)|阻塞线程，并在线程解除阻塞后设置一个时间间隔。|  
|[condition\_variable\_any::wait\_until 方法](../Topic/condition_variable_any::wait_until%20Method.md)|阻止线程，并设置线程解除的最大时间点。|  
  
## 要求  
 **Header:** condition\_variable  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<condition\_variable\>](../standard-library/condition-variable.md)