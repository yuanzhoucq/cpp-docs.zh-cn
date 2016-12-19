---
title: "priority_queue::pop (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::pop"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pop 成员 [STL/CLR]"
ms.assetid: d363b3f1-247b-466a-a300-c5918b0dfd4e
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::pop (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除 proirity 最高的元素。  
  
## 语法  
  
```  
void pop();  
```  
  
## 备注  
 移除成员函数控制序列的优先级最高的元素，必须非空。  使用由元素结合在队列返回。  
  
## 示例  
  
```  
// cliext_priority_queue_pop.cpp   
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
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c b**  
 **为 b**   
## 要求  
 **页眉：** \<\/cliext 队列\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::push](../dotnet/priority-queue-push-stl-clr.md)