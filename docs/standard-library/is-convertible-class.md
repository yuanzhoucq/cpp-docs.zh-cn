---
title: "is_convertible 类 | Microsoft Docs"
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
  - "is_convertible"
  - "std.tr1.is_convertible"
  - "std::tr1::is_convertible"
  - "std.is_convertible"
  - "std::is_convertible"
  - "type_traits/std::is_convertible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_convertible 类 [TR1]"
  - "is_convertible"
ms.assetid: 75614008-1894-42ea-bd57-974399628536
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_convertible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试一种类型是否可转换为另一种类型。  
  
## 语法  
  
```  
template<class From, class To>  
    struct is_convertible;  
```  
  
#### 参数  
 `From`  
 要转换的类型。  
  
 `Ty`  
 要转换为的类型。  
  
## 备注  
 如果表达式 `To to = from;`（其中 `from` 是类型 `From` 的对象）为标准的格式，则类型谓词的实例将为 true。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_convertible.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_convertible<trivial, int> == " << std::boolalpha   
        << std::is_convertible<trivial, int>::value << std::endl;   
    std::cout << "is_convertible<trivial, trivial> == " << std::boolalpha   
        << std::is_convertible<trivial, trivial>::value << std::endl;   
    std::cout << "is_convertible<char, int> == " << std::boolalpha   
        << std::is_convertible<char, int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_convertible\<trivial, int\> \=\= false**  
**is\_convertible\<trivial, trivial\> \=\= true**  
**is\_convertible\<char, int\> \=\= true**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_base\_of 类](../standard-library/is-base-of-class.md)