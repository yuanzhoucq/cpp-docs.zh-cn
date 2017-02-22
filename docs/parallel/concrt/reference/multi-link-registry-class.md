---
title: "multi_link_registry 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::multi_link_registry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multi_link_registry 类"
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# multi_link_registry 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`multi_link_registry` 对象是 `network_link_registry`，管理多个源块或多个目标块。  
  
## 语法  
  
```  
template<  
   class _Block  
>  
class multi_link_registry : public network_link_registry<_Block>;  
```  
  
#### 参数  
 `_Block`  
 `multi_link_registry` 对象中存储的块数据类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[multi\_link\_registry::multi\_link\_registry 构造函数](../Topic/multi_link_registry::multi_link_registry%20Constructor.md)|构造 `multi_link_registry` 对象。|  
|[multi\_link\_registry::~multi\_link\_registry 析构函数](../Topic/multi_link_registry::~multi_link_registry%20Destructor.md)|销毁 `multi_link_registry` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[multi\_link\_registry::add 方法](../Topic/multi_link_registry::add%20Method.md)|添加指向 `multi_link_registry` 对象的链接。（重写 [network\_link\_registry::add](../Topic/network_link_registry::add%20Method.md)。）|  
|[multi\_link\_registry::begin 方法](../Topic/multi_link_registry::begin%20Method.md)|返回指向 `multi_link_registry` 对象中的第一个元素的迭代器。（重写 [network\_link\_registry::begin](../Topic/network_link_registry::begin%20Method.md)。）|  
|[multi\_link\_registry::contains 方法](../Topic/multi_link_registry::contains%20Method.md)|在 `multi_link_registry` 对象中搜索指定块。（重写 [network\_link\_registry::contains](../Topic/network_link_registry::contains%20Method.md)。）|  
|[multi\_link\_registry::count 方法](../Topic/multi_link_registry::count%20Method.md)|计算 `multi_link_registry` 对象中的项数。（重写 [network\_link\_registry::count](../Topic/network_link_registry::count%20Method.md)。）|  
|[multi\_link\_registry::remove 方法](../Topic/multi_link_registry::remove%20Method.md)|从 `multi_link_registry` 对象中移除链接。（重写 [network\_link\_registry::remove](../Topic/network_link_registry::remove%20Method.md)。）|  
|[multi\_link\_registry::set\_bound 方法](../Topic/multi_link_registry::set_bound%20Method.md)|设置 `multi_link_registry` 对象可以保存的链接数的上限。|  
  
## 继承层次结构  
 [network\_link\_registry](../../../parallel/concrt/reference/network-link-registry-class.md)  
  
 `multi_link_registry`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [single\_link\_registry 类](../../../parallel/concrt/reference/single-link-registry-class.md)