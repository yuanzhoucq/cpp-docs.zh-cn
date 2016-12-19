---
title: "hash_map::const_reverse_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::const_reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_reverse_iterator 成员 [STL/CLR]"
ms.assetid: 0c31131a-6eb6-4b14-bab9-ebc8ff25f414
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::const_reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这种类型的常量为受控序列存储迭代器。  
  
## 语法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
## 备注  
 描述类型可以作为常数的双向迭代数。为控制序列未指定的 `T4` 类型的对象。  
  
## 示例  
  
```  
// cliext_hash_map_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Myhash_map::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" [{0} {1}]", crit->first, crit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[c 3\] \[b 2\] \[a 1\]**   
## 要求  
 **标头:** \<cliext\/hash\_map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::reverse\_iterator](../dotnet/hash-map-reverse-iterator-stl-clr.md)