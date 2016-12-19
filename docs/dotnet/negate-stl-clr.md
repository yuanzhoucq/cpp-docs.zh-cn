---
title: "negate (STL/CLR) | Microsoft Docs"
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
  - "cliext::negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "negate 函数 [STL/CLR]"
ms.assetid: 58e4c339-0dee-4db8-b2cc-de8920977039
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# negate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类描述了一个仿函数，调用它时，返回其否定参数。  根据其参数类型使用它来指定一个函数对象。  
  
## 语法  
  
```  
template<typename Arg>  
    ref class negate  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    negate();  
    negate(negate<Arg>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### 参数  
 Arg  
 参数类型。  
  
## 成员函数  
  
|类型定义|说明|  
|----------|--------|  
|类型变量|仿函数参数的类型。|  
|委托类型|泛型委托的类型。|  
|结果类型|仿函数结果的类型 。|  
  
|成员|说明|  
|--------|--------|  
|negate|构造仿函数。|  
  
|运算符|说明|  
|---------|--------|  
|operator\(\)|计算所需函数数量。|  
|运算符 delegate\_type^|转换仿函数为委托。|  
  
## 备注  
 模板类描述带有一个参数的仿函数。  它定义成员运算符 `operator()`，这样，当对象被调用作为函数时，它返回对其否定参数。  
  
 也可以传递对象作为类型为 `delegate_type^` 的函数参数，并将相应地转换。  
  
## 示例  
  
```  
// cliext_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(-3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 -3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::negate<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 \-3**  
 **\-4 3**   
## 要求  
 **Header:** \<cliext\/functional\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [logical\_not](../dotnet/logical-not-stl-clr.md)