---
title: "is_scalar 类 | Microsoft Docs"
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
  - "std.tr1.is_scalar"
  - "std::tr1::is_scalar"
  - "is_scalar"
  - "std.is_scalar"
  - "std::is_scalar"
  - "type_traits/std::is_scalar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_scalar 类 [TR1]"
  - "is_scalar"
ms.assetid: a0cdfc9a-f27e-4808-890f-6ed7942db60c
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_scalar 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为标量。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_scalar;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是整数类型、浮点类型、枚举类型、指针类型或指向成员类型的指针或其中任意一个的 `cv-qualified` 形式，则类型谓词的实例将为 true；否则为 false。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_scalar.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_scalar<trivial> == " << std::boolalpha   
        << std::is_scalar<trivial>::value << std::endl;   
    std::cout << "is_scalar<trivial *> == " << std::boolalpha   
        << std::is_scalar<trivial *>::value << std::endl;   
    std::cout << "is_scalar<int> == " << std::boolalpha   
        << std::is_scalar<int>::value << std::endl;   
    std::cout << "is_scalar<float> == " << std::boolalpha   
        << std::is_scalar<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_scalar\<trivial\> \=\= false**  
**is\_scalar\<trivial \*\> \=\= true**  
**is\_scalar\<int\> \=\= true**  
**is\_scalar\<float\> \=\= true**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_compound 类](../standard-library/is-compound-class.md)