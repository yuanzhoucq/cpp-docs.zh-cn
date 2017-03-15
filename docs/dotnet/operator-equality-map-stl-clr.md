---
title: "operator== (map) (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator== 成员 [STL/CLR]"
ms.assetid: 6f7672af-71f8-4086-ac42-173203e52951
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator== (map) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列出相等比较。  
  
## 语法  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator==(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### 参数  
 left  
 比较左边的容器。  
  
 right  
 比较右边的容器。  
  
## 备注  
 当由 `left` 和 `right` 控制的顺序具有相同长度，并且，对每个位置 `i`，`left``[i] ==` `right``[i]`，该运算符函数返回 true。  当一个个元素地比较两个集合时，您可以用它测试 `left` 是否和 `right` 排序一样。  
  
## 示例  
  
```  
// cliext_map_operator_eq.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[d 4\]**  
**\[a b c\] \=\= \[a b c\] 为True**  
**\[a b c\] \=\= \[a b d\] 为 False**   
## 要求  
 **标头:** \<cliext\/map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [map](../dotnet/map-stl-clr.md)   
 [operator\!\= \(map\)](../dotnet/operator-inequality-map-stl-clr.md)   
 [operator\< \(map\)](../dotnet/operator-less-than-map-stl-clr.md)   
 [operator\>\= \(map\)](../dotnet/operator-greater-or-equal-map-stl-clr.md)   
 [operator\> \(map\)](../dotnet/operator-greater-than-map-stl-clr.md)   
 [operator\<\= \(map\)](../dotnet/operator-less-or-equal-map-stl-clr.md)