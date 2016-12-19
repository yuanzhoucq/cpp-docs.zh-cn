---
title: "unique_lock 类 | Microsoft Docs"
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
  - "mutex/std::unique_lock"
dev_langs: 
  - "C++"
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
caps.latest.revision: 10
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unique_lock 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示可以实例化对象创建托管锁定和取消锁定 `mutex`的模板。  
  
## 语法  
  
```  
template<class Mutex>  
class unique_lock;  
```  
  
## 备注  
 模板参数 `Mutex` 必须命名 *Mutex 类型*。  
  
 在内部，`unique_lock` 存储指向某一关联的 `mutex` 对象和 `bool` 当前线程是否拥有 `mutex`。  
  
## 成员  
  
### 公共 Typedef  
  
|Name|说明|  
|----------|--------|  
|`unique_lock::mutex_type`|模板参数的同义词。`Mutex`|  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[unique\_lock::unique\_lock 构造函数](../Topic/unique_lock::unique_lock%20Constructor.md)|构造 `unique_lock` 对象。|  
|[unique\_lock::~unique\_lock 析构函数](../Topic/unique_lock::~unique_lock%20Destructor.md)|释放与 `unique_lock` 对象的所有资源。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[unique\_lock::lock 方法](../Topic/unique_lock::lock%20Method.md)|阻止调用线程，直到该线程获得关联 `mutex`的所有权。|  
|[unique\_lock::mutex 方法](../Topic/unique_lock::mutex%20Method.md)|检索存储区的指针为关联 `mutex`。|  
|[unique\_lock::owns\_lock 方法](../Topic/unique_lock::owns_lock%20Method.md)|指定调用线程是否拥有关联 `mutex`。|  
|[unique\_lock::release 方法](../Topic/unique_lock::release%20Method.md)|离散从关联的 `mutex` 对象的 `unique_lock` 对象。|  
|[unique\_lock::swap 方法](../Topic/unique_lock::swap%20Method.md)|交换将所有权和 `mutex` 状态与一对指定的对象。|  
|[unique\_lock::try\_lock 方法](../Topic/unique_lock::try_lock%20Method.md)|在不阻止的情况下尝试获取关联 `mutex` 的所有权。|  
|[unique\_lock::try\_lock\_for 方法](../Topic/unique_lock::try_lock_for%20Method.md)|在不阻止的情况下尝试获取关联 `mutex` 的所有权。|  
|[unique\_lock::try\_lock\_until 方法](../Topic/unique_lock::try_lock_until%20Method.md)|在不阻止的情况下尝试获取关联 `mutex` 的所有权。|  
|[unique\_lock::unlock 方法](../Topic/unique_lock::unlock%20Method.md)|释放与 `mutex`的所有权。|  
  
### 公共运算符  
  
|Name|说明|  
|----------|--------|  
|[unique\_lock::operator bool 运算符](../Topic/unique_lock::operator%20bool%20Operator.md)|指定调用的线程是否有关联 `mutex`的所有权。|  
|[unique\_lock::operator\= 运算符](../Topic/unique_lock::operator=%20Operator.md)|复制存储指针的 `mutex` 和关联所有权状态从指定的对象。|  
  
## 继承层次结构  
 `unique_lock`  
  
## 要求  
 **标头:** mutex  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)