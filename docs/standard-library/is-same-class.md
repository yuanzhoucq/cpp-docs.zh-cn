---
title: "is_same 类 | Microsoft Docs"
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
  - "std::tr1::is_same"
  - "std.tr1.is_same"
  - "is_same"
  - "std.is_same"
  - "std::is_same"
  - "type_traits/std::is_same"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_same 类 [TR1]"
  - "is_same"
ms.assetid: d9df6c1d-c270-4ec2-802a-af275648dd1d
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_same 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试两个类型是否相同。  
  
## 语法  
  
```  
template<class Ty1, class Ty2>  
    struct is_same;  
```  
  
#### 参数  
 `Ty1`  
 要查询的第一个类型。  
  
 `Ty2`  
 要查询的第二个类型。  
  
## 备注  
 如果类型 `Ty1` 和 `Ty2` 是相同类型，则类型谓词的实例为 true；否则为 false。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_same.cpp   
// compile with: /EHsc   
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
    std::cout << "is_same<base, base> == " << std::boolalpha   
        << std::is_same<base, base>::value << std::endl;   
    std::cout << "is_same<base, derived> == " << std::boolalpha   
        << std::is_same<base, derived>::value << std::endl;   
    std::cout << "is_same<derived, base> == " << std::boolalpha   
        << std::is_same<derived, base>::value << std::endl;   
    std::cout << "is_same<int, int> == " << std::boolalpha   
        << std::is_same<int, int>::value << std::endl;   
    std::cout << "is_same<int, const int> == " << std::boolalpha   
        << std::is_same<int, const int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_same\<base, base\> \=\= true**  
**is\_same\<base, derived\> \=\= false**  
**is\_same\<derived, base\> \=\= false**  
**is\_same\<int, int\> \=\= true**  
**is\_same\<int, const int\> \=\= false**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_convertible 类](../standard-library/is-convertible-class.md)   
 [is\_base\_of 类](../standard-library/is-base-of-class.md)