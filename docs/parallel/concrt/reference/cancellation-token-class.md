---
title: "cancellation_token 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pplcancellation_token/concurrency::cancellation_token"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cancellation_token 类"
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# cancellation_token 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`cancellation_token` 类表示能够确定某项操作是否已请求取消的功能。  给定的标记可与 `task_group`、`structured_task_group` 或 `task` 关联以实现隐式取消。  它还可以因取消而进行轮询，或则当取消关联的 `cancellation_token_source` 时，还可以注册回调。  
  
## 语法  
  
```  
class cancellation_token;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[cancellation\_token::cancellation\_token 构造函数](../Topic/cancellation_token::cancellation_token%20Constructor.md)||  
|[cancellation\_token::~cancellation\_token 析构函数](../Topic/cancellation_token::~cancellation_token%20Destructor.md)||  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[cancellation\_token::deregister\_callback 方法](../Topic/cancellation_token::deregister_callback%20Method.md)|通过 `register` 方法移除之前注册的回调，此方法基于注册时返回的 `cancellation_token_registration` 对象。|  
|[cancellation\_token::is\_cancelable 方法](../Topic/cancellation_token::is_cancelable%20Method.md)|返回一个指示，指示此标记是否可以删除。|  
|[cancellation\_token::is\_canceled 方法](../Topic/cancellation_token::is_canceled%20Method.md)|如果标记已取消，则返回 `true`。|  
|[cancellation\_token::none 方法](../Topic/cancellation_token::none%20Method.md)|返回一个取消标记，此标记不受取消限制。|  
|[cancellation\_token::register\_callback 方法](../Topic/cancellation_token::register_callback%20Method.md)|利用标记注册一个回调函数。  当取消该标记时，会进行回调。  请注意，如果标记已在调用此方法的点被删除，将立即并同步进行回调。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[cancellation\_token::operator\!\= 运算符](../Topic/cancellation_token::operator!=%20Operator.md)||  
|[cancellation\_token::operator\= 运算符](../Topic/cancellation_token::operator=%20Operator.md)||  
|[cancellation\_token::operator\=\= 运算符](../Topic/cancellation_token::operator==%20Operator.md)||  
  
## 继承层次结构  
 `cancellation_token`  
  
## 要求  
 **标头：**pplcancellation\_token.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)