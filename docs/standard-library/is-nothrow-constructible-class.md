---
title: "is_nothrow_constructible 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_nothrow_constructible"
  - "std.is_nothrow_constructible"
  - "std::is_nothrow_constructible"
  - "type_traits/std::is_nothrow_constructible"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_nothrow_constructible"
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_nothrow_constructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型可构造，以及已知不使用指定的参数类型时引发。  
  
## 语法  
  
```  
template <class T, class... Args>  
    struct is_nothrow_constructible;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
 `Args`  
 要匹配的构造函数中的参数类型 `T`。  
  
## 备注  
 如果类型谓词的实例将为 true 类型 `T` 是构造使用中的参数类型 `Args`, ，并且编译器已知构造函数无法引发; 否则为 false。 类型 `T` 是构造如果变量定义 `T t(std::declval<Args>()...);` 的格式是否正确。 同时 `T` 和中的所有类型 `Args` 必须是完整的类型， `void`, ，或未知绑定的数组。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)