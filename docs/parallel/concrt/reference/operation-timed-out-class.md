---
title: "operation_timed_out 类 | Microsoft Docs"
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
  - "concrt/concurrency::operation_timed_out"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operation_timed_out 类"
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operation_timed_out 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

，当操作超时时，介绍异常引发此类。  
  
## 语法  
  
```  
class operation_timed_out : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[operation\_timed\_out::operation\_timed\_out 构造函数](../Topic/operation_timed_out::operation_timed_out%20Constructor.md)|已重载。  构造 `operation_timed_out` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `operation_timed_out`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)