---
title: "is_member_object_pointer 类 | Microsoft Docs"
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
  - "is_member_object_pointer"
  - "std.tr1.is_member_object_pointer"
  - "std::tr1::is_member_object_pointer"
  - "std.is_member_object_pointer"
  - "std::is_member_object_pointer"
  - "type_traits/std::is_member_object_pointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_member_object_pointer 类 [TR1]"
  - "is_member_object_pointer"
ms.assetid: 64f9cdf3-4621-4310-a076-a7bc986926b9
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_member_object_pointer 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为指向成员对象的指针。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_member_object_pointer;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是指向成员对象的指针，则类型谓词的实例为 true；如果它是指向成员对象的 `cv-qualified` 指针，则类型谓词的实例为 false。  请注意，如果 `Ty` 是指向成员函数的指针，则 `is_member_object_pointer` 为 false。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_member_object_pointer.cpp   
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
    std::cout << "is_member_object_pointer<trivial *> == "   
        << std::boolalpha   
        << std::is_member_object_pointer<trivial *>::value   
        << std::endl;   
    std::cout << "is_member_object_pointer<int trivial::*> == "   
        << std::boolalpha   
        << std::is_member_object_pointer<int trivial::*>::value   
        << std::endl;   
    std::cout << "is_member_object_pointer<int (functional::*)()> == "   
        << std::boolalpha   
        << std::is_member_object_pointer<int (functional::*)()>::value   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_member\_object\_pointer\<trivial \*\> \=\= false**  
**is\_member\_object\_pointer\<int trivial::\*\> \=\= true**  
**is\_member\_object\_pointer\<int \(functional::\*\)\(\)\> \=\= false**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_member\_pointer 类](../standard-library/is-member-pointer-class.md)