---
title: "is_function 类 | Microsoft Docs"
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
  - "std::tr1::is_function"
  - "std.tr1.is_function"
  - "is_function"
  - "std.is_function"
  - "std::is_function"
  - "type_traits/std::is_function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_function 类 [TR1]"
  - "is_function"
ms.assetid: e5c0dbcd-829b-415f-853f-8c5be47c5040
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_function 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为函数类型。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_function;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是函数类型，则类型谓词的实例为 true；否则为 false。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_function.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct functional   
    {   
    int f();   
    };   
  
int main()   
    {   
    std::cout << "is_function<trivial> == " << std::boolalpha   
        << std::is_function<trivial>::value << std::endl;   
    std::cout << "is_function<functional> == " << std::boolalpha   
        << std::is_function<functional>::value << std::endl;   
    std::cout << "is_function<float()> == " << std::boolalpha   
        << std::is_function<float()>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_function\<trivial\> \=\= false**  
**is\_function\<functional\> \=\= false**  
**is\_function\<float\(\)\> \=\= true**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_object 类](../standard-library/is-object-class.md)