---
title: "hash_multiset::equal_range (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::equal_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "equal_range 成员 [STL/CLR]"
ms.assetid: a4141d7e-4964-4c78-8989-ae1d1258b50a
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::equal_range (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找与指定键匹配的范围。  
  
## 语法  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### 参数  
 键  
 要搜索的键值。  
  
## 备注  
 成员函数返回一对迭代器 `cliext::pair<iterator, iterator>(` [hash\_multiset::lower\_bound](../dotnet/hash-multiset-lower-bound-stl-clr.md)[hash\_multiset::upper\_bound](../dotnet/hash-multiset-upper-bound-stl-clr.md)`(``key``),` `(``key``))`。  可以使用它来确定当前受控序列中与指定键匹配的元素范围。  
  
## 示例  
  
```  
// cliext_hash_multiset_equal_range.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
typedef Myhash_multiset::pair_iter_iter Pairii;   
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
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**equal\_range\(L'x'\) empty \= True**  
 **b**   
## 要求  
 **标头:** \<cliext\/hash\_set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::count](../dotnet/hash-multiset-count-stl-clr.md)   
 [hash\_multiset::find](../dotnet/hash-multiset-find-stl-clr.md)   
 [hash\_multiset::lower\_bound](../dotnet/hash-multiset-lower-bound-stl-clr.md)   
 [hash\_multiset::upper\_bound](../dotnet/hash-multiset-upper-bound-stl-clr.md)