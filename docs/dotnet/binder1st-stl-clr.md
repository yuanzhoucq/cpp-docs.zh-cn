---
title: "binder1st (STL/CLR) | Microsoft Docs"
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
  - "cliext::binder1st"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binder1st 函数 [STL/CLR]"
ms.assetid: a989c9cc-a485-45d9-bd19-519018e6974b
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# binder1st (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述模板类，那么，当调用返回，其存储的两个参数 functor 调用及其存储的第一个参数提供的第二和参数的一个参数 functor。  在其存储函数对象期间使用它来指定一个函数对象。  
  
## 语法  
  
```  
template<typename Fun>  
    ref class binder1st  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        second_argument_type, result_type>  
        delegate_type;  
  
    binder1st(Fun% functor, first_argument_type left);  
    binder1st(binder1st<Arg>% right);  
  
    result_type operator()(second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### 参数  
 Fun  
 存储函数对象的类型。  
  
## 成员函数  
  
|类型定义|说明|  
|----------|--------|  
|委托类型|泛型委托的类型。|  
|第一个参数类型|第一个参数的函数对象类型。|  
|结果类型|仿函数结果的类型 。|  
|第二个参数类型|第二个参数的类型函数对象。|  
|stored\_function\_type|函数对象的类型。|  
  
|成员|说明|  
|--------|--------|  
|binder1st|构造仿函数。|  
  
|运算符|说明|  
|---------|--------|  
|operator\(\)|计算所需函数数量。|  
|运算符 delegate\_type^\(\)|转换仿函数为委托。|  
  
## 备注  
 描述模板类存储两参数 functor 和第一参数的一个参数 functor。  它定义成员运算符 `operator()`，这样，当对象为调用函数时，将只返回调用存储和使用的第一个参数提供的第二个参数的存储 functor 的结果。  
  
 也可以传递对象作为类型为 `delegate_type^` 的函数参数，并将相应地转换。  
  
## 示例  
  
```  
// cliext_binder1st.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **\-1 0**  
 **\-1 0**   
## 要求  
 **头文件:** \<cliext\/functional\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [bind1st](../dotnet/bind1st-stl-clr.md)