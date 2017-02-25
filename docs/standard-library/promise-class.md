---
title: "promise 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::promise"
dev_langs: 
  - "C++"
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# promise 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describes“异步提供程序” .  
  
## 语法  
  
```  
template<class Ty>  
class promise;  
```  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[promise::promise 构造函数](../Topic/promise::promise%20Constructor.md)|构造 `promise` 对象。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[promise::get\_future 方法](../Topic/promise::get_future%20Method.md)|返回与承诺有关的“将来” [](../standard-library/future-class.md "future Class") 。|  
|[promise::set\_exception 方法](../Topic/promise::set_exception%20Method.md)|基本设置承诺的结果指示异常。|  
|[promise::set\_exception\_at\_thread\_exit 方法](../Topic/promise::set_exception_at_thread_exit%20Method.md)|基本设置 的结果指示异常，只有在销毁后当前线程上的所有线程本地对象 \(通常在线程退出时\)才会传递通知。|  
|[promise::set\_value 方法](../Topic/promise::set_value%20Method.md)|基本设置承诺的结果指示值。|  
|[promise::set\_value\_at\_thread\_exit 方法](../Topic/promise::set_value_at_thread_exit%20Method.md)|基本设置的结果指示异常，只有在销毁后当前线程上的所有线程本地对象 \(通常在线程退出时\)才会传递通知。|  
|[promise::swap 方法](../Topic/promise::swap%20Method.md)|交换“关联的异步状态”  与指定的承诺对象。|  
  
### 公共运算符  
  
|Name|说明|  
|----------|--------|  
|[promise::operator\= Operator](../Topic/promise::operator=%20Operator.md)|此承诺对象共享状态的分配。|  
  
## 继承层次结构  
 `promise`  
  
## 要求  
 **标头:** future  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)