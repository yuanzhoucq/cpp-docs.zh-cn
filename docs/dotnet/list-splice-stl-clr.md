---
title: "list::splice (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::splice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "splice 成员 [STL/CLR]"
ms.assetid: ebc424b9-8341-4a88-b101-86d56324f5ac
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# list::splice (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

节点之间的 Restitch 链接。  
  
## 语法  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### 参数  
 首先  
 交错范围的开头。  
  
 last  
 接合范围末尾。  
  
 right  
 拼接的容器中。  
  
 where  
 在前面带锯齿的容器。  
  
## 备注  
 第一个成员函数插入顺序控制由 `right` 控制在序列的元素之前指向的 `where`。  它从 `right`中移除所有元素。\(无法等于`%``right``this`。\)使用该耦合整个列表到另一个。  
  
 第二个成员函数中移除元素指向按顺序控制的 `first` 由 `right` 和控制在序列的元素之前插入它指向的 `where`。\(如果 `where` `==` `first` `||` `where` `== ++``first`，则发生更改。\)使用该耦合一个列表的唯一元素到另一个。  
  
 第三个 `[`成员函数插入选定的子范围`first``,` 中的`last`控制`)` 顺序由 `right` 控制在序列的元素之前指向的 `where`。  它还移除从原始顺序控制指定子范围的 `right`。\(如果 `right` `==` `this`，范围 `[``first``,` `last``)` 不包含元素指向的 `where`。\)使用该耦合零个或多个元素 subsequence 从一个列表中为另一个中。  
  
## 示例  
  
```  
// cliext_list_splice.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**c1.size\(\) \= 0**  
 **a b c**  
 **a**  
 **为 c**  
 **b c。**  
**c2.size\(\) \= 0**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::assign](../dotnet/list-assign-stl-clr.md)   
 [list::insert](../dotnet/list-insert-stl-clr.md)   
 [list::merge](../dotnet/list-merge-stl-clr.md)