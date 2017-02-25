---
title: "is_abstract 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.is_abstract"
  - "std::tr1::is_abstract"
  - "is_abstract"
  - "std.is_abstract"
  - "std::is_abstract"
  - "type_traits/std::is_abstract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_abstract 类 [TR1]"
  - "is_abstract"
ms.assetid: 8867f660-3434-404c-ba90-c26607a5e0d2
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_abstract 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为抽象类。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_abstract;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是具有至少一个纯虚拟函数的类，则类型谓词的实例为 true；否则为 false。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_abstract.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct abstract   
    {   
    virtual int val() = 0;   
    };   
  
int main()   
    {   
    std::cout << "is_abstract<trivial> == " << std::boolalpha   
        << std::is_abstract<trivial>::value << std::endl;   
    std::cout << "is_abstract<abstract> == " << std::boolalpha   
        << std::is_abstract<abstract>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_abstract < 普通 > = = false is_abstract < 抽象 > = = true  
```  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_polymorphic 类](../standard-library/is-polymorphic-class.md)