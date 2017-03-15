---
title: "priority_queue::empty (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue::empty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "empty 成员 [STL/CLR]"
ms.assetid: bb2bc4cf-395f-4c4f-b432-550b85e1865d
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# priority_queue::empty (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试元素不存在。  
  
## 语法  
  
```  
bool empty();  
```  
  
## 备注  
 成员函数返回 true 一个空序列控制。  它与`() == 0`等效。[priority\_queue::size](../dotnet/priority-queue-size-stl-clr.md) 使用该测试 priority\_queue 是否为空。  
  
## 示例  
  
```  
// cliext_priority_queue_empty.cpp   
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
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.pop();   
    c1.pop();   
    c1.pop();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
  **c b**  
**size\(\) \= 3**  
**empty\(\) \= false**  
**size\(\) \= 0**  
**empty\(\) 为 True**   
## 要求  
 **页眉：** \<\/cliext 队列\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::size](../dotnet/priority-queue-size-stl-clr.md)