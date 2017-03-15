---
title: "discard_block_engine 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1.discard_block_engine"
  - "std.tr1.discard_block_engine"
  - "std::tr1::discard_block_engine"
  - "random/std::tr1::discard_block_engine"
  - "discard_block_engine"
  - "tr1::discard_block_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "discard_block_engine 类"
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# discard_block_engine 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过丢弃由其基引擎返回的值，生成随机序列。  
  
## 语法  
  
```  
template<class Engine, size_t P, size_t R> class discard_block_engine;  
```  
  
#### 参数  
 `Engine`  
 基引擎类型。  
  
 `P`  
 **块大小**。  每个块中的值数。  
  
 `R`  
 **已使用的块**。  已使用的每个块中的值数。  丢弃剩余部分（`P` \- `R`\).  **前置条件**：`0 < R ≤ P`  
  
## Members  
  
||||  
|-|-|-|  
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|  
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|  
  
 有关引擎成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 此模板类描述了通过弃用由其基引擎返回的一些值来产生值的引擎适配器。  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)