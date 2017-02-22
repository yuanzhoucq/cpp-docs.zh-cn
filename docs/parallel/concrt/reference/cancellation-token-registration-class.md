---
title: "cancellation_token_registration 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pplcancellation_token/concurrency::cancellation_token_registration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cancellation_token_registration 类"
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# cancellation_token_registration 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`cancellation_token_registration` 类表示来自 `cancellation_token` 的回调通知。  如果 `cancellation_token` 上的 `register` 方法用于接收取消何时发生的通知，系统就会将 `cancellation_token_registration` 对象作为回调的句柄返回，让调用方可以请求不再通过使用 `deregister` 方法实现的特定回调。  
  
## 语法  
  
```  
class cancellation_token_registration;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[cancellation\_token\_registration::cancellation\_token\_registration 构造函数](../Topic/cancellation_token_registration::cancellation_token_registration%20Constructor.md)||  
|[cancellation\_token\_registration::~cancellation\_token\_registration 析构函数](../Topic/cancellation_token_registration::~cancellation_token_registration%20Destructor.md)||  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[cancellation\_token\_registration::operator\!\= 运算符](../Topic/cancellation_token_registration::operator!=%20Operator.md)||  
|[cancellation\_token\_registration::operator\= 运算符](../Topic/cancellation_token_registration::operator=%20Operator.md)||  
|[cancellation\_token\_registration::operator\=\= 运算符](../Topic/cancellation_token_registration::operator==%20Operator.md)||  
  
## 继承层次结构  
 `cancellation_token_registration`  
  
## 要求  
 **标头：**pplcancellation\_token.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)