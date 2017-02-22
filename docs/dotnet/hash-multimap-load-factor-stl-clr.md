---
title: "hash_multimap::load_factor (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multimap::load_factor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "load_factor 成员 [STL/CLR]"
ms.assetid: c4b34387-fe76-405d-bead-a092b4571631
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# hash_multimap::load_factor (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计数、元素每个存储桶。  
  
## 语法  
  
```  
float load_factor();  
```  
  
## 备注  
 成员函数返回 `(float)`[hash\_multimap::size](../dotnet/hash-multimap-size-stl-clr.md)[hash\_multimap::bucket\_count](../dotnet/hash-multimap-bucket-count-stl-clr.md)`() /` `()`。  使用它、确定存储桶大小。  
  
## 示例  
  
```  
// cliext_hash_multimap_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1 = gcnew Myhash_multimap;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**bucket\_count\(\) \= 16**  
**load\_factor\(\) \= 0.1875**  
**max\_load\_factor\(\) \= 4**  
**bucket\_count\(\) \= 16**  
**load\_factor\(\) \= 0.1875**  
**max\_load\_factor\(\) \= 0.25**  
**bucket\_count\(\) \= 128**  
**load\_factor\(\) \= 0.0234375**  
**max\_load\_factor\(\) \= 0.25**   
## 要求  
 **页眉：** \<cliext\/hash\_map\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::bucket\_count](../dotnet/hash-multimap-bucket-count-stl-clr.md)   
 [hash\_multimap::max\_load\_factor](../dotnet/hash-multimap-max-load-factor-stl-clr.md)