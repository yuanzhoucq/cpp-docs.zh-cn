---
title: "future 类 | Microsoft Docs"
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
  - "future/std::future"
dev_langs: 
  - "C++"
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
caps.latest.revision: 13
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# future 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 *异步的对象*。  
  
## 语法  
  
```  
template<class Ty>  
class future;  
```  
  
## 备注  
 每个标准 *异步的提供程序* 返回类型是此模板的实例化的对象。  `future` 对象提供对异步提供程序的唯一访问其关联。  如果需要与同一异步提供程序的多个异步的对象，请复制到 [shared\_future](../standard-library/shared-future-class.md) 对象的 `future` 对象。  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[future::future 构造函数](../Topic/future::future%20Constructor.md)|构造 `future` 对象。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[future::get 方法](../Topic/future::get%20Method.md)|在异步检索关联的状态存储的结果。|  
|[future::share 方法](../Topic/future::share%20Method.md)|转换为 `shared_future`的对象。|  
|[future::valid 方法](../Topic/future::valid%20Method.md)|指定对象是否不为 null。|  
|[future::wait 方法](../Topic/future::wait%20Method.md)|阻止当前线程，直到异步关联的就绪状态。|  
|[future::wait\_for 方法](../Topic/future::wait_for%20Method.md)|直到异步块关联的准备或直到指定的时间已经过去。|  
|[future::wait\_until 方法](../Topic/future::wait_until%20Method.md)|直到异步块关联的准备或直到指定的点。|  
  
### 公共运算符  
  
|Name|说明|  
|----------|--------|  
|[future::operator\= 运算符](../Topic/future::operator=%20Operator.md)|将从指定对象的关联异步的状态。|  
  
## 要求  
 **标头:** future  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)