---
title: "is_nothrow_assignable 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_nothrow_assignable"
  - "std.is_nothrow_assignable"
  - "std::is_nothrow_assignable"
  - "type_traits/std::is_nothrow_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_assignable"
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# is_nothrow_assignable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试的值是否 `From` 类型可以分配给 `To` 类型和工作分配已知不引发。  
  
## 语法  
  
```  
template <class To, class From>   
    struct is_nothrow_assignable;  
```  
  
#### 参数  
 到  
 接收赋值的对象的类型。  
  
 从  
 提供值的对象的类型。  
  
## 备注  
 该表达式 `declval<To>() = declval<From>()` 必须是格式良好，并且必须向编译器知道无法引发。 同时 `From` 和 `To` 必须是完整的类型， `void`, ，或未知绑定的数组。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)