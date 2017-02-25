---
title: "is_array 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_array"
  - "std.tr1.is_array"
  - "std::tr1::is_array"
  - "std.is_array"
  - "std::is_array"
  - "type_traits/std::is_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_array 类 [TR1]"
  - "is_array"
ms.assetid: 61fb2201-8de3-4746-9721-617f02df170f
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_array 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为数组。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_array;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是数组类型，则类型谓词的实例为 true；否则为 false。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_array.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_array<trivial> == " << std::boolalpha   
        << std::is_array<trivial>::value << std::endl;   
    std::cout << "is_array<int> == " << std::boolalpha   
        << std::is_array<int>::value << std::endl;   
    std::cout << "is_array<int[5]> == " << std::boolalpha   
        << std::is_array<int[5]>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_array\<trivial\> \=\= false**  
**is\_array\<int\> \=\= false**  
**is\_array\<int\[5\]\> \=\= true**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [extent 类](../standard-library/extent-class.md)   
 [rank 类](../standard-library/rank-class.md)