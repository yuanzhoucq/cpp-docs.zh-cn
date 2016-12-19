---
title: "unary_negate (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::unary_negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unary_negate 函数 [STL/CLR]"
ms.assetid: 83bbdd86-199c-4451-9f70-72f9ade2264a
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unary_negate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述模板类表示当调用一个函数对象，返回，其存储一个参数函数对象的逻辑“非”。  在其存储函数对象期间使用它来指定一个函数对象。  
  
## 语法  
  
```  
template<typename Fun>  
    ref class unary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::argument_type argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    unary_negate(Fun% functor);  
    unary_negate(unary_negate<Fun>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### 参数  
 Fun  
 存储函数对象的类型。  
  
## 成员函数  
  
|类型定义|说明|  
|----------|--------|  
|类型变量|仿函数参数的类型。|  
|委托类型|泛型委托的类型。|  
|结果类型|仿函数结果的类型 。|  
  
|成员|说明|  
|--------|--------|  
|unary\_negate|构造仿函数。|  
  
|运算符|说明|  
|---------|--------|  
|operator\(\)|计算所需函数数量。|  
|委托类型^|转换仿函数为委托。|  
  
## 备注  
 模板类表示一个含有一个参数的函数对象，该函数对象存储另一个含有一个参数函数对象。  它定义成员运算符 `operator()`，这样，当对象作为函数被调用时，它返回调用参数的存储函数对象的逻辑“非”。  
  
 也可以传递对象作为类型为 `delegate_type^` 的函数参数，并将相应地转换。  
  
## 示例  
  
```  
// cliext_unary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 0**  
 **1 0**  
 **1 0**   
## 要求  
 **头文件:** \<cliext\/functional\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [not1](../dotnet/not1-stl-clr.md)