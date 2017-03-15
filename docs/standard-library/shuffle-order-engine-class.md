---
title: "shuffle_order_engine 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "shuffle_order_engine"
  - "std.tr1.shuffle_order_engine"
  - "tr1::shuffle_order_engine"
  - "tr1.shuffle_order_engine"
  - "std::tr1::shuffle_order_engine"
  - "random/std::tr1::shuffle_order_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shuffle_order_engine 类"
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# shuffle_order_engine 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过对从其基引擎中返回的值进行重新排序，生成随机序列。  
  
## 语法  
  
```  
template<class Engine, size_t K>  
class shuffle_order_engine;  
```  
  
#### 参数  
 `Engine`  
 基引擎类型。  
  
 `K`  
 **表大小**。 缓冲区（表）中的元素数。**前置条件**：`0 < K`  
  
## 成员  
  
||||  
|-|-|-|  
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|  
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|  
  
 有关引擎成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 此模板类描述了通过对其基引擎返回的值进行重新排序来产生值的*引擎适配器*。 每个构造函数都将使用由基引擎返回的 `K` 值填充内部表，请求一个值后，将从该表中选择一个随机元素。  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)