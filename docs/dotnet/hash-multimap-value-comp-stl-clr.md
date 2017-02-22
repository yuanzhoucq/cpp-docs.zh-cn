---
title: "hash_multimap::value_comp (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multimap::value_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_comp 成员 [STL/CLR]"
ms.assetid: ec6108b8-a529-499b-bc7f-dce41f5b6175
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# hash_multimap::value_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

复制两个元素值排序的委托。  
  
## 语法  
  
```  
value_compare^ value_comp();  
```  
  
## 备注  
 成员函数返回 Orders 的委托用于控制对的序列。  使用此规则可以比较两个元素值。  
  
## 示例  
  
```  
// cliext_hash_multimap_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    Myhash_multimap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Myhash_multimap::make_value(L'a', 1),   
            Myhash_multimap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Myhash_multimap::make_value(L'a', 1),   
            Myhash_multimap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Myhash_multimap::make_value(L'b', 2),   
            Myhash_multimap::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **比较 \(\[L'a，1\]，\[L'a，1\]\) \= true**  
**比较 \(\[L'a，1\]，\[L'b，2\]\) \= true**  
**比较 \(\[L'b，2\]，\[L'a，1\]\) \= false**   
## 要求  
 **页眉：** \<cliext\/hash\_map\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::value\_compare](../dotnet/hash-multimap-value-compare-stl-clr.md)   
 [hash\_multimap::value\_type](../dotnet/hash-multimap-value-type-stl-clr.md)