---
title: "message_not_found 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::message_not_found"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message_not_found 类"
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# message_not_found 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

，当消息块找不到请求的消息时，此类描述时引发的异常。  
  
## 语法  
  
```  
class message_not_found : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[message\_not\_found::message\_not\_found 构造函数](../Topic/message_not_found::message_not_found%20Constructor.md)|已重载。  构造 `message_not_found` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `message_not_found`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)