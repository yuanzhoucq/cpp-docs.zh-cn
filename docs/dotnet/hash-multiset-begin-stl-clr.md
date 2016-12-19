---
title: "hash_multiset::begin (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin 成员 [STL/CLR]"
ms.assetid: f03fc205-cbc9-4054-ac6d-41ad526edfea
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::begin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定受控序列的开头。  
  
## 语法  
  
```  
iterator begin();  
```  
  
## 备注  
 指定控件成员函数返回序列中的第一个元素的双向迭代器，或者除一个空序列的结尾。  用于获取一个迭代器，该迭代器指定受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。  
  
## 示例  
  
```  
// cliext_hash_multiset_begin.cpp   
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
  
// inspect first two items   
    Myhash_multiset::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*begin\(\) \=。**  
**\*\+\+begin\(\) \= b**   
## 要求  
 **页眉：** \<cliext\/hash\_set\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)