---
title: "network_link_registry 类 | Microsoft Docs"
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
  - "agents/concurrency::network_link_registry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "network_link_registry 类"
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# network_link_registry 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`network_link_registry` 的抽象基类管理源和目标块之间的链接。  
  
## 语法  
  
```  
template<  
   class _Block  
>  
class network_link_registry;  
```  
  
#### 参数  
 `_Block`  
 `network_link_registry` 中存储的块数据类型。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|`const_pointer`|一个类型，提供指向 `network_link_registry` 对象中 `const` 元素的指针。|  
|`const_reference`|提供对存储在 `network_link_registry` 对象中的 `const` 元素的引用从而读取和执行 const 操作的类型。|  
|`iterator`|提供可读取或修改 `network_link_registry` 对象中的任意元素的迭代器的类型。|  
|`type`|表示存储在 `network_link_registry` 对象中的块类型的类型。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[network\_link\_registry::add 方法](../Topic/network_link_registry::add%20Method.md)|在派生类中重写时，向 `network_link_registry` 对象中添加一个链接。|  
|[network\_link\_registry::begin 方法](../Topic/network_link_registry::begin%20Method.md)|当在派生类中重写时，将迭代器返回至 `network_link_registry` 对象中的第一元素。|  
|[network\_link\_registry::contains 方法](../Topic/network_link_registry::contains%20Method.md)|在派生类中重写时，为指定的块搜索 `network_link_registry` 对象。|  
|[network\_link\_registry::count 方法](../Topic/network_link_registry::count%20Method.md)|在派生类中重写时，返回 `network_link_registry` 对象中的项目数。|  
|[network\_link\_registry::remove 方法](../Topic/network_link_registry::remove%20Method.md)|在派生类中重写时，从 `network_link_registry` 对象中移除指定块。|  
  
## 备注  
 `network link registry` 对并发访问是不安全的。  
  
## 继承层次结构  
 `network_link_registry`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [single\_link\_registry 类](../../../parallel/concrt/reference/single-link-registry-class.md)   
 [multi\_link\_registry 类](../../../parallel/concrt/reference/multi-link-registry-class.md)