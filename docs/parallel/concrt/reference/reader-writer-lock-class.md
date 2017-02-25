---
title: "reader_writer_lock 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::reader_writer_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reader_writer_lock 类"
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# reader_writer_lock 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

只能本地旋转的基于编写器首选队列的读取器\-编写器锁。  锁授予对编写器的先进先出 \(FIFO\) 访问，并使读取器在编写器在持续负载的情况下停止。  
  
## 语法  
  
```  
class reader_writer_lock;  
```  
  
## 成员  
  
### 公共类  
  
|名称|说明|  
|--------|--------|  
|[reader\_writer\_lock::scoped\_lock 类](../Topic/reader_writer_lock::scoped_lock%20Class.md)|可用于获取 `reader_writer_lock` 锁定对象用作编写器的异常安全 RAII 包装。|  
|[reader\_writer\_lock::scoped\_lock\_read 类](../Topic/reader_writer_lock::scoped_lock_read%20Class.md)|可用于获取 `reader_writer_lock` 锁定对象用作读取器的异常安全 RAII 包装。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[reader\_writer\_lock::reader\_writer\_lock 构造函数](../Topic/reader_writer_lock::reader_writer_lock%20Constructor.md)|构造新的 `reader_writer_lock` 对象。|  
|[reader\_writer\_lock::~reader\_writer\_lock 析构函数](../Topic/reader_writer_lock::~reader_writer_lock%20Destructor.md)|销毁 `reader_writer_lock` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[reader\_writer\_lock::lock 方法](../Topic/reader_writer_lock::lock%20Method.md)|获取读取器\-编写器锁，用作编写器。|  
|[reader\_writer\_lock::lock\_read 方法](../Topic/reader_writer_lock::lock_read%20Method.md)|获取读取器\-编写器锁，用作读取器。  如果有编写器，活动的读取器必须等待直到这些编写器完成。  读取器只注册感兴趣锁定并等待编写器释放它。|  
|[reader\_writer\_lock::try\_lock 方法](../Topic/reader_writer_lock::try_lock%20Method.md)|尝试将读取器\-编写器锁获取为一个不阻塞的编写器。|  
|[reader\_writer\_lock::try\_lock\_read 方法](../Topic/reader_writer_lock::try_lock_read%20Method.md)|尝试将读取器\-编写器锁获取为一个不阻塞的读取器。|  
|[reader\_writer\_lock::unlock 方法](../Topic/reader_writer_lock::unlock%20Method.md)|根据锁定读取器\-编写器锁的读取器和编写器进行解锁。|  
  
## 备注  
 有关更多信息，请参见 [同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## 继承层次结构  
 `reader_writer_lock`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [critical\_section 类](../../../parallel/concrt/reference/critical-section-class.md)