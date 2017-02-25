---
title: "source_link_manager 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::source_link_manager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "source_link_manager 类"
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# source_link_manager 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`source_link_manager` 对象管理 `ISource` 块的消息阻止网络链接。  
  
## 语法  
  
```  
template<  
   class _LinkRegistry  
>  
class source_link_manager;  
```  
  
#### 参数  
 `_LinkRegistry`  
 网络链接注册表。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|`const_pointer`|一个类型，提供指向 `source_link_manager` 对象中 `const` 元素的指针。|  
|`const_reference`|提供对存储在 `source_link_manager` 对象中的 `const` 元素的引用从而读取和执行 const 操作的类型。|  
|`iterator`|提供可读取或修改 `source_link_manager` 对象中的任意元素的迭代器的类型。|  
|`type`|正由 `source_link_manager` 对象管理的链接注册表类型。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[source\_link\_manager::source\_link\_manager 构造函数](../Topic/source_link_manager::source_link_manager%20Constructor.md)|构造 `source_link_manager` 对象。|  
|[source\_link\_manager::~source\_link\_manager 析构函数](../Topic/source_link_manager::~source_link_manager%20Destructor.md)|销毁 `source_link_manager` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[source\_link\_manager::add 方法](../Topic/source_link_manager::add%20Method.md)|添加指向 `source_link_manager` 对象的源链接。|  
|[source\_link\_manager::begin 方法](../Topic/source_link_manager::begin%20Method.md)|返回指向 `source_link_manager` 对象中的第一个元素的迭代器。|  
|[source\_link\_manager::contains 方法](../Topic/source_link_manager::contains%20Method.md)|在此 `source_link_manager` 对象中的 `network_link_registry` 中搜索指定块。|  
|[source\_link\_manager::count 方法](../Topic/source_link_manager::count%20Method.md)|计算 `source_link_manager` 对象中已链接块的数量。|  
|[source\_link\_manager::reference 方法](../Topic/source_link_manager::reference%20Method.md)|获取对 `source_link_manager` 对象的引用。|  
|[source\_link\_manager::register\_target\_block 方法](../Topic/source_link_manager::register_target_block%20Method.md)|注册持有此 `source_link_manager` 对象的目标块。|  
|[source\_link\_manager::release 方法](../Topic/source_link_manager::release%20Method.md)|释放对 `source_link_manager` 对象的引用。|  
|[source\_link\_manager::remove 方法](../Topic/source_link_manager::remove%20Method.md)|从 `source_link_manager` 对象中移除链接。|  
|[source\_link\_manager::set\_bound 方法](../Topic/source_link_manager::set_bound%20Method.md)|设置可以添加到此 `source_link_manager` 对象的最大源链接数。|  
  
## 备注  
 当前，源块均被引用计算。  这是 `network_link_registry` 对象上的包装，允许对链接进行并发访问，并提供通过回调引用链接的能力。  消息块（`target_block` 或 `propagator_block`）应将此类用于其源链接。  
  
## 继承层次结构  
 `source_link_manager`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [single\_link\_registry 类](../../../parallel/concrt/reference/single-link-registry-class.md)   
 [multi\_link\_registry 类](../../../parallel/concrt/reference/multi-link-registry-class.md)