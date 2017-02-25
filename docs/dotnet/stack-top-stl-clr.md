---
title: "stack::top (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::stack::top"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "top 成员 [STL/CLR]"
ms.assetid: 5d8b7b69-336e-4d01-8b91-413a17aa2533
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# stack::top (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

访问最后一个元素。  
  
## 语法  
  
```  
reference top();  
```  
  
## 备注  
 成员函数返回控制到序列中最后面的元素的引用，必须非空。  使用它访问，最后一个元素，在您知道存在\)。  
  
## 示例  
  
```  
// cliext_stack_top.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top() = {0}", c1.top());   
  
// alter last item and reinspect   
    c1.top() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**top\(\) \= c**  
 **a b x**   
## 要求  
 **标头:** \<cliext\/stack\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [stack](../dotnet/stack-stl-clr.md)   
 [stack::top\_item](../dotnet/stack-top-item-stl-clr.md)