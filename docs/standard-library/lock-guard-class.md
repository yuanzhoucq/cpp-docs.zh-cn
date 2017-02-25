---
title: "lock_guard 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mutex/std::lock_guard"
dev_langs: 
  - "C++"
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# lock_guard 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示可以实例化创建对象析构函数释放锁定 `mutex`的模板。  
  
## 语法  
  
```  
template<class Mutex>  
class lock_guard;  
```  
  
## 备注  
 模板参数 `Mutex` 必须命名 *Mutex 类型*。  
  
## 成员  
  
### 公共 Typedef  
  
|Name|说明|  
|----------|--------|  
|`lock_guard::mutex_type`|模板参数的同义词。`Mutex`|  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[lock\_guard::lock\_guard 构造函数](../Topic/lock_guard::lock_guard%20Constructor.md)|构造 `lock_guard` 对象。|  
|[lock\_guard::~lock\_guard 析构函数](../Topic/lock_guard::~lock_guard%20Destructor.md)|取消锁定传递给构造函数的 `mutex`。|  
  
## 要求  
 **标头:** mutex  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)