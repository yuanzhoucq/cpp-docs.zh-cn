---
title: "ISource 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::ISource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISource 类"
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# ISource 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`ISource` 类是所有源块的接口。  源块将消息传播到 `ITarget` 块。  
  
## 语法  
  
```  
template<  
   class _Type  
>  
class ISource;  
```  
  
#### 参数  
 `_Type`  
 源块生成的消息内负载的数据类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|`source_type`|`_Type` 的类型别名。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[ISource::~ISource 析构函数](../Topic/ISource::~ISource%20Destructor.md)|销毁 `ISource` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ISource::accept 方法](../Topic/ISource::accept%20Method.md)|如果在派生的类中重写，接受由该 `ISource` 块提供的消息，将所有权转移给调用方。|  
|[ISource::acquire\_ref 方法](../Topic/ISource::acquire_ref%20Method.md)|如果在派生的类中重写，在该 `ISource` 块上获取索引计数，以防止删除。|  
|[ISource::consume 方法](../Topic/ISource::consume%20Method.md)|如果在派生类中重写，使用先前由 `ISource` 块提供并由目标成功保留的消息，将所有权转移给调用方。|  
|[ISource::link\_target 方法](../Topic/ISource::link_target%20Method.md)|在派生类中重写时，将目标块链接至该 `ISource` 块。|  
|[ISource::release 方法](../Topic/ISource::release%20Method.md)|当在派生类中被重写时，释放之前成功的消息保留。|  
|[ISource::release\_ref 方法](../Topic/ISource::release_ref%20Method.md)|如果在派生的类中重写，在该 `ISource` 块上释放索引计数。|  
|[ISource::reserve 方法](../Topic/ISource::reserve%20Method.md)|当在派生类中重写时，保留之前由该 `ISource` 块提供的消息。|  
|[ISource::unlink\_target 方法](../Topic/ISource::unlink_target%20Method.md)|在派生类中重写后，将目标块与该 `ISource` 块断开链接，前提是之前发现已链接。|  
|[ISource::unlink\_targets 方法](../Topic/ISource::unlink_targets%20Method.md)|在派生类中重写时，将所有目标块与该 `ISource` 块断开链接。|  
  
## 备注  
 有关更多信息，请参见 [异步消息块](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## 继承层次结构  
 `ISource`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ITarget 类](../../../parallel/concrt/reference/itarget-class.md)