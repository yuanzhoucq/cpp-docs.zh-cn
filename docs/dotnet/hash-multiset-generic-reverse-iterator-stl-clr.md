---
title: "hash_multiset::generic_reverse_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::generic_reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic_reverse_iterator 成员 [STL/CLR]"
ms.assetid: cd921563-3ab1-428e-8f0c-82e3f0aa1a5e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# hash_multiset::generic_reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一进行反向迭代器的类型用于泛型接口的容器使用的。  
  
## 语法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
## 备注  
 类型描述可以使用泛型接口。此模板容器类的一个泛反向迭代器。  
  
## 示例  
  
```  
// cliext_hash_multiset_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_reverse_iterator gcit = gc1->rbegin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**  
 **c**   
## 要求  
 **页眉：** \<cliext\/hash\_set\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::generic\_container](../dotnet/hash-multiset-generic-container-stl-clr.md)   
 [hash\_multiset::generic\_iterator](../dotnet/hash-multiset-generic-iterator-stl-clr.md)