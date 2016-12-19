---
title: "&lt;condition_variable&gt; | Microsoft Docs"
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
  - "<condition_variable>"
dev_langs: 
  - "C++"
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;condition_variable&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义用于创建对象等待条件变为 true 类和 [condition\_variable](../standard-library/condition-variable-class.md)[condition\_variable\_any](../standard-library/condition-variable-any-class.md)。  
  
 此标头使用并发运行时 \(ConcRT\)，以便可以与其他 ConcRT framework 一起使用它。  有关ConcRT的详细信息，请参阅[并发运行时](../parallel/concrt/concurrency-runtime.md)。  
  
## 语法  
  
```cpp  
#include <condition_variable>  
```  
  
> [!NOTE]
>  在代码中使用 **\/clr**或者**\/clr:pure**来编译,标头是被锁定的。  
  
### 备注  
 等待变量代码情况还必须使用 `mutex`。  对的调用的线程必须锁定 `mutex`，然后再调用情况等待变量的函数。  当调用函数返回时，`mutex` 将阻塞。  当线程等待条件变为 true 时，`mutex` 不锁定。  不可预知的结果，因而不等待环境变量的每个线程都必须使用同一 `mutex` 对象。  
  
 类型 `condition_variable_any` 对象可用于任何类型 mutex。  mutex 使用的类型不必须提供 `try_lock` 方法。  类型 `condition_variable` 对象只能与 `unique_lock<mutex>`类型 mutex。  此类型对象比类型 `condition_variable_any<unique_lock<mutex>>`对象可能快。  
  
 要等到事件，请先锁定 mutex，然后调用一在条件变量的 `wait` 方法。  直到另一个线程中调用 `wait` 块终止条件变量。  
  
 *"虚拟"唤醒* 发生情况，当等待变量的线程已取消，而没有相应的通知。  若要识别此"虚拟"唤醒，则条件变为 true 的代码应显式检查条件，如果代码从等待功能时返回。  使用循环，这通常执行；可以使用 `wait(unique_lock<mutex>& lock, Predicate pred)` 为您执行此循环。  
  
```cpp  
while (condition is false)  
    wait for condition variable;  
```  
  
 `condition_variable_any` 和 `condition_variable` 类有等待环境的三种方法。  
  
-   `wait` 等待无限的时间段。  
  
-   直到指定 `time`的`wait_until`。  
  
-   等待指定`wait_for` 的 `time interval`。  
  
 这些方法中的每一个都具有两个重载版本。  一个等待并能抵御伪造地醒。  其他都采用定义某一谓词的其他模板参数。  方法不返回，直到谓词变为 `true`。  
  
 每个类也拥有用于通知条件变量的两个方法其条件是 `true`。  
  
-   `notify_one` 叫醒等待环境变量的一个线程。  
  
-   `notify_all` 叫醒等待环境变量的所有线程。  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [condition\_variable 类](../standard-library/condition-variable-class.md)   
 [condition\_variable\_any 类](../standard-library/condition-variable-any-class.md)   
 [cv\_status 枚举](../Topic/cv_status%20Enumeration.md)