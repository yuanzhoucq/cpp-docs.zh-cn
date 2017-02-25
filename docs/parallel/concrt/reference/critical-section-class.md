---
title: "critical_section 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::critical_section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "critical_section 类"
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# critical_section 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

一个明确知道并发运行时的非重入互斥体。  
  
## 语法  
  
```  
class critical_section;  
```  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`native_handle_type`|一个对 `critical_section` 对象的引用。|  
  
### 公共类  
  
|名称|说明|  
|--------|--------|  
|[critical\_section::scoped\_lock 类](../Topic/critical_section::scoped_lock%20Class.md)|`critical_section` 对象的异常安全 RAII 包装。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[critical\_section::critical\_section 构造函数](../Topic/critical_section::critical_section%20Constructor.md)|构造一个新的临界区。|  
|[critical\_section::~critical\_section 析构函数](../Topic/critical_section::~critical_section%20Destructor.md)|销毁临界区。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[critical\_section::lock 方法](../Topic/critical_section::lock%20Method.md)|获取此临界区。|  
|[critical\_section::native\_handle 方法](../Topic/critical_section::native_handle%20Method.md)|如果存在，则返回一个特定于平台的本机句柄。|  
|[critical\_section::try\_lock 方法](../Topic/critical_section::try_lock%20Method.md)|尝试在没有阻止的情况下获取锁定。|  
|[critical\_section::try\_lock\_for 方法](../Topic/critical_section::try_lock_for%20Method.md)|尝试获取锁，而不阻碍一个具体的毫秒数。|  
|[critical\_section::unlock 方法](../Topic/critical_section::unlock%20Method.md)|解锁临界区。|  
  
## 备注  
 有关详细信息，请参阅[同步数据结构](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## 继承层次结构  
 `critical_section`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [reader\_writer\_lock 类](../../../parallel/concrt/reference/reader-writer-lock-class.md)