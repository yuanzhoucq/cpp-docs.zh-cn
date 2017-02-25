---
title: "is_placeholder 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_placeholder"
  - "std.tr1.is_placeholder"
  - "functional/std::tr1::is_placeholder"
  - "std::tr1::is_placeholder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_placeholder 类 [TR1]"
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# is_placeholder 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试，如果类型为占位符。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_placeholder {  
    static const int value;  
    };  
```  
  
## 备注  
 如果类型没有 `Ty` 只是占位符，常数值 `value` 为 0;否则，其值是绑定函数调用参数的位置。  使用它确定第 N 的占位符的 `_N``N` 值。  
  
## 示例  
  
```  
// std_tr1__functional__is_placeholder.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
using namespace std::placeholders;   
  
template<class Expr>   
    void test_for_placeholder(const Expr&)   
    {   
    std::cout << std::is_placeholder<Expr>::value << std::endl;   
    }   
  
int main()   
    {   
    test_for_placeholder(3.0);   
    test_for_placeholder(_3);   
  
    return (0);   
    }  
  
```  
  
  **0**  
**3**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\_1 对象](../standard-library/1-object.md)