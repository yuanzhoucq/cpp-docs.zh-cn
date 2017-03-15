---
title: "hash_multimap::size (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multimap::size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size 成员 [STL/CLR]"
ms.assetid: 6937c980-5952-48bf-b411-81ab03b2f940
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# hash_multimap::size (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计算元素的数量。  
  
## 语法  
  
```  
size_type size();  
```  
  
## 备注  
 成员函数返回控制序列的长度。  使用其当前确定元素的数目。控制序列。  如果您关注的是序列是否具有非零大小，请参见 [hash\_multimap::empty](../dotnet/hash-multimap-empty-stl-clr.md)`()`。  
  
## 示例  
  
```  
// cliext_hash_multimap_size.cpp   
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
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Myhash_multimap::make_value(L'd', 4));   
    c1.insert(Myhash_multimap::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0之后清除**  
**size\(\) \= 2 在" 2 "之后**   
## 要求  
 **标头:** \<cliext\/hash\_map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::empty](../dotnet/hash-multimap-empty-stl-clr.md)