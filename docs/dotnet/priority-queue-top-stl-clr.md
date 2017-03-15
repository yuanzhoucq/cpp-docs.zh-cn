---
title: "priority_queue::top (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue::top"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "top 成员 [STL/CLR]"
ms.assetid: e45211d5-e6df-4c03-97fd-57afb87af58c
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# priority_queue::top (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

访问要求优先级最高的元素。  
  
## 语法  
  
```  
reference top();  
```  
  
## 备注  
 成员函数返回给控制序列的顶部 \(优先级最高的元素\) 的引用，必须非空。  使用访问它的优先级最高，的元素，在您知道存在\)。  
  
## 示例  
  
```  
// cliext_priority_queue_top.cpp   
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
  
  **c b**  
**top\(\) 为 c**  
 **x b**   
## 要求  
 **页眉：** \<\/cliext 队列\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::top\_item](../dotnet/priority-queue-top-item-stl-clr.md)