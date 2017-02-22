---
title: "is_trivially_assignable 类 | Microsoft Docs"
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
  - "is_trivially_assignable"
  - "std.is_trivially_assignable"
  - "std::is_trivially_assignable"
  - "type_traits/std::is_trivially_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_assignable"
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# is_trivially_assignable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试的值是否 `From` 类型可以完全无法分配给 `To` 类型  
  
## 语法  
  
```  
template <class To, class From>  
    struct is_trivially_assignable;  
```  
  
#### 参数  
 到  
 接收赋值的对象的类型。  
  
 从  
 提供值的对象的类型。  
  
## 备注  
 该表达式 `declval<To>() = declval<From>()` 必须是格式良好，并且必须向编译器已知需要任何重要的操作。 这两 `From` 和 `To` 必须是完整的类型， `void`, ，或未知绑定的数组。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)