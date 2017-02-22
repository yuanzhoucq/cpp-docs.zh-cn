---
title: "is_base_of 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.is_base_of"
  - "is_base_of"
  - "std::tr1::is_base_of"
  - "std.is_base_of"
  - "std::is_base_of"
  - "type_traits/std::is_base_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_base_of 类 [TR1]"
  - "is_base_of"
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_base_of 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试一种类型是否是另一种类型的基类。  
  
## 语法  
  
```  
template<class Base, class Derived>  
    struct is_base_of;  
```  
  
#### 参数  
 `Base`  
 要测试的基类。  
  
 `Derived`  
 要测试的派生类型。  
  
## 备注  
 如果类型 `Base` 是类型 `Derived` 的基类，则类型谓词的实例为 true；否则为 false。  
  
## 示例  
  
```  
  
#include <type_traits>   
#include <iostream>   
  
struct base   
    {   
    int val;   
    };   
  
struct derived   
    : public base   
    {   
    };   
  
int main()   
    {   
    std::cout << "is_base_of<base, base> == " << std::boolalpha   
        << std::is_base_of<base, base>::value << std::endl;   
    std::cout << "is_base_of<base, derived> == " << std::boolalpha   
        << std::is_base_of<base, derived>::value << std::endl;   
    std::cout << "is_base_of<derived, base> == " << std::boolalpha   
        << std::is_base_of<derived, base>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_base\_of\<base, base\> \=\= true**  
**is\_base\_of\<base, derived\> \=\= true**  
**is\_base\_of\<derived, base\> \=\= false**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_convertible 类](../standard-library/is-convertible-class.md)