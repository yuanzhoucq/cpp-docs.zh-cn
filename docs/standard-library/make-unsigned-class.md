---
title: "make_unsigned 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.make_unsigned"
  - "make_unsigned"
  - "std::tr1::make_unsigned"
  - "std.make_unsigned"
  - "std::make_unsigned"
  - "type_traits/std::make_unsigned"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_unsigned 类 [TR1]"
  - "make_unsigned"
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# make_unsigned 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

设置类型或大小大于或等于类型的无符号的最小类型。  
  
## 语法  
  
```  
template<class T>  
    struct make_unsigned;  
  
template<class T>  
    using make_unsigned_t = typename make_unsigned<T>::type;  
  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`T`|要修改的类型。|  
  
## 备注  
 如果 `is_unsigned<T>` 为 true，则类型修饰符的实例保留修改后的类型 `T`。  否则，它就是适用于 `sizeof (T) <= sizeof (ST)` 的最小的带符号类型 `ST`。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)