---
title: "multimap::clear (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::clear"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clear 成员 [STL/CLR]"
ms.assetid: 2c4aae4b-0aac-42ba-abf4-eaf2d5734817
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# multimap::clear (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除所有元素。  
  
## 语法  
  
```  
void clear();  
```  
  
## 备注  
 成员函数中有效调用 [multimap::erase](../dotnet/multimap-erase-stl-clr.md)[multimap::begin](../dotnet/multimap-begin-stl-clr.md)[multimap::end](../dotnet/multimap-end-stl-clr.md)`(` `(),` `())`。  用以确保控制序列为空。  
  
## 示例  
  
```  
// cliext_multimap_clear.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
  
// display contents " [a 1] [b 2]"   
    for each (Mymultimap::value_type elem in c1)   
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
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::erase](../dotnet/multimap-erase-stl-clr.md)