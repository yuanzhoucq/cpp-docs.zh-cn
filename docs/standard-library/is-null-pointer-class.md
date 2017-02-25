---
title: "is_null_pointer 类 | Microsoft Docs"
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
  - "is_null_pointer"
  - "std.is_null_pointer"
  - "std::is_null_pointer"
  - "type_traits/std::is_null_pointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_null_pointer"
ms.assetid: f3b3601b-f162-4803-a6e9-dabf5c3876cc
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# is_null_pointer 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否 std::nullptr\_t。  
  
## 语法  
  
```  
template<class T>  
    struct is_null_pointer;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果类型谓词的实例将为 true 类型 `T` 是 `std::nullptr_t`, ，否则为 false。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)