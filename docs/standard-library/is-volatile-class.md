---
title: "is_volatile 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::is_volatile"
  - "std.tr1.is_volatile"
  - "is_volatile"
  - "std.is_volatile"
  - "std::is_volatile"
  - "type_traits/std::is_volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_volatile 类 [TR1]"
  - "is_volatile"
ms.assetid: 54922e8a-db4e-4cae-8931-b3352f0b8d3b
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_volatile 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否是可变的。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_volatile;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果 `Ty` 是 `volatile-qualified`，则类型谓词的实例为 true。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_volatile.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_volatile<trivial> == " << std::boolalpha   
        << std::is_volatile<trivial>::value << std::endl;   
    std::cout << "is_volatile<volatile trivial> == " << std::boolalpha   
        << std::is_volatile<volatile trivial>::value << std::endl;   
    std::cout << "is_volatile<int> == " << std::boolalpha   
        << std::is_volatile<int>::value << std::endl;   
    std::cout << "is_volatile<volatile int> == " << std::boolalpha   
        << std::is_volatile<volatile int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_volatile\<trivial\> \=\= false**  
**is\_volatile\<volatile trivial\> \=\= true**  
**is\_volatile\<int\> \=\= false**  
**is\_volatile\<volatile int\> \=\= true**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_const 类](../standard-library/is-const-class.md)