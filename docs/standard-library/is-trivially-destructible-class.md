---
title: "is_trivially_destructible 类 | Microsoft Docs"
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
  - "is_trivially_destructible"
  - "std.is_trivially_destructible"
  - "std::is_trivially_destructible"
  - "type_traits/std::is_trivially_destructible"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_trivially_destructible"
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_destructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为完全无法易损坏。  
  
## 语法  
  
```  
template <class T>  
    struct is_trivially_destructible;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果类型谓词的实例将为 true 类型 `T` 易损坏的类型，然后析构函数编译器知道要使用不重要的操作。 否则，为 false。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)