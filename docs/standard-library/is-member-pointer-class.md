---
title: "is_member_pointer 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::is_member_pointer"
  - "is_member_pointer"
  - "std.tr1.is_member_pointer"
  - "std.is_member_pointer"
  - "std::is_member_pointer"
  - "type_traits/std::is_member_pointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_member_pointer 类 [TR1]"
  - "is_member_pointer"
ms.assetid: da07ff4e-9ee0-4baa-ad93-1741f10913d1
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_member_pointer 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试，如果类型是指向成员的指针。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_member_pointer;  
```  
  
#### 参数  
 `Ty`  
 查询的类型。  
  
## 备注  
 谓词应用类型的实例，如果类型 `Ty` 是指针或指向成员函数的指针。成员对象，或者窗体。`cv-qualified` 中，否则它对负错误。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_member_pointer.cpp   
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
    std::cout << "is_member_pointer<trivial *> == "   
        << std::boolalpha   
        << std::is_member_pointer<trivial *>::value   
        << std::endl;   
    std::cout << "is_member_pointer<int trivial::*> == "   
        << std::boolalpha   
        << std::is_member_pointer<int trivial::*>::value   
        << std::endl;   
    std::cout << "is_member_pointer<int (functional::*)()> == "   
        << std::boolalpha   
        << std::is_member_pointer<int (functional::*)()>::value   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **\*\> is\_member\_pointertrivial\<\=\= 的错误**  
**is\_member\_pointerint\<true 的 trivial::\*\> \=\=**  
**true is\_member\_pointerint\<\(functional::\*\) \(\=\=\)\>**   
## 要求  
 **标头：** \<type\_traits\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_member\_function\_pointer 类](../standard-library/is-member-function-pointer-class.md)   
 [is\_member\_object\_pointer 类](../standard-library/is-member-object-pointer-class.md)   
 [is\_pointer 类](../standard-library/is-pointer-class.md)