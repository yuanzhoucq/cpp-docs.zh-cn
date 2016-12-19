---
title: "completion_future 类 | Microsoft Docs"
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
  - "amprt/Concurrency::completion_future"
dev_langs: 
  - "C++"
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# completion_future 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示对应 C\+\+ AMP 的异步操作的将来。  
  
## 语法  
  
```  
class completion_future;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[completion\_future::completion\_future 构造函数](../Topic/completion_future::completion_future%20Constructor.md)|初始化 `completion_future` 类的新实例。|  
|[completion\_future::~completion\_future 析构函数](../Topic/completion_future::~completion_future%20Destructor.md)|销毁 `completion_future` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[completion\_future::get 方法](../Topic/completion_future::get%20Method.md)|等待，直到关联的异步操作完成为止。|  
|[completion\_future::then 方法](../Topic/completion_future::then%20Method.md)|在相关联的异步操作完成执行时，请将一个回调函数对象链接至 `completion_future` 对象以执行。|  
|[completion\_future::to\_task 方法](../Topic/completion_future::to_task%20Method.md)|返回对应于关联的异步操作的 `task` 对象。|  
|[completion\_future::valid 方法](../Topic/completion_future::valid%20Method.md)|获取一个布尔值，该值指示该对象是否与异步操作关联。|  
|[completion\_future::wait 方法](../Topic/completion_future::wait%20Method.md)|阻止，直到关联的异步操作完成为止。|  
|[completion\_future::wait\_for 方法](../Topic/completion_future::wait_for%20Method.md)|阻止，直到关联的异步操作完成或 `_Rel_time` 指定的时间过去为止。|  
|[completion\_future::wait\_until 方法](../Topic/completion_future::wait_until%20Method.md)|阻止，直到关联的异步操作完成或当前时间超出由 `_Abs_time` 指定的值为止。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[completion\_future::operator std::shared\_future\<void\> 运算符](../Topic/completion_future::operator%20std::shared_future%3Cvoid%3E%20Operator.md)|隐式地将 `completion_future` 对象转换为 `std::shared_future` 对象。|  
|[completion\_future::operator\= 运算符](../Topic/completion_future::operator=%20Operator.md)|将指定的 `completion_future` 对象的内容复制到此对象中。|  
  
## 继承层次结构  
 `completion_future`  
  
## 要求  
 **标头：**amprt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)