---
title: "priority_queue::priority_queue (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "priority_queue 成员 [STL/CLR]"
ms.assetid: aab423d7-959e-48fd-9028-e9f45f43cb8a
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::priority_queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
```  
priority_queue();  
priority_queue(priority_queue<Value, Container> right);  
priority_queue(priority_queue<Value, Container> right);  
explicit priority_queue(value_compare^ pred);  
priority_queue(value_compare^ pred, container_type% cont);  
template<typename InIt>  
    priority_queue(InIt first, InIt last);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred, container_type% cont);  
```  
  
#### 参数  
 继续  
 容器复制。  
  
 first  
 插入范围的开头。  
  
 last  
 插入范围的末尾。  
  
 pred  
 排序规则序列的谓词。  
  
 right  
 要插入的对象或范围。  
  
## 备注  
 构造函数：  
  
 `priority_queue();`  
  
 创建空的包装的容器，含有默认排序谓词。  使用它来指定空的初始序列，使用控制默认排序谓词。  
  
 构造函数：  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 创建 `right.get_container()`复制的包装的容器，具有排序谓词的 `right.value_comp()`。  可以使用它来指定初始化的控制序列，该序列是由该集对象`right`控制序列的副本并使用默认的排序谓词。  
  
 构造函数：  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 创建 `right->get_container()`复制的包装的容器，具有排序谓词的 `right->value_comp()`。  可以使用它来指定初始化的控制序列，该序列是由该集对象`*right`控制序列的副本并使用默认的排序谓词。  
  
 构造函数：  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 创建空的包装的容器，含有默认排序谓词`pred`。  使用它来指定空的初始序列，使用指定的默认排序谓词。  
  
 构造函数：  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 创建空的包装的容器，具有排序谓词的 `pred`，然后按下要使用它指定从现有容器的初始序列 `cont` 控制的所有元素，具有指定顺序的谓词。  
  
 构造函数：  
  
 `template<typename InIt>`  
  
 `priority_queue(InIt first, InIt last);`  
  
 创建空的包装的容器，含有默认排序谓词，然后按下序列 `[``first``,` `last``)`。  使用它指定从一个指定的 eqeuence 的初始序列控件，具有指定顺序的谓词。  
  
 构造函数：  
  
 `template<typename InIt>`  
  
 `priority_queue(InIt first, InIt last,`  
  
 `value_compare^ pred);`  
  
 创建空的包装的容器，含有默认排序谓词`pred`，然后按下序列 `[``first``,` `last``)`。  使用它指定从一个指定的 eqeuence 的初始序列控件，具有指定顺序的谓词。  
  
 构造函数：  
  
 `template<typename InIt>`  
  
 `priority_queue(InIt first, InIt last,`  
  
 `value_compare^ pred, container_type% cont);`  
  
 创建空的包装的容器，具有排序谓词的 `pred`，然后按下 `cont` 的所有元素和序列 `[``first``,` `last``)`。  使用它指定从现有的容器和指定的 seqeuence 的初始序列控件，具有指定顺序的谓词。  
  
## 示例  
  
```  
// cliext_priority_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/deque>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
typedef cliext::deque<wchar_t> Mydeque;   
int main()   
    {   
// construct an empty container   
    Mypriority_queue c1;   
    Mypriority_queue::container_type^ wc1 = c1.get_container();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **c a b**  
**size\(\) \= 0**  
 **a c b**  
 **a c b**  
 **c a b**  
 **a c b**  
 **a a b c c b**  
 **c a b**  
 **c a b**  
 **a c b**   
## 要求  
 **标头:** \<cliext\/queue\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::assign](../dotnet/priority-queue-assign-stl-clr.md)   
 [priority\_queue::generic\_container](../dotnet/priority-queue-generic-container-stl-clr.md)   
 [priority\_queue::operator\=](../dotnet/priority-queue-operator-assign-stl-clr.md)