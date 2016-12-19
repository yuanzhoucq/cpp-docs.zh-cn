---
title: "operator&gt;= (list) (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator>= 成员 [STL/CLR]"
ms.assetid: c6142241-8e85-4759-98fd-4f2b7d37b255
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&gt;= (list) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大列表比或等于比较。  
  
## 语法  
  
```  
template<typename Value>  
    bool operator>=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### 参数  
 left  
 比较的容器。  
  
 right  
 比较的正确的容器。  
  
## 备注  
 运算符函数返回 `!(``left` `<` `right``)`。  您可用它测试 `left` 是否没有 `right` 之前排序，当两列表是比较的元素由元素。  
  
## 示例  
  
```  
// cliext_list_operator_ge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a bc d**  
**\[a b c\] \>\= \[a b c\] 为 true 为 c**  
**\[a b c\] \>\= \[a b d\] 为 b 的错误**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [operator\=\= \(list\)](../dotnet/operator-equality-list-stl-clr.md)   
 [operator\!\= \(list\)](../dotnet/operator-inequality-list-stl-clr.md)   
 [operator\< \(list\)](../dotnet/operator-less-than-list-stl-clr.md)   
 [operator\> \(list\)](../dotnet/operator-greater-than-list-stl-clr.md)   
 [operator\<\= \(list\)](../dotnet/operator-less-or-equal-list-stl-clr.md)