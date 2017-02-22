---
title: "is_trivial 类 | Microsoft Docs"
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
  - "is_trivial"
  - "std.is_trivial"
  - "std::is_trivial"
  - "type_traits/std::is_trivial"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivial"
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# is_trivial 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为通常类型。  
  
## 语法  
  
```  
template <class T>  
    struct is_trivial;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果类型 `T` 是常用类型，则类型谓词的实例为 true；否则为 false。 常用类型是标量类型、完全可复制类类型、这些类型的数组以及这些类型的 cv 限定版本。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)