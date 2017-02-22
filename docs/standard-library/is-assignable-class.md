---
title: "is_assignable 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_assignable"
  - "std.is_assignable"
  - "std::is_assignable"
  - "type_traits/std::is_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_assignable"
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# is_assignable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试的值是否 `From` 类型可以分配给 `To` 类型。  
  
## 语法  
  
```  
template <class To, class From>  
    struct is_assignable;  
```  
  
#### 参数  
 到  
 接收赋值的对象的类型。  
  
 从  
 提供值的对象的类型。  
  
## 备注  
 未计算的表达式 `declval<To>() = declval<From>()` 必须是格式良好。 这两 `From` 和 `To` 必须是完整的类型， `void`, ，或未知绑定的数组。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)