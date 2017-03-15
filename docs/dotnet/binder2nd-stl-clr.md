---
title: "binder2nd (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::binder2nd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binder2nd 函数 [STL/CLR]"
ms.assetid: f4be8722-1778-4cb9-9ec7-ad1443f6899f
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# binder2nd (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述模板类，那么，当调用返回，其存储的两个参数 functor 调用该提供的第一参数及其存储的第二个参数的参数 functor。  使用该指定函数。对象的存储的 functor。  
  
## 语法  
  
```  
template<typename Fun>  
    ref class binder2nd  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        first_argument_type, result_type>  
        delegate_type;  
  
    binder2nd(Fun% functor, second_argument_type left);  
    binder2nd(binder2nd<Arg>% right);  
  
    result_type operator()(first_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### 参数  
 挑战性。  
 存储的 functor 的类型。  
  
## 成员函数  
  
|类型定义|说明|  
|----------|--------|  
|delegate\_type|泛型委托的类型。|  
|first\_argument\_type|functor 第一个参数的类型。|  
|result\_type|functor 结果的类型。|  
|second\_argument\_type|functor 第二个参数的类型。|  
|stored\_function\_type|functor 的类型。|  
  
|成员|说明|  
|--------|--------|  
|binder2nd|构造 functor。|  
  
|运算符|说明|  
|---------|--------|  
|operator\(\)|计算所需的函数。|  
|运算符 delegate\_type^\(\)|转换 functor 为委托。|  
  
## 备注  
 描述模板类存储两参数 functor 和第二个参数的参数 functor 一。  它定义成员运算符 `operator()`，这样，当对象为，调用函数时调用，它将返回。提供的第一个参数。和存储的第二个参数的存储 functor 的结果。  
  
 还可以传递一个对象，因为类型为 `delegate_type^` 的函数参数，并将相应地转换。  
  
## 示例  
  
```  
// cliext_binder2nd.cpp   
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
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **0 \-1**  
 **0 \-1**   
## 要求  
 **页眉：** \<\/cliext 功能\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [bind2nd](../dotnet/bind2nd-stl-clr.md)