---
title: "is_pointer 类 | Microsoft Docs"
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
  - "std.tr1.is_pointer"
  - "is_pointer"
  - "std::tr1::is_pointer"
  - "std.is_pointer"
  - "std::is_pointer"
  - "type_traits/std::is_pointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_pointer 类 [TR1]"
  - "is_pointer"
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_pointer 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为指针。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_pointer;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是指向 `void` 的指针、指向对象的指针、指向函数的指针或是其中之一的 `cv-qualified` 形式，类型谓词的实例将为 true，否则为 false。  请注意，如果 `Ty` 是指向成员的指针或指向成员函数的指针，则 `is_pointer` 为 false。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_pointer.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_pointer<trivial> == " << std::boolalpha   
        << std::is_pointer<trivial>::value << std::endl;   
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha   
        << std::is_pointer<int trivial::*>::value << std::endl;   
    std::cout << "is_pointer<trivial *> == " << std::boolalpha   
        << std::is_pointer<trivial *>::value << std::endl;   
    std::cout << "is_pointer<int> == " << std::boolalpha   
        << std::is_pointer<int>::value << std::endl;   
    std::cout << "is_pointer<int *> == " << std::boolalpha   
        << std::is_pointer<int *>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_pointer\<trivial\> \=\= false**  
**is\_pointer\<int trivial::\*\> \=\= false**  
**is\_pointer\<trivial \*\> \=\= true**  
**is\_pointer\<int\> \=\= false**  
**is\_pointer\<int \*\> \=\= true**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_member\_pointer 类](../standard-library/is-member-pointer-class.md)   
 [is\_reference 类](../standard-library/is-reference-class.md)