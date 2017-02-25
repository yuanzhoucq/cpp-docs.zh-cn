---
title: "list::clear (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::clear"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clear 成员 [STL/CLR]"
ms.assetid: 5aac9a64-52f6-4a73-8b24-e30ceedcbc20
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# list::clear (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除所有元素。  
  
## 语法  
  
```  
void clear();  
```  
  
## 备注  
 成员函数中有效调用 [list::erase](../dotnet/list-erase-stl-clr.md)[list::begin](../dotnet/list-begin-stl-clr.md)[list::end](../dotnet/list-end-stl-clr.md)`(` `(),` `())`。  用以确保控制序列为空。  
  
## 示例  
  
```  
// cliext_list_clear.cpp   
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
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size\(\) \= 0**  
 **a b**  
**size\(\) \= 0**   
## 要求  
 **标头:** \<cliext\/list\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::erase](../dotnet/list-erase-stl-clr.md)