---
title: "is_destructible 类 | Microsoft Docs"
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
  - "is_destructible"
  - "std.is_destructible"
  - "std::is_destructible"
  - "type_traits/std::is_destructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_destructible "
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# is_destructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试该类型是否易损坏。  
  
## 语法  
  
```  
template <class T>  
    struct is_destructible;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果类型 `T` 是易损坏类型，则类型谓词的实例为 true；否则为 false。 易损坏类型是引用类型、对象类型以及那些在其中对于等于 `remove_all_extents_t<T>` 的某些类型 `U` 而言未计算操作数 `std::declval<U&>.~U()` 格式正确的类型。 其他类型（包括不完整类型、`void` 和函数类型）均不属于易损坏类型。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)