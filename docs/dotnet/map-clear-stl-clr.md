---
title: "map::clear (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::clear"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clear 成员 [STL/CLR]"
ms.assetid: 2a6a01fe-2998-447d-9ae8-6cb6343d0dfa
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# map::clear (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除所有元素。  
  
## 语法  
  
```  
void clear();  
```  
  
## 备注  
 成员函数中有效调用 [map::erase](../dotnet/map-erase-stl-clr.md)[map::begin](../dotnet/map-begin-stl-clr.md)[map::end](../dotnet/map-end-stl-clr.md)`(` `(),` `())`。  用以确保控制序列为空。  
  
## 示例  
  
```  
// cliext_map_clear.cpp   
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
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
  
// display contents " [a 1] [b 2]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0**  
 **\[a 1\] \[b 2\]**  
**size\(\) \= 0**   
## 要求  
 **标头:** \<cliext\/map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [map](../dotnet/map-stl-clr.md)   
 [map::erase](../dotnet/map-erase-stl-clr.md)