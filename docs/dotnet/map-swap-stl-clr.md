---
title: "map::swap (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap 成员 [STL/CLR]"
ms.assetid: b36ed982-21ce-40e5-9636-ecdbaf1b7eec
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

交换两个容器的内容。  
  
## 语法  
  
```  
void swap(map<Key, Mapped>% right);  
```  
  
#### 参数  
 right  
 要与其交换内容的容器。  
  
## 备注  
 成员函数将交换了 `this` 和 `right`之间的控制序列。  在常数的时间来实现，且不引发异常。  将它用作一种快速交换两个内容容器。  
  
## 示例  
  
```  
// cliext_map_swap.cpp   
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
  
// construct another container with repetition of values   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'd', 4));   
    c2.insert(Mymap::make_value(L'e', 5));   
    c2.insert(Mymap::make_value(L'f', 6));   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
 **\[、\] 和 \[4 5\] \[f 6\]**  
 **\[、\] 和 \[4 5\] \[f 6\]**  
 **\[a 1\] \[b 2\] \[c 3\]**   
## 要求  
 **页眉：** \<\/cliext 映射\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [map](../dotnet/map-stl-clr.md)   
 [map::operator\=](../dotnet/map-operator-assign-stl-clr.md)