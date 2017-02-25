---
title: "list::const_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::const_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_iterator 成员 [STL/CLR]"
ms.assetid: 24e19077-02d2-456e-a3f1-7caaf0b6c974
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# list::const_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

受控序列的常量迭代器的类型。  
  
## 语法  
  
```  
typedef T2 const_iterator;  
```  
  
## 备注  
 描述类型可以作为常数的双向迭代数，为控制序列未指定的 `T2` 类型的对象。  
  
## 示例  
  
```  
// cliext_list_const_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 要求  
 **标头:** \<cliext\/list\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::iterator](../dotnet/list-iterator-stl-clr.md)