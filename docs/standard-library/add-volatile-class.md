---
title: "add_volatile 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::add_volatile"
  - "add_volatile"
  - "std.tr1.add_volatile"
  - "std.add_volatile"
  - "std::add_volatile"
  - "type_traits/std::add_volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_volatile 类 [TR1]"
  - "add_volatile"
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# add_volatile 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从指定类型创建可变类型。  
  
## 语法  
  
```  
template<class Ty>  
    struct add_volatile;  
  
template<class T>  
using add_volatile_t = typename add_volatile<T>::type;  
```  
  
#### 参数  
 `Ty`  
 要修改的类型。  
  
## 备注  
 类型修饰符的实例会保留修改后的类型，当 `Ty` 为引用、函数或可变限定类型时，修改后的类型为 `Ty`，否则为 `volatile Ty`。  
  
## 示例  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::add_volatile_t<int> *p = (volatile int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_volatile<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **add\_volatile\<int\> \=\= int**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_volatile 类](../standard-library/remove-volatile-class.md)