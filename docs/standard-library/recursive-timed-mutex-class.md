---
title: "recursive_timed_mutex 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mutex/std::recursive_timed_mutex"
dev_langs: 
  - "C++"
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# recursive_timed_mutex 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示一个 *mutex 计时类型*。  使用程序内的，该对象用于锁定时间限制类型强制互斥。  与不同类型 [timed\_mutex](../standard-library/timed-mutex-class.md)对象，调用 `recursive_timed_mutex` 对象的锁的方法的效果是显式定义的。  
  
## 语法  
  
```  
class recursive_timed_mutex;  
```  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[recursive\_timed\_mutex::recursive\_timed\_mutex 构造函数](../Topic/recursive_timed_mutex::recursive_timed_mutex%20Constructor.md)|构造尚未锁定的 `recursive_timed_mutex` 对象。|  
|[recursive\_timed\_mutex::~recursive\_timed\_mutex 析构函数](../Topic/recursive_timed_mutex::~recursive_timed_mutex%20Destructor.md)|释放 `recursive_timed_mutex` 对象使用的所有资源。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[recursive\_timed\_mutex::lock 方法](../Topic/recursive_timed_mutex::lock%20Method.md)|阻止调用线程，直到线程获取 `mutex` 的所有权。|  
|[recursive\_timed\_mutex::try\_lock 方法](../Topic/recursive_timed_mutex::try_lock%20Method.md)|在不阻止的情况下尝试获取 `mutex` 的所有权。|  
|[recursive\_timed\_mutex::try\_lock\_for 方法](../Topic/recursive_timed_mutex::try_lock_for%20Method.md)|尝试获取 `mutex` 的所有权指定时间间隔的。|  
|[recursive\_timed\_mutex::try\_lock\_until 方法](../Topic/recursive_timed_mutex::try_lock_until%20Method.md)|尝试获取 `mutex` 的所有权直到指定的时间。|  
|[recursive\_timed\_mutex::unlock 方法](../Topic/recursive_timed_mutex::unlock%20Method.md)|释放 `mutex` 的所有权。|  
  
## 要求  
 **标头:** mutex  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)