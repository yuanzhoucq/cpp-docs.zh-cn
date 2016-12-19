---
title: "queue::queue (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "队列成员 [STL/CLR]"
ms.assetid: 6106c07f-d5eb-4f0b-82df-ee4e2e751047
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue::queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
```  
queue();  
queue(queue<Value, Container>% right);  
queue(queue<Value, Container>^ right);  
explicit queue(container_type% wrapped);  
```  
  
#### 参数  
 right  
 要复制的对象。  
  
 包装  
 使用包装的容器。  
  
## 备注  
 构造函数：  
  
 `queue();`  
  
 创建空的包装的容器。  可以使用它来指定空的初始序列控制。  
  
 构造函数：  
  
 `queue(queue<Value, Container>% right);`  
  
 创建 `right.get_container()`复制的包装的容器。  将它指定为复制顺序控制是由队列对象 `right`的初始序列控制。  
  
 构造函数：  
  
 `queue(queue<Value, Container>^ right);`  
  
 创建 `right->get_container()`复制的包装的容器。  将它指定为复制顺序控制是由队列对象 `*right`的初始序列控制。  
  
 构造函数：  
  
 `explicit queue(container_type wrapped);`  
  
 使用现有 `wrapped` 容器作为包装的容器。  使用该构造从现有容器的队列。  
  
## 示例  
  
```  
// cliext_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/list>   
  
typedef cliext::queue<wchar_t> Myqueue;   
typedef cliext::list<wchar_t> Mylist;   
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;   
int main()   
    {   
// construct an empty container   
    Myqueue c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Mylist v2(5, L'x');   
    Myqueue_list c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myqueue_list c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Myqueue_list c4(%c2);   
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
 **标头:** \<cliext\/queue\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::assign](../dotnet/queue-assign-stl-clr.md)   
 [queue::generic\_container](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::operator\=](../dotnet/queue-operator-assign-stl-clr.md)