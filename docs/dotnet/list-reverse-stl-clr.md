---
title: "list::reverse (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::reverse"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse 成员 [STL/CLR]"
ms.assetid: de3bce1e-01fe-461d-a785-5cf4fcea988f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# list::reverse (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

撤消控制序列。  
  
## 语法  
  
```  
void reverse();  
```  
  
## 备注  
 成员函数同时撤消所有元素在序列的控制。  使用它反映元素的列表。  
  
## 示例  
  
```  
// cliext_list_reverse.cpp   
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
  
// reverse and redisplay   
    c1.reverse();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **c b。**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::sort](../dotnet/list-sort-stl-clr.md)