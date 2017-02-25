---
title: "greater (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::greater"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "greater 函数 [STL/CLR]"
ms.assetid: a6dfe5e3-b5a5-4ec4-8e53-8dd33a37d10d
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# greater (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述模板类，那么，当调用，则返回 true 的 functor，只有第一参数比第二大。  根据其参数类型使用它来指定一个函数对象。  
  
## 语法  
  
```  
template<typename Arg>  
    ref class greater  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    greater();  
    greater(greater<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### 参数  
 Arg  
 参数类型。  
  
## 成员函数  
  
|类型定义|说明|  
|----------|--------|  
|委托类型|泛型委托的类型。|  
|第一个参数类型|第一个参数的函数对象类型。|  
|结果类型|仿函数结果的类型 。|  
|第二个参数类型|第二个参数的类型函数对象。|  
  
|成员|说明|  
|--------|--------|  
|greater|构造仿函数。|  
  
|运算符|说明|  
|---------|--------|  
|operator\(\)|计算所需函数数量。|  
|运算符 delegate\_type^|转换仿函数为委托。|  
  
## 备注  
 模板类描述带有两个参数的仿函数。  它定义成员运算符 `operator()`，这样，当调用对象，作为函数时，它将返回 true，只有第一参数比第二大。  
  
 也可以传递对象作为类型为 `delegate_type^` 的函数参数，并将相应地转换。  
  
## 示例  
  
```  
// cliext_greater.cpp   
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
    c2.push_back(3);   
    c2.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 3 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::greater<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **3 3**  
 **1 0**   
## 要求  
 **Header:** \<cliext\/functional\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [less\_equal](../dotnet/less-equal-stl-clr.md)