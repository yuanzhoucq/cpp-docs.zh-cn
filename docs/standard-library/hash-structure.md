---
title: "hash 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "typeindex/std::hash"
dev_langs: 
  - "C++"
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# hash 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类将其方法定义为返回 `val.hash_code()`。 此方法定义用于将类型 [type\_index](../standard-library/type-index-class.md) 的值映射到索引值的分发的哈希函数。  
  
## 语法  
  
```vb  
template<>  
    struct hash<type_index>  
        : public unary_function<type_index, size_t>  
    { // hashes a typeinfo object  
    size_t operator()(type_index val) const;  
    };  
```  
  
## 请参阅  
 [\<typeindex\>](../standard-library/typeindex.md)