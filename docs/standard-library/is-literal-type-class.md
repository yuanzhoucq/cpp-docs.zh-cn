---
title: "is_literal_type 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_literal_type"
  - "std.is_literal_type"
  - "std::is_literal_type"
  - "type_traits/std::is_literal_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_literal_type"
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_literal_type 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试是否可用作一种类型 `constexpr` 变量或可构造，请使用，或从返回 `constexpr` 函数。  
  
## 语法  
  
```  
template <class T>  
    struct is_literal_type;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果类型谓词的实例将为 true 类型 `T` 是 *文本类型*, ，否则为 false。 文字类型为 `void`, ，标量类型、 引用类型、 文本类型的数组或文字类类型。 文本类类型是具有普通的析构函数的类类型、 聚合类型或具有至少一个非移动，非复制 `constexpr` 构造函数中，和它的所有基类和非静态数据成员都是非易失性文字类型。 文本类型的概念虽然文本类型始终是文本类型，包括任何编译器可以计算为 `constexpr` 在编译时。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)