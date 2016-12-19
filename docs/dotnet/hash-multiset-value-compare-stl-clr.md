---
title: "hash_multiset::value_compare (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::value_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_compare 成员 [STL/CLR]"
ms.assetid: 87f7df53-832b-4932-987b-1300943ad299
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::value_compare (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

两个元素值的排序委托。  
  
## 语法  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
## 备注  
 类型确定其排序值变量委托的同义词。  
  
## 示例  
  
```  
// cliext_hash_multiset_value_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **compare\(L'a', L'a'\) \= True**  
**compare\(L'a', L'b'\) \= True**  
**compare\(L'b', L'a'\) \= False**   
## 要求  
 **标头:** \<cliext\/hash\_set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::key\_compare](../dotnet/hash-multiset-key-compare-stl-clr.md)   
 [hash\_multiset::value\_comp](../dotnet/hash-multiset-value-comp-stl-clr.md)   
 [hash\_multiset::value\_type](../dotnet/hash-multiset-value-type-stl-clr.md)