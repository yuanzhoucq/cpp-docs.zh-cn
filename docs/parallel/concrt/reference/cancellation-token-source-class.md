---
title: "cancellation_token_source 类 | Microsoft Docs"
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
  - "pplcancellation_token/concurrency::cancellation_token_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cancellation_token_source 类"
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
caps.latest.revision: 10
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# cancellation_token_source 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`cancellation_token_source` 类表示能够取消某些可取消操作的功能。  
  
## 语法  
  
```  
class cancellation_token_source;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[cancellation\_token\_source::cancellation\_token\_source 构造函数](../Topic/cancellation_token_source::cancellation_token_source%20Constructor.md)|已重载。  构造一个新的 `cancellation_token_source`。  该源可用于标记某可取消操作的取消。|  
|[cancellation\_token\_source::~cancellation\_token\_source 析构函数](../Topic/cancellation_token_source::~cancellation_token_source%20Destructor.md)||  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[cancellation\_token\_source::cancel 方法](../Topic/cancellation_token_source::cancel%20Method.md)|取消标记。  所有使用标记的 `task_group`、`structured_task_group` 或 `task` 将在此调用时取消，并在下一个中断点引发异常。|  
|[cancellation\_token\_source::create\_linked\_source 方法](../Topic/cancellation_token_source::create_linked_source%20Method.md)|已重载。  创建 `cancellation_token_source`，其在提供的标记被取消时被取消。|  
|[cancellation\_token\_source::get\_token 方法](../Topic/cancellation_token_source::get_token%20Method.md)|返回一个与此源相关联的取消标记。  如果发生取消操作，则返回的标记可能取消或提供回调。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[cancellation\_token\_source::operator\!\= 运算符](../Topic/cancellation_token_source::operator!=%20Operator.md)||  
|[cancellation\_token\_source::operator\= 运算符](../Topic/cancellation_token_source::operator=%20Operator.md)||  
|[cancellation\_token\_source::operator\=\= 运算符](../Topic/cancellation_token_source::operator==%20Operator.md)||  
  
## 继承层次结构  
 `cancellation_token_source`  
  
## 要求  
 **标头：**pplcancellation\_token.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)