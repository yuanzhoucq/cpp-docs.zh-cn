---
title: "shared_future 类 | Microsoft Docs"
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
  - "future/std::shared_future"
dev_langs: 
  - "C++"
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# shared_future 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 *异步的对象*。  [未来](../standard-library/future-class.md) 与对象不同，*异步的提供程序* 可与任意数量的 `shared_future` 对象。  
  
## 语法  
  
```  
template<class Ty>  
class shared_future;  
```  
  
## 备注  
 请勿调用任何方法为 `valid`、`operator=`和析构函数。在 *空的*`shared_future` 对象。  
  
 `shared_future` 对象不同步。  对同一对象的方法来自多个线程会具有不可预知的结果的数据通过争用来  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[shared\_future::shared\_future 构造函数](../Topic/shared_future::shared_future%20Constructor.md)|构造 `shared_future` 对象。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[shared\_future::get 方法](../Topic/shared_future::get%20Method.md)|在 *关联的异步状态*存储的结果。|  
|[shared\_future::valid 方法](../Topic/shared_future::valid%20Method.md)|指定对象是否不为 null。|  
|[shared\_future::wait 方法](../Topic/shared_future::wait%20Method.md)|阻止当前线程，直到异步关联的就绪状态。|  
|[shared\_future::wait\_for 方法](../Topic/shared_future::wait_for%20Method.md)|直到异步块关联的准备或直到指定的时间已经过去。|  
|[shared\_future::wait\_until 方法](../Topic/shared_future::wait_until%20Method.md)|直到异步块关联的准备或直到指定的点。|  
  
### 公共运算符  
  
|Name|说明|  
|----------|--------|  
|[shared\_future::operator\= 运算符](../Topic/shared_future::operator=%20Operator.md)|分配新异步关联的状态。|  
  
## 要求  
 **标头:** future  
  
 **命名空间:** std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)