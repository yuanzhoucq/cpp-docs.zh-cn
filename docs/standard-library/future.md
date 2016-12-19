---
title: "&lt;future&gt; | Microsoft Docs"
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
  - "<future>"
dev_langs: 
  - "C++"
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;future&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含标准标头\<future\> 来定义能够简化运行函数的模版类和支持模版—可能分离线程—并且复查结果。  结果为任何函数或异常由函数返回发出的值，但没有捕获在函数。  
  
 此标头使用并发运行时 \(ConcRT\)，以便可以与其他 ConcRT framework 一起使用它。  有关ConcRT的详细信息，请参阅[并发运行时](../parallel/concrt/concurrency-runtime.md)。  
  
## 语法  
  
```cpp  
#include <future>  
```  
  
## 备注  
  
> [!NOTE]
>  在代码中使用 **\/clr**或者**\/clr:pure**来编译,标头是被锁定的。  
  
 *异步提供程序*存储了函数调用的结果。  *异步返回对象*用来取回函数调用的结果。   *联系异步状态*提供了异步提供程序和更多返回的异步对象之间的交流。  
  
 程序不直接创建任何关联的异步状态对象。  程序创建一个异步提供程序，每当控件需要一个，并从已经创建异步返回对象与提供程序共享其关联的异步状态。  异步提供程序和异步返回对象管理保存这些共享关联的异步状态的对象。  当引用关联的异步状态释放它，该元素包含该关联的异步状态的对象销毁的最后一个对象。  
  
 只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会是 *ready*。  
  
 只有当其异步提供程序存储了返回值或存储了异常时，关联的异步状态才会是 *ready*。  
  
 模版函数`async` 和模版类`promise`和`packaged_task`是异步程序提供者。  模板类`future`和 `shared_future` 描述了异步返回对象。  
  
 每一个模版类`promise`, `future`,和`shared_future` has a specialization for the type 有特定的类型`void`并且通过引用为存储和检索部分值。  这些专用化与母版仅针对模板不同于存储和检索返回值的函数的签名和语义。  
  
 模版类 `future` 和`shared_future`从来不在各自的析构函数中上锁，除非为了保持向后兼容：与其他futures不同的是，对于`future`—或者最后的`shared_future`—这是由`std::async`开始的任务，假如任务没有完成那么析构函数便会上锁；也是就是假如线程仍没有`.get()`或 `.wait()` 并且任务依旧运行，那么便会上锁。  在最初的版本标准中，以下的可用性没有被增加到`std::async`的描述中：“\[注意：假如future从std::async从本地范围中移除，其他使用future的代码必须注意到析构函数可能会锁起对于共享的状态。—结束注意\]"其它的例子，`future`和`shared_future`析构函数是必要的并且保证从不上锁。  
  
## 成员  
  
### 类  
  
|Name|说明|  
|----------|--------|  
|[future 类](../standard-library/future-class.md)|描述异步返回对象。|  
|[future\_error 类](../standard-library/future-error-class.md)|描述一个能够管理`future`对象并且能够由类型方法抛出的异常对象。|  
|[packaged\_task 类](../standard-library/packaged-task-class.md)|描述异步程序提供者是一个调用包装器并且调用签名为 `Ty(ArgTypes...)`。  除了予考虑结果之外，其关联的异步状态保留其可调用对象的副本。|  
|[promise 类](../standard-library/promise-class.md)|描述一个异步提供程序。|  
|[shared\_future 类](../standard-library/shared-future-class.md)|描述异步返回对象。  与`future` 对象对比，一个异步程序提供者能够与任何`shared_future` 对象相联系。|  
  
### 结构  
  
|Name|说明|  
|----------|--------|  
|[is\_error\_code\_enum 结构](../standard-library/is-error-code-enum-structure.md)|专业化表明了`future_errc`是合适存储`error_code`。|  
|[uses\_allocator 结构](../standard-library/uses-allocator-structure.md)|专用化总是真的。|  
  
### 函数  
  
|Name|说明|  
|----------|--------|  
|[async 函数](../Topic/async%20Function.md)|表示一个异步提供程序.|  
|[future\_category 函数](../Topic/future_category%20Function.md)|返回`error_category`对象的引用错误的特征与`future`对象相联系。|  
|[make\_error\_code 函数](../Topic/make_error_code%20Function.md)|创建`error_code`有描述 `future` 错误的`error_category` 对象。|  
|[make\_error\_condition 函数](../Topic/make_error_condition%20Function.md)|创建`error_condition`有描述 `future` 错误的`error_category` 对象。|  
|[swap 函数 \(\<future\>\)](../Topic/swap%20Function%20\(%3Cfuture%3E\).md)|如果对象有关联的异步状态，则为 `promise`；否则为 。|  
  
### 枚举  
  
|Name|说明|  
|----------|--------|  
|[future\_errc 枚举](../Topic/future_errc%20Enumeration.md)|提供由`future_error`类支持的符号名错误 。|  
|[future\_status 枚举](../Topic/future_status%20Enumeration.md)|提供符号名对于一个可以返回计时等待函数原因。|  
|[launch 枚举](../Topic/launch%20Enumeration.md)|呈现了一个描述模版函数`async`的可能模式的位掩码类型。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)