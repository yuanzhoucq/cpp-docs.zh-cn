---
title: "recursive_mutex 类 | Microsoft Docs"
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
  - "mutex/std::recursive_mutex"
dev_langs: 
  - "C++"
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
caps.latest.revision: 9
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# recursive_mutex 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示一个 *mutex 类型*。  与 [mutex](../standard-library/mutex-class-stl.md)不同，调用阻止方法的行为。已锁定的对象的过程模板是定义完善的。  
  
## 语法  
  
```  
class recursive_mutex;  
```  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[recursive\_mutex::recursive\_mutex 构造函数](../Topic/recursive_mutex::recursive_mutex%20Constructor.md)|构造 `recursive_mutex` 对象。|  
|[recursive\_mutex::~recursive\_mutex 析构函数](../Topic/recursive_mutex::~recursive_mutex%20Destructor.md)|释放 `recursive_mutex` 对象使用的所有资源。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[recursive\_mutex::lock 方法](../Topic/recursive_mutex::lock%20Method.md)|阻止调用线程，直到线程获取该 mutex 的所有权。|  
|[recursive\_mutex::try\_lock 方法](../Topic/recursive_mutex::try_lock%20Method.md)|尝试获取该 mutex 的所属权，但不阻塞。|  
|[recursive\_mutex::unlock 方法](../Topic/recursive_mutex::unlock%20Method.md)|释放 mutex 的所有权。|  
  
## 要求  
 **标头:** mutex  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)