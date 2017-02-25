---
title: "out_of_memory 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::out_of_memory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "out_of_memory 类"
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# out_of_memory 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

当由于缺少系统或设备内存方法失败时引发的异常。  
  
## 语法  
  
```  
class out_of_memory : public runtime_exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[out\_of\_memory::out\_of\_memory 构造函数](../Topic/out_of_memory::out_of_memory%20Constructor.md)|初始化 `out_of_memory` 类的新实例。|  
  
## 继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## 要求  
 **标题:**  amprt.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)