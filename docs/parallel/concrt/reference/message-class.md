---
title: "message 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::message"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message 类"
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# message 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

包含正在消息块之间传递数据负载的基本消息信封。  
  
## 语法  
  
```  
template<  
   class _Type  
>  
class message : public ::Concurrency::details::_Runtime_object;  
```  
  
#### 参数  
 `_Type`  
 消息内的负载的数据类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|`type`|`_Type` 的类型别名。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[message::message 构造方法](../Topic/message::message%20Constructor.md)|已重载。  构造 `message` 对象。|  
|[message::~message 析构函数](../Topic/message::~message%20Destructor.md)|销毁 `message` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[message::add\_ref 方法](../Topic/message::add_ref%20Method.md)|添加到 `message` 对象的引用计数。  用于需要引用计数以确定消息生存期的消息块。|  
|[message::msg\_id 方法](../Topic/message::msg_id%20Method.md)|返回 `message` 对象的 ID。|  
|[message::remove\_ref 方法](../Topic/message::remove_ref%20Method.md)|从 `message` 对象的引用数中减去。  用于需要引用计数以确定消息生存期的消息块。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[message::payload 数据成员](../Topic/message::payload%20Data%20Member.md)|`message` 对象的负载。|  
  
## 备注  
 有关更多信息，请参见 [异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 继承层次结构  
 `message`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)