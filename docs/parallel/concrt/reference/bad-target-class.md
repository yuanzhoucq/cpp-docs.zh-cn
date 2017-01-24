---
title: "bad_target 类 | Microsoft Docs"
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
  - "concrt/concurrency::bad_target"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_target 类"
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bad_target 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

介绍异常引发此类，在消息块为指针的执行的操作无效的目标时。  
  
## 语法  
  
```  
class bad_target : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[bad\_target::bad\_target 构造函数](../Topic/bad_target::bad_target%20Constructor.md)|已重载。  构造 `bad_target` 对象。|  
  
## 备注  
 引发该异常的通常原因为，例如目标尝试使用为不同目标保留的消息或释放未持有的保留。  
  
## 继承层次结构  
 `exception`  
  
 `bad_target`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)