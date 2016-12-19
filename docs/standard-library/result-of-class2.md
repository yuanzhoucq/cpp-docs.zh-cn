---
title: "result_of 类 | Microsoft Docs"
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
  - "functional/std::tr1::result_of"
  - "std::tr1::result_of"
  - "result_of"
  - "std.tr1.result_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "result_of 类 [TR1]"
ms.assetid: 14ec0040-07f1-45a5-80b5-d0c9f9b00c8f
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# result_of 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包装的可调用对象的返回类型。  
  
## 语法  
  
```  
template<class Ty>  
    struct result_of {  
    typedef T0 type;  
    };  
```  
  
#### 参数  
 `Ty`  
 调用函数的说明 \(请参见"备注"节。\)  
  
## 备注  
 模板类定义了其成员 `type`，其模板参数描述的函数调用的返回类型的同义词 `Ty`。  模板参数必须是 `Fty(T1, T2, ..., TN)`格式，`Fty` 是可调用的类型。  模板根据应用的第一天规则确定返回类型：  
  
-   如果 `Fty` 为函数的指针类型时返回 `R(*)(U1, U2, ..., UN)` 类型为 `R`;  
  
-   如果 `Fty` 为函数类型 `R(&)(U1, U2, ..., UN)` 的引用返回类型为 `R`;  
  
-   如果 `Fty` 是指向成员函数 `R(U1::*)(U2, ..., UN)` 类型的返回类型为 `R`;  
  
-   如果 `Fty` 为指向数据成员 `R U1::*` 类型的返回类型为 `R`;  
  
-   如果 `Fty` 为与成员 `result_type` typedef 的类返回类型为 `Fty::result_type`;  
  
-   如果 `N` 是 0 \(即 `Ty` 是窗体 `Fty()`\) 返回类型为 `void`;  
  
-   如果 `Fty` 与名为 `result` 的成员模板的类返回类型为 `Fty::result<T1, T2, ..., TN>::type`;  
  
-   在所有其他情况下这是一个错误。  
  
## 示例  
  
```  
// std_tr1__functional__result_of.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
double square(double x)   
    {   
    return (x * x);   
    }   
  
template<class Fun,   
    class Arg>   
    void test_result(const Fun& fun, Arg arg)   
    {   
    typename std::result_of<Fun(Arg)>::type val = fun(arg);   
    std::cout << "val == " << val << std::endl;   
    }   
  
int main()   
    {   
    test_result(&square, 3.0);   
  
    return (0);   
    }  
  
```  
  
  **val \=\= 9**   
## 要求  
 **标头：** \<起作用的\>  
  
 **命名空间:**  std