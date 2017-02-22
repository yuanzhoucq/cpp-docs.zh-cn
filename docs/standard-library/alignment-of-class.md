---
title: "alignment_of 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.alignment_of"
  - "std::tr1::alignment_of"
  - "alignment_of"
  - "std.alignment_of"
  - "std::alignment_of"
  - "type_traits/std::alignment_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "alignment_of 类 [TR1]"
  - "alignment_of"
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# alignment_of 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取指定类型的对齐方式。  此结构根据 [alignof](../cpp/alignof-and-alignas-cpp.md) 来实现。  只需查询对齐方式值时可直接使用 `alignof`。  需要整数常量时（例如在执行标记调度时），可使用 alignment\_of。  
  
## 语法  
  
```  
template<class Ty>  
    struct alignment_of;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 类型查询可保存 `Ty` 类型的对齐方式的值。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [aligned\_storage 类](../standard-library/aligned-storage-class.md)