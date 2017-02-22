---
title: "sampler 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# sampler 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

采样器类聚合用于纹理采样的配置信息。  
  
## 语法  
  
```  
class sampler;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[sampler::sampler 构造函数](../Topic/sampler::sampler%20Constructor.md)|已重载。  构造采样器实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[sampler::get\_address\_mode 方法](../Topic/sampler::get_address_mode%20Method.md)|返回与采样器对象关联的 `address_mode`。|  
|[sampler::get\_border\_color 方法](../Topic/sampler::get_border_color%20Method.md)|返回与采样器对象关联的边框颜色。|  
|[sampler::get\_filter\_mode 方法](../Topic/sampler::get_filter_mode%20Method.md)|返回与采样器对象关联的 `filter_mode`。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[sampler::operator\= 运算符](../Topic/sampler::operator=%20Operator.md)|已重载。  赋值运算符。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[sampler::address\_mode 数据成员](../Topic/sampler::address_mode%20Data%20Member.md)|获取 `sampler` 对象的寻址模式。|  
|[sampler::border\_color 数据成员](../Topic/sampler::border_color%20Data%20Member.md)|获取 `sampler` 对象的边框颜色。|  
|[sampler::filter\_mode 数据成员](../Topic/sampler::filter_mode%20Data%20Member.md)|获取 `sampler` 对象的筛选模式。|  
  
## 继承层次结构  
 `sampler`  
  
## 要求  
 **标头：**amp\_graphics.h  
  
 **命名空间：**concurrency::graphics  
  
## 请参阅  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)