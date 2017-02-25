---
title: "hash_set::generic_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_set::generic_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic_iterator 成员 [STL/CLR]"
ms.assetid: 9d6ac06d-d70c-4343-b959-553885a9cb53
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# hash_set::generic_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

与容器的泛型接口一起使用的迭代器的类型。  
  
## 语法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
## 备注  
 此类型描述了一个泛型迭代器，此迭代器可以与模板类的泛型接口一同使用。  
  
## 示例  
  
```  
// cliext_hash_set_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_set::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_set::generic_iterator gcit = gc1->begin();   
    Myhash_set::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**  
 **a**   
## 要求  
 **标头:** \<cliext\/hash\_set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::generic\_container](../dotnet/hash-set-generic-container-stl-clr.md)