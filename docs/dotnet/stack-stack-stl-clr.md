---
title: "stack::stack (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stack 成员 [STL/CLR]"
ms.assetid: f1cfb3fe-4d22-41e5-906b-e8faa0bcde9b
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack::stack (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器适配器对象。  
  
## 语法  
  
```  
stack();  
stack(stack<Value, Container>% right);  
stack(stack<Value, Container>^ right);  
explicit stack(container_type% wrapped);  
```  
  
#### 参数  
 right  
 复制的对象。  
  
 包装  
 使用包装的容器。  
  
## 备注  
 构造函数：  
  
 `stack();`  
  
 创建空的包装的容器。  可以使用它来指定空的初始序列控制。  
  
 构造函数：  
  
 `stack(stack<Value, Container>% right);`  
  
 创建 `right.get_container()`复制的包装的容器。  将它指定为将顺序控制堆栈对象由 `right`控制的初始序列。  
  
 构造函数：  
  
 `stack(stack<Value, Container>^ right);`  
  
 创建 `right->get_container()`复制的包装的容器。  将它指定为将顺序控制堆栈对象由 `*right`控制的初始序列。  
  
 构造函数：  
  
 `explicit stack(container_type% wrapped);`  
  
 使用现有 `wrapped` 容器作为包装的容器。  使用该构造从现有容器的堆栈。  
  
## 示例  
  
```  
// cliext_stack_construct.cpp   
// compile with: /clr   
#include <cliext/stack>   
#include <cliext/vector>   
  
typedef cliext::stack<wchar_t> Mystack;   
typedef cliext::vector<wchar_t> Myvector;   
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;   
int main()   
    {   
// construct an empty container   
    Mystack c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Myvector v2(5, L'x');   
    Mystack_vec c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mystack_vec c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Mystack_vec c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **x x x x x**  
 **x x x x x**  
 **x x x x x**   
## 要求  
 **页眉：** \<\/cliext 堆栈\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [stack](../dotnet/stack-stl-clr.md)   
 [stack::assign](../dotnet/stack-assign-stl-clr.md)   
 [stack::generic\_container](../dotnet/stack-generic-container-stl-clr.md)   
 [stack::operator\=](../dotnet/stack-operator-assign-stl-clr.md)