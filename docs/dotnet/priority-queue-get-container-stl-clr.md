---
title: "priority_queue::get_container (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue::get_container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "get_container 成员 [STL/CLR]"
ms.assetid: bd3cc63b-776f-495c-bf81-a9e8ba189a56
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# priority_queue::get_container (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

访问基础容器。  
  
## 语法  
  
```  
container_type get_container();  
```  
  
## 备注  
 成员函数返回基础容器。  使用它绕过容器包装施加的限制。  
  
## 示例  
  
```  
// cliext_priority_queue_get_container.cpp   
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
    return (0);   
    }  
  
```  
  
  **c b**   
## 要求  
 **页眉：** \<\/cliext 队列\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::container\_type](../dotnet/priority-queue-container-type-stl-clr.md)