---
title: "is_floating_point 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_floating_point"
  - "std.tr1.is_floating_point"
  - "std::tr1::is_floating_point"
  - "std.is_floating_point"
  - "std::is_floating_point"
  - "type_traits/std::is_floating_point"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_floating_point 类 [TR1]"
  - "is_floating_point"
ms.assetid: 070679c1-115b-4ee4-8ab7-f52e5d9e157f
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_floating_point 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为浮点。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_floating_point;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是浮点类型或 `cv-qualified` 形式的浮点类型，类型谓词的实例将为 true，否则为 false。  
  
 浮点类型为 `float`、`double` 或 `long double` 之一。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_floating_point.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_floating_point<trivial> == " << std::boolalpha   
        << std::is_floating_point<trivial>::value << std::endl;   
    std::cout << "is_floating_point<int> == " << std::boolalpha   
        << std::is_floating_point<int>::value << std::endl;   
    std::cout << "is_floating_point<float> == " << std::boolalpha   
        << std::is_floating_point<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_floating\_point\<trivial\> \=\= false**  
**is\_floating\_point\<int\> \=\= false**  
**is\_floating\_point\<float\> \=\= true**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_integral 类](../standard-library/is-integral-class.md)