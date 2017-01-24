---
title: "ITarget 类 | Microsoft Docs"
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
  - "agents/concurrency::ITarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITarget 类"
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
caps.latest.revision: 22
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ITarget 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`ITarget` 类是所有目标块的接口。  目标块使用 `ISource` 块提供给他们的消息。  
  
## 语法  
  
```  
template<  
   class _Type  
>  
class ITarget;  
```  
  
#### 参数  
 `_Type`  
 目标块接受的消息内负载的数据类型。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`filter_method`|返回 `bool` 值的块使用的任何方法的签名确定提供的消息是否应接受。|  
|`type`|`_Type` 的类型别名。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[ITarget::~ITarget 析构函数](../Topic/ITarget::~ITarget%20Destructor.md)|销毁 `ITarget` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ITarget::propagate 方法](../Topic/ITarget::propagate%20Method.md)|在派生类中重写后，异步地将消息从源块传递至该目标块。|  
|[ITarget::send 方法](../Topic/ITarget::send%20Method.md)|当在派生类中重写时，异步将消息传递至目标块。|  
|[ITarget::supports\_anonymous\_source 方法](../Topic/ITarget::supports_anonymous_source%20Method.md)|重写派生类中，则返回 TRUE 或 FALSE 根据消息块是接受不链接到它的源提供的消息。  如果重写方法返回 `true`，目标不可以推迟提供的消息，因为已推迟消息的开销在其 sourse 链接注册表要求后源中标识。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[ITarget::link\_source 方法](../Topic/ITarget::link_source%20Method.md)|在派生类中重写时，将指定的源块链接至该 `ITarget` 块。|  
|[ITarget::unlink\_source 方法](../Topic/ITarget::unlink_source%20Method.md)|在派生类中重写时，将指定的源块与该 `ITarget` 块断开链接。|  
|[ITarget::unlink\_sources 方法](../Topic/ITarget::unlink_sources%20Method.md)|在派生类中重写时，将所有源块与该 `ITarget` 块断开链接。|  
  
## 备注  
 有关详细信息，请参阅[异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 继承层次结构  
 `ITarget`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ISource 类](../../../parallel/concrt/reference/isource-class.md)