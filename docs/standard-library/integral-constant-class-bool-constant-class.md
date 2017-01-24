---
title: "integral_constant 类，bool_constant 类 | Microsoft Docs"
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
  - "std.tr1.integral_constant"
  - "integral_constant"
  - "std::tr1::integral_constant"
  - "std.integral_constant"
  - "std::integral_constant"
  - "type_traits/std::integral_constant"
  - "std.bool_constant"
  - "std::bool_constant"
  - "type_traits/std::bool_constant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "integral_constant 类 [TR1]"
  - "integral_constant"
  - "bool_constant"
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
caps.latest.revision: 23
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# integral_constant 类，bool_constant 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从类型和值设置整型常量。  
  
## 语法  
  
```  
template <class T, T v>  
    struct integral_constant {  
        static constexpr T value = v;  
        typedef T value_type;  
        typedef integral_constant<T, v> type;  
        constexpr operator value_type() const noexcept { return (value); }  
        constexpr value_type operator()() const noexcept { return (value); }  
    };  
  
template <bool v>  
    using bool_constant = integral_constant<bool, v>;  
  
```  
  
#### 参数  
 `T`  
 常量的类型。  
  
 `v`  
 常量的值。  
  
## 备注  
 `integral_constant` 模板类，当带整型专用化 `T` 和值 `v` 的该类型表示包含指定的值与该整型类型的常量的对象。 名为的成员 `type` 是生成的模板专用化类型的别名和 `value` 成员将具有的值 `v` 用于创建专用化。  
  
 `bool_constant` 模板类是显式的部分专用化 `integral_constant` ，它使用 `bool` 作为 `T` 参数。  
  
## 示例  
  
```cpp  
// std__type_traits__integral_constant.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "integral_constant<int, 5> == "   
        << std::integral_constant<int, 5>::value << std::endl;   
    std::cout << "integral_constant<bool, false> == " << std::boolalpha   
        << std::integral_constant<bool, false>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
integral_constant < int，5 > = = 5 integral_constant < bool false > = = false  
```  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [false\_type Typedef](../Topic/false_type%20Typedef.md)   
 [true\_type Typedef](../Topic/true_type%20Typedef.md)