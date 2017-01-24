---
title: "thread 类 | Microsoft Docs"
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
  - "thread/std::thread"
dev_langs: 
  - "C++"
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
caps.latest.revision: 16
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# thread 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义一个用于观察和管理在应用程序中执行线程的对象。  
  
## 语法  
  
```  
class thread;  
```  
  
## 备注  
 你可以使用 `thread` 对象来观察和管理在应用程序中的执行线程。  使用默认的构造函数创建的线程对象不与任何可执行线程关联。  通过使用一个可调用对象的线程对象创建一个执行线程，并在该线程对象中调用这个可调用对象。  线程对象可以被移动，但不能被复制。  因此，一个执行线程只能与一个线程对象关联。  
  
 每个可执行线程都具有唯一 `thread::id`标识符。  函数 `this_thread::get_id` 返回调用线程的标识符。  成员函数 `thread::get_id` 返回可由线程对象管理的线程的标识符。  对于默认构造函数创建的线程对象，`thread::get_id` 方法返回一个对象，该对象具有和所有默认构造函数线程对象相同的值，但 `this_thread::get_id` 方法返回在调用时可以加入的任何执行线程的值是不同的。  
  
## 成员  
  
### 公共类  
  
|Name|说明|  
|----------|--------|  
|[thread::id 类](../Topic/thread::id%20Class.md)|唯一标识相关线程。|  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[thread::thread 构造函数](../Topic/thread::thread%20Constructor.md)|构造 `thread` 对象。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[thread::detach 方法](../Topic/thread::detach%20Method.md)|分离 `thread` 对象关联的线程。|  
|[thread::get\_id 方法](../Topic/thread::get_id%20Method.md)|返回关联线程的唯一标识符。|  
|[thread::hardware\_concurrency 方法](../Topic/thread::hardware_concurrency%20Method.md)|静态的。  返回硬件线程上下文的数目的估计值。|  
|[thread::join 方法](../Topic/thread::join%20Method.md)|阻塞，直到关联的线程完成。|  
|[thread::joinable 方法](../Topic/thread::joinable%20Method.md)|指定关联的线程是否可连接。|  
|[thread::native\_handle 方法](../Topic/thread::native_handle%20Method.md)|返回表示线程句柄的特殊类型的实现。|  
|[thread::swap 方法](../Topic/thread::swap%20Method.md)|交换与指定的 `thread` 对象的状态。|  
  
### 公共运算符  
  
|Name|说明|  
|----------|--------|  
|[thread::operator\= 运算符](../Topic/thread::operator=%20Operator.md)|关联与当前 `thread` 对象的线程。|  
  
## 要求  
 **标头:** 线程  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<thread\>](../standard-library/thread.md)