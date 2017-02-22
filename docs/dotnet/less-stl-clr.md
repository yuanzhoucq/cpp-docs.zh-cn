---
title: "less (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::less"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "less 函数 [STL/CLR]"
ms.assetid: fae56216-af66-4cb9-a688-be58a7c7edbb
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# less (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述模板类，那么，当调用，则返回 true 的 functor，只有第一参数比第二个小于。  使用该指定函数对象根据其参数类型。  
  
## 语法  
  
```  
template<typename Arg>  
    ref class less  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    less();  
    less(less<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### 参数  
 Arg  
 参数的类型。  
  
## 成员函数  
  
|类型定义|说明|  
|----------|--------|  
|delegate\_type|泛型委托的类型。|  
|first\_argument\_type|functor 第一个参数的类型。|  
|result\_type|functor 结果的类型。|  
|second\_argument\_type|functor 第二个参数的类型。|  
  
|成员|说明|  
|--------|--------|  
|less|构造 functor。|  
  
|运算符|说明|  
|---------|--------|  
|operator\(\)|计算所需的函数。|  
|运算符 delegate\_type^|转换 functor 为委托。|  
  
## 备注  
 模板类描述两参数 functor。  它定义成员运算符 `operator()`，这样，当调用对象，作为函数时，它将返回 true，只有第一参数比第二个小于。  
  
 还可以传递一个对象，因为类型为 `delegate_type^` 的函数参数，并将相应地转换。  
  
## 示例  
  
```  
// cliext_less.cpp   
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
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::less<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **4 4**  
 **0 1**   
## 要求  
 **页眉：** \<\/cliext 功能\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [greater\_equal](../dotnet/greater-equal-stl-clr.md)