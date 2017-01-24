---
title: "is_arithmetic 类 | Microsoft Docs"
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
  - "is_arithmetic"
  - "std.tr1.is_arithmetic"
  - "std::tr1::is_arithmetic"
  - "std.is_arithmetic"
  - "std::is_arithmetic"
  - "type_traits/std::is_arithmetic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_arithmetic 类 [TR1]"
  - "is_arithmetic"
ms.assetid: ea427b7e-0141-4a04-848f-561054c53001
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_arithmetic 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为算术型。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_arithmetic;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是算术类型（即整型类型、浮点类型或前述其中一个类型的 `cv-qualified` 形式），则类型谓词的实例将为 true，否则为 false。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_arithmetic.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_arithmetic<trivial> == " << std::boolalpha   
        << std::is_arithmetic<trivial>::value << std::endl;   
    std::cout << "is_arithmetic<int> == " << std::boolalpha   
        << std::is_arithmetic<int>::value << std::endl;   
    std::cout << "is_arithmetic<float> == " << std::boolalpha   
        << std::is_arithmetic<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_arithmetic\<trivial\> \=\= false**  
**is\_arithmetic\<int\> \=\= true**  
**is\_arithmetic\<float\> \=\= true**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_floating\_point 类](../standard-library/is-floating-point-class.md)   
 [is\_integral 类](../standard-library/is-integral-class.md)