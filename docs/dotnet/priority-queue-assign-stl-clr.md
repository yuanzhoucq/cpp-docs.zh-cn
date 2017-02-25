---
title: "priority_queue::assign (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue::assign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "assign 成员 [STL/CLR]"
ms.assetid: 00cd3623-ecd0-4dde-ba5c-777c1c0bc0b5
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# priority_queue::assign (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

替换所有元素。  
  
## 语法  
  
```  
void assign(priority_queue<Value, Container>% right);  
```  
  
#### 参数  
 right  
 插入容器适配器。  
  
## 备注  
 成员函数分配 `right``.get_container()`给基础容器。  将它更改队列的整个内容。  
  
## 示例  
  
```  
// cliext_priority_queue_assign.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Mypriority_queue c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c a b**  
 **c a b**   
## 要求  
 **标头:** \<cliext\/queue\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::operator\=](../dotnet/priority-queue-operator-assign-stl-clr.md)