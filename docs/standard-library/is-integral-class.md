---
title: "is_integral 类 | Microsoft Docs"
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
  - "std::tr1::is_integral"
  - "std.tr1.is_integral"
  - "is_integral"
  - "std.is_integral"
  - "std::is_integral"
  - "type_traits/std::is_integral"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_integral 类 [TR1]"
  - "is_integral"
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_integral 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为整型。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_integral;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是整型类型之一，或整型类型之一的 `cv-qualified` 形式，则类型谓词的实例将为 true，否则为 false。  
  
 整型类型是 `bool`、`char`、`unsigned char`、`signed char`、`wchar_t`、`short`、`unsigned short`、`int`、`unsigned int`、`long` 和 `unsigned long` 之一。  此外，若使用提供这些类型的编译器，整型类型还可以是 `long long`、`unsigned long long`、`__int64` 和 `unsigned __int64` 之一。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_integral.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_integral<trivial> == " << std::boolalpha   
        << std::is_integral<trivial>::value << std::endl;   
    std::cout << "is_integral<int> == " << std::boolalpha   
        << std::is_integral<int>::value << std::endl;   
    std::cout << "is_integral<float> == " << std::boolalpha   
        << std::is_integral<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_integral\<trivial\> \=\= false**  
**is\_integral \< int \> \= \= true**  
**is\_integral\<float\> \=\= false**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_enum 类](../standard-library/is-enum-class.md)   
 [is\_floating\_point 类](../standard-library/is-floating-point-class.md)