---
title: "mutex 类 (STL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mutex/std::mutex"
dev_langs: 
  - "C++"
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# mutex 类 (STL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示一个 *mutex 类型*。  此类型对象可用于强制在程序内的互斥。  
  
## 语法  
  
```  
class mutex;  
```  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[mutex::mutex 构造函数 \(STL\)](../Topic/mutex::mutex%20Constructor%20\(STL\).md)|构造 `mutex` 对象。|  
|[mutex::~mutex 析构函数 \(STL\)](../Topic/mutex::~mutex%20Destructor%20\(STL\).md)|释放由该`mutex` 对象使用的任何资源。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[mutex::lock 方法 \(STL\)](../Topic/mutex::lock%20Method%20\(STL\).md)|阻止调用线程，直到线程获取 `mutex` 的所有权。|  
|[mutex::native\_handle 方法 \(STL\)](../Topic/mutex::native_handle%20Method%20\(STL\).md)|返回表示互斥句柄的特殊类型的实现。|  
|[mutex::try\_lock 方法 \(STL\)](../Topic/mutex::try_lock%20Method%20\(STL\).md)|在不阻止的情况下尝试获取 `mutex` 的所有权。|  
|[mutex::unlock 方法 \(STL\)](../Topic/mutex::unlock%20Method%20\(STL\).md)|释放 `mutex` 的所有权。|  
  
## 要求  
 **标头:** mutex  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)