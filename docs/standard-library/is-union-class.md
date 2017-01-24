---
title: "is_union 类 | Microsoft Docs"
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
  - "is_union"
  - "std::tr1::is_union"
  - "std.tr1.is_union"
  - "std.is_union"
  - "std::is_union"
  - "type_traits/std::is_union"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_union 类 [TR1]"
  - "is_union"
ms.assetid: 80eda256-40b8-4db5-9ac1-d58bb8032a3e
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_union 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为联合。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_union;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是联合类型或 `cv-qualified` 形式的联合类型，则类型谓词的实例保留为 true，否则保留为 false。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_union.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
union ints   
    {   
    int in;   
    long lo;   
    };   
  
int main()   
    {   
    std::cout << "is_union<trivial> == " << std::boolalpha   
        << std::is_union<trivial>::value << std::endl;   
    std::cout << "is_union<int> == " << std::boolalpha   
        << std::is_union<int>::value << std::endl;   
    std::cout << "is_union<ints> == " << std::boolalpha   
        << std::is_union<ints>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_union\<trivial\> \=\= false**  
**is\_union\<int\> \=\= false**  
**is\_union\<ints\> \=\= true**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_class 类](../standard-library/is-class-class.md)