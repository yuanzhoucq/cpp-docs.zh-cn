---
title: "decay 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "decay"
  - "std.tr1.decay"
  - "std::tr1::decay"
  - "std.decay"
  - "std::decay"
  - "type_traits/std::decay"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "decay 类 [TR1]"
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# decay 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

所传递的值，则生成的类型。 设置类型的非引用、 非常量、 非易失性，或者从一个函数或数组类型的类型设置指向的指针。  
  
## 语法  
  
```  
template<class T>  
    struct decay;  
  
template<class T> using decay_t = typename decay<T>::type;  
```  
  
#### 参数  
 `T`  
 要修改的类型。  
  
## 备注  
 Decay 模板用于生成结果的类型，就像按值作为参数传递的类型。 模板类成员 typedef `type` 包含在以下几个阶段中定义的修改的类型︰  
  
-   类型 `U` 定义为 `remove_reference<T>::type`。  
  
-   如果 `is_array<U>::value` 为 true，修改的类型 `type` 是 `remove_extent<U>::type *`。  
  
-   否则为如果 `is_function<U>::value` 为 true，修改的类型 `type` 是 `add_pointer<U>::type`。  
  
-   否则为在修改的类型 `type` 是 `remove_cv<U>::type`。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)