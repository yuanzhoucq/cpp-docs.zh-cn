---
title: "is_bind_expression 类 | Microsoft Docs"
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
  - "std.tr1.is_bind_expression"
  - "is_bind_expression"
  - "std::tr1::is_bind_expression"
  - "functional/std::tr1::is_bind_expression"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_bind_expression 类 [TR1]"
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_bind_expression 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试，如果调用生成的 `bind`类型。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_bind_expression {  
    static const bool value;  
    };  
```  
  
## 备注  
 常数值 `value` 为 True，则类型是 `Ty` 调用的返回类型为 `bind`，否则为 false。  
  
## 示例  
  
```  
// std_tr1__functional__is_bind_expression.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
void square(double x)   
    {   
    std::cout << x << "^2 == " << x * x << std::endl;   
    }   
  
template<class Expr>   
    void test_for_bind(const Expr&)   
    {   
    std::cout << std::is_bind_expression<Expr>::value << std::endl;   
    }   
  
int main()   
    {   
    test_for_bind(3.0 * 3.0);   
    test_for_bind(std::bind(square, 3));   
  
    return (0);   
    }  
  
```  
  
  **0**  
**1**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [bind 函数](../Topic/bind%20Function.md)