---
title: "invalid_oversubscribe_operation 类 | Microsoft Docs"
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
  - "concrt/concurrency::invalid_oversubscribe_operation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_oversubscribe_operation 类"
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
caps.latest.revision: 19
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_oversubscribe_operation 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

，当 `Context::Oversubscribe` 方法调用与 `_BeginOversubscription` 参数设置为 `false` ，而无需事先调用 `Context::Oversubscribe` 与 `_BeginOversubscription` 参数的方法设置为 `true`时，介绍异常引发此类。  
  
## 语法  
  
```  
class invalid_oversubscribe_operation : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[invalid\_oversubscribe\_operation::invalid\_oversubscribe\_operation 构造函数](../Topic/invalid_oversubscribe_operation::invalid_oversubscribe_operation%20Constructor.md)|已重载。  构造 `invalid_oversubscribe_operation` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Context::Oversubscribe 方法](../Topic/Context::Oversubscribe%20Method.md)