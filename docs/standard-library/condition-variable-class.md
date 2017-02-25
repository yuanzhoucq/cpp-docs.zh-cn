---
title: "condition_variable 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "condition_variable/std::condition_variable"
dev_langs: 
  - "C++"
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# condition_variable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您具有类型 `unique_lock<mutex>`的`mutex`时，请使用 `condition_variable` 类等待事件。  此类型对象比 [condition\_variable\_any\<unique\_lock\<mutex\>\>](../standard-library/condition-variable-any-class.md)类型对象可以具有更好的性能。  
  
## 语法  
  
```  
class condition_variable;  
```  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[condition\_variable::condition\_variable 构造函数](../Topic/condition_variable::condition_variable%20Constructor.md)|构造 `condition_variable` 对象。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[condition\_variable::native\_handle 方法](../Topic/condition_variable::native_handle%20Method.md)|返回表示 condition\_variable图柄的implementation\-specific型。|  
|[condition\_variable::notify\_all 方法](../Topic/condition_variable::notify_all%20Method.md)|将等待 `condition_variable` 对象的所有线程解除阻塞。|  
|[condition\_variable::notify\_one 方法](../Topic/condition_variable::notify_one%20Method.md)|将等待 `condition_variable` 对象的其中一个线程解除阻塞。|  
|[condition\_variable::wait 方法](../Topic/condition_variable::wait%20Method.md)|阻塞线程。|  
|[condition\_variable::wait\_for 方法](../Topic/condition_variable::wait_for%20Method.md)|阻塞线程，并在线程解除阻塞后设置一个时间间隔。|  
|[condition\_variable::wait\_until 方法](../Topic/condition_variable::wait_until%20Method.md)|阻止线程，并设置线程解除的最大时间点。|  
  
## 要求  
 **Header:** condition\_variable  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<condition\_variable\>](../standard-library/condition-variable.md)