---
title: "packaged_task 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::packaged_task"
dev_langs: 
  - "C++"
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# packaged_task 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

介绍用调用包装调用签名为 `Ty(ArgTypes...)`的 *异步提供程序*。  除了不予结果之外，其 *关联异步的状态* 保留它可以调用的对象副本。  
  
## 语法  
  
```  
template<class>  
class packaged_task;  
```  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[packaged\_task::packaged\_task 构造函数](../Topic/packaged_task::packaged_task%20Constructor.md)|构造 `packaged_task` 对象。|  
|[packaged\_task::~packaged\_task 析构函数](../Topic/packaged_task::~packaged_task%20Destructor.md)|销毁 `packaged_task` 对象。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[packaged\_task::get\_future 方法](../Topic/packaged_task::get_future%20Method.md)|具有相同返回异步关联的 [未来](../standard-library/future-class.md) 对象。|  
|[packaged\_task::make\_ready\_at\_thread\_exit 方法](../Topic/packaged_task::make_ready_at_thread_exit%20Method.md)|在调用异步关联的状态存储可调用对象和基本存储区中返回的值。|  
|[packaged\_task::reset 方法](../Topic/packaged_task::reset%20Method.md)|替换与异步的状态。|  
|[packaged\_task::swap 方法](../Topic/packaged_task::swap%20Method.md)|交换关联异步的状态与一对指定的对象。|  
|[packaged\_task::valid 类](../Topic/packaged_task::valid%20Method.md)|指定对象是否具有关联异步的状态。|  
  
### 公共运算符  
  
|Name|说明|  
|----------|--------|  
|[packaged\_task::operator\= 运算符](../Topic/packaged_task::operator=%20Operator.md)|将从指定的对象与异步的状态。|  
|[packaged\_task::operator\(\) 运算符](../Topic/packaged_task::operator\(\)%20Operator.md)|在调用异步关联的状态存储可调用对象，基本存储区中返回的值，并将 *其*状态。|  
|[packaged\_task::operator bool 运算符](../Topic/packaged_task::operator%20bool%20Operator.md)|指定对象是否具有关联异步的状态。|  
  
## 要求  
 **标头:** future  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)