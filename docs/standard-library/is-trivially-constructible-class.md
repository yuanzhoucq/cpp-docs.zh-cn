---
title: "is_trivially_constructible 类 | Microsoft Docs"
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
  - "is_trivially_constructible"
  - "std.is_trivially_constructible"
  - "std::is_trivially_constructible"
  - "type_traits/std::is_trivially_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_constructible"
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# is_trivially_constructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试是否使用指定的参数类型时，是完全无法构造类型。  
  
## 语法  
  
```  
template <class T, class... Args>  
    struct is_trivially_constructible;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
 `Args`  
 要匹配的构造函数中的参数类型 `T`。  
  
## 备注  
 如果类型谓词的实例将为 true 类型 `T` 是完全无法构造使用中的参数类型 `Args`, ，否则为 false。 类型 `T` 是完全无法构造如果变量定义 `T t(std::declval<Args>()...);` 格式正确并且知道要调用任何重要的操作。 同时 `T` 和中的所有类型 `Args` 必须是完整的类型， `void`, ，或未知绑定的数组。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)