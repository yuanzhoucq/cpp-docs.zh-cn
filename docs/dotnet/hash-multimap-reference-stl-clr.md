---
title: "hash_multimap::reference (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "引用成员 [STL/CLR]"
ms.assetid: 2f54e8d4-59c4-44ed-a059-881dba9d7d8e
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::reference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

元素的引用的类型。  
  
## 语法  
  
```  
typedef value_type% reference;  
```  
  
## 备注  
 此类型描述了一个对元素的引用。  
  
## 示例  
  
```  
// cliext_hash_multimap_reference.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Myhash_multimap::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Myhash_multimap::reference ref = *it;   
        System::Console::Write(" [{0} {1}]", ref->first, ref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**   
## 要求  
 **标头:** \<cliext\/hash\_map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::const\_reference](../dotnet/hash-multimap-const-reference-stl-clr.md)   
 [hash\_multimap::value\_type](../dotnet/hash-multimap-value-type-stl-clr.md)