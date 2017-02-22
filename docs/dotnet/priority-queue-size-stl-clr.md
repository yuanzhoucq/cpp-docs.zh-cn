---
title: "priority_queue::size (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue::size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size 成员 [STL/CLR]"
ms.assetid: 37ef4be3-daac-4b5a-9a00-085863f694e0
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# priority_queue::size (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计算元素的数量。  
  
## 语法  
  
```  
size_type size();  
```  
  
## 备注  
 成员函数返回控制序列的长度。  使用其当前确定元素的数目。控制序列。  如果您关注的是序列是否具有非零大小，请参见 [priority\_queue::empty](../dotnet/priority-queue-empty-stl-clr.md)`()`。  
  
## 示例  
  
```  
// cliext_priority_queue_size.cpp   
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
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// pop an item and reinspect   
    c1.pop();   
    System::Console::WriteLine("size() = {0} after popping", c1.size());   
  
// add two elements and reinspect   
    c1.push(L'a');   
    c1.push(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
  **c a b**  
**size\(\) \= 3从3开始：**  
**size\(\) \= 2 在弹出之后**  
**size\(\) \= 4 在" 2 "之后**   
## 要求  
 **标头:** \<cliext\/queue\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::empty](../dotnet/priority-queue-empty-stl-clr.md)