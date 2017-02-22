---
title: "_1 对象 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1._1"
  - "_1"
  - "std::tr1::_1"
  - "functional/std::tr1::_1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_1 对象 [TR1]"
ms.assetid: 30c3c480-ff31-4708-94be-7d0d65f243c9
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _1 对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可替换参数的占位符。  
  
## 语法  
  
```  
namespace placeholders {  
  extern unspecified _1, _2, ... _M  
  } // namespace placeholders (within std)  
```  
  
## 备注  
 `_1, _2, ... _M` 对象是占位符，其通过 [bind 函数](../Topic/bind%20Function.md) 在一个函数调用中分别指定第一个、第二个、…第 M 个参数。  您使用 `_N` 以指定当评估绑定表达式时应插入第 N 参数的位置。  
  
 在此实现中，`M` 的值为 20。  
  
## 示例  
  
```cpp  
// std__functional_placeholder.cpp   
// compile with: /EHsc   
#include <functional>   
#include <algorithm>   
#include <iostream>   
  
using namespace std::placeholders;   
  
void square(double x)   
    {   
    std::cout << x << "^2 == " << x * x << std::endl;   
    }   
  
void product(double x, double y)   
    {   
    std::cout << x << "*" << y << " == " << x * y << std::endl;   
    }   
  
int main()   
    {   
    double arg[] = {1, 2, 3};   
  
    std::for_each(&arg[0], &arg[3], square);   
    std::cout << std::endl;   
  
    std::for_each(&arg[0], &arg[3], std::bind(product, _1, 2));   
    std::cout << std::endl;   
  
    std::for_each(&arg[0], &arg[3], std::bind(square, _1));   
  
    return (0);   
    }  
  
```  
  
  **1^2 \=\= 1**  
**2^2 \=\= 4**  
**3^2 \=\= 9**  
**1\*2 \=\= 2**  
**2\*2 \=\= 4**  
**3\*2 \=\= 6**  
**1^2 \=\= 1**  
**2^2 \=\= 4**  
**3^2 \=\= 9**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [bind 函数](../Topic/bind%20Function.md)   
 [is\_placeholder 类](../standard-library/is-placeholder-class.md)