---
title: "priority_queue::push (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::push"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "push 成员 [STL/CLR]"
ms.assetid: 317d3feb-0688-4658-866b-a26cae060354
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::push (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

添加一个新元素。  
  
## 语法  
  
```  
void push(value_type val);  
```  
  
## 备注  
 成员函数插入值为`val` 的元素到受控序列中，并对受控序列重新排序以保持堆的特性。  使用该示例将另一个元素添加到队列中。  
  
## 示例  
  
```  
// cliext_priority_queue_push.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a、b、c、\+、\=**   
## 要求  
 **标头:** \<cliext\/queue\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::pop](../dotnet/priority-queue-pop-stl-clr.md)