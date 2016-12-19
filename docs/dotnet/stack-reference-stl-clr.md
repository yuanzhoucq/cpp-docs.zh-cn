---
title: "stack::reference (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "引用成员 [STL/CLR]"
ms.assetid: 05c8fb2c-215c-4b83-80f9-d4d354577c6a
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack::reference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

元素的引用的类型。  
  
## 语法  
  
```  
typedef value_type% reference;  
```  
  
## 备注  
 此类型描述了一个对元素的引用。  
  
## 示例  
  
```  
// cliext_stack_reference.cpp   
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
  
// modify top of stack and redisplay   
    Mystack::reference ref = c1.top();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b x**   
## 要求  
 **标头:** \<cliext\/stack\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [stack](../dotnet/stack-stl-clr.md)   
 [stack::const\_reference](../dotnet/stack-const-reference-stl-clr.md)   
 [stack::value\_type](../dotnet/stack-value-type-stl-clr.md)