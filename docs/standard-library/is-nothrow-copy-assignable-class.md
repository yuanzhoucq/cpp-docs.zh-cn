---
title: "is_nothrow_copy_assignable 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_nothrow_copy_assignable"
  - "std.is_nothrow_copy_assignable"
  - "std::is_nothrow_copy_assignable"
  - "type_traits/std::is_nothrow_copy_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_copy_assignable"
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# is_nothrow_copy_assignable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否具有与编译器已知无法引发一个复制赋值运算符。  
  
## 语法  
  
```  
template<class T>  
    struct is_nothrow_copy_assignable;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 类型谓词的实例会保留可引用类型，则返回 true `T` 其中 `is_nothrow_assignable<T&, const T&>` 包含 true; 否则为 false。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_nothrow\_assignable 类](../standard-library/is-nothrow-assignable-class.md)   
 [nothrow](../cpp/nothrow-cpp.md)