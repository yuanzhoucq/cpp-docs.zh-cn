---
title: "hash_set::iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "迭代器成员 [STL/CLR]"
ms.assetid: b75fc54f-6a9e-4ce8-a168-988afe7fe7e5
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

受控序列的迭代器的类型。  
  
## 语法  
  
```  
typedef T1 iterator;  
```  
  
## 备注  
 描述类型可以作为一双向迭代数。为控制序列未指定的 `T1` 类型的对象。  
  
## 示例  
  
```  
// cliext_hash_set_iterator.cpp   
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
    Myhash_set::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 要求  
 **页眉：** \<cliext\/hash\_set\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::const\_iterator](../dotnet/hash-set-const-iterator-stl-clr.md)