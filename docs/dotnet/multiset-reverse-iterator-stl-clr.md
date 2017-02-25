---
title: "multiset::reverse_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multiset::reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_iterator 成员 [STL/CLR]"
ms.assetid: dde6ad36-ca59-4728-aa53-e3d117eb4f48
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# multiset::reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一进行反向迭代器类型的控制的序列。  
  
## 语法  
  
```  
typedef T3 reverse_iterator;  
```  
  
## 备注  
 描述类型可用作一进行反向迭代数。为控制序列未指定的 `T3` 类型的对象。  
  
## 示例  
  
```  
// cliext_multiset_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Mymultiset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c b。**   
## 要求  
 **页眉：** \<cliext\/设置\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::const\_iterator](../dotnet/multiset-const-iterator-stl-clr.md)   
 [multiset::const\_reverse\_iterator](../dotnet/multiset-const-reverse-iterator-stl-clr.md)   
 [multiset::iterator](../dotnet/multiset-iterator-stl-clr.md)