---
title: "uninitialized_object 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::uninitialized_object"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uninitialized_object 类"
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# uninitialized_object 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

当使用未初始化的对象时引发的异常。  
  
## 语法  
  
```  
class uninitialized_object : public runtime_exception;  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[uninitialized\_object::uninitialized\_object 构造函数](../Topic/uninitialized_object::uninitialized_object%20Constructor.md)|初始化 `uninitialized_object` 类的新实例。|  
  
## 继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `uninitialized_object`  
  
## 要求  
 **标题:**  amprt.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)