---
title: "is_nothrow_destructible 类 | Microsoft Docs"
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
  - "is_nothrow_destructible"
  - "std.is_nothrow_destructible"
  - "std::is_nothrow_destructible"
  - "type_traits/std::is_nothrow_destructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_destructible"
ms.assetid: 0bbd8a28-e312-4d72-bd28-aac027f974d3
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# is_nothrow_destructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型易损坏以及编译器知道析构函数不以引发。  
  
## 语法  
  
```  
template <class T>  
    struct is_nothrow_destructible;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果类型谓词的实例将为 true 类型 `T` 易损坏的类型，然后编译器知道析构函数不以引发。 否则，为 false。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)