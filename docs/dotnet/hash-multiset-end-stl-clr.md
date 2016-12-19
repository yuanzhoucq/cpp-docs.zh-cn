---
title: "hash_multiset::end (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "end 成员 [STL/CLR]"
ms.assetid: 6f4b222c-2f82-445e-80e5-6e2afd233d4b
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::end (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定受控序列的末尾。  
  
## 语法  
  
```  
iterator end();  
```  
  
## 备注  
 该成员函数返回一个双向迭代器，指向刚刚超越控制序列的末尾。  用于获取一个迭代器，该迭代器指定受控序列的末尾，但如果受控序列的长度发生更改，则该迭代器的状态也不会发生更改。  
  
## 示例  
  
```  
// cliext_hash_multiset_end.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myhash_multiset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*\-\- \-\-end\(\) \= b**  
**\*\-\-end\(\) \= c**   
## 要求  
 **标头:** \<cliext\/hash\_set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)