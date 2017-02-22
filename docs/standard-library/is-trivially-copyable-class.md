---
title: "is_trivially_copyable 类 | Microsoft Docs"
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
  - "is_trivially_copyable"
  - "std.is_trivially_copyable"
  - "std::is_trivially_copyable"
  - "type_traits/std::is_trivially_copyable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_copyable"
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# is_trivially_copyable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否是完全复制的类型。  
  
## 语法  
  
```  
template<class T>  
    struct is_trivially_copyable;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果类型谓词的实例将为 true 类型 `T` 是完全复制类型，否则为 false。 完全复制的类型具有任何非普通的复制操作、 移动操作或析构函数。 通常情况下，复制操作将被视为不重要，如果它可以实现为按位复制。 内置类型和完全复制类型的数组是完全复制。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)