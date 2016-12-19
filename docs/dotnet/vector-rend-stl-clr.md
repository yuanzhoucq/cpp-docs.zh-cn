---
title: "vector::rend (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::rend"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rend 成员 [STL/CLR]"
ms.assetid: 8dc1927f-9214-468d-877e-eda20c03e90d
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::rend (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定反转的受控序列的末尾。  
  
## 语法  
  
```  
reverse_iterator rend();  
```  
  
## 备注  
 该成员函数返回一个反向迭代器，指向刚刚超越控制序列的开头。  因此，它指定反向序列的 `end`。  用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 末尾，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。  
  
## 示例  
  
```  
// cliext_vector_rend.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*\-\- \-\-rend\(\) \= b**  
**\*\-\-rend\(\) \= a**  
 **y x c**   
## 要求  
 **标头:** \<cliext\/vector\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::begin](../dotnet/vector-begin-stl-clr.md)   
 [vector::end](../dotnet/vector-end-stl-clr.md)   
 [vector::rbegin](../dotnet/vector-rbegin-stl-clr.md)