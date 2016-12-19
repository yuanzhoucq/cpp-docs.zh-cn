---
title: "set::to_array (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::to_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "to_array 成员 [STL/CLR]"
ms.assetid: 62ee03ce-5bf0-4235-9835-8b77929702c9
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::to_array (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

复制控制序列到新数组。  
  
## 语法  
  
```  
cli::array<value_type>^ to_array();  
```  
  
## 备注  
 成员函数返回包含一控制序列的数组。  使用它获得数组窗体中的一个控制序列副本。  
  
## 示例  
  
```  
// cliext_set_to_array.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c d**  
 **a b c**   
## 要求  
 **标头:** \<cliext\/set\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [集合](../dotnet/set-stl-clr.md)