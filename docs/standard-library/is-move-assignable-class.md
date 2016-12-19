---
title: "is_move_assignable 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_move_assignable"
  - "std.is_move_assignable"
  - "std::is_move_assignable"
  - "type_traits/std::is_move_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_move_assignable"
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_move_assignable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试是否有此类型可以是移动分配。  
  
## 语法  
  
```  
template<class T>  
    struct is_move_assignable;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果对该类型的右值引用可以分配给对类型的引用的类型是移动赋值。 类型谓词等效于 `is_assignable<T&, T&&>`。 移动赋值的类型包括可引用标量类型，并具有编译器生成或用户定义的类类型移动赋值运算符。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)