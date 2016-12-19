---
title: "hash_multiset::load_factor (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::load_factor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "load_factor 成员 [STL/CLR]"
ms.assetid: 67125c97-1018-4d0f-858f-b4c09e7f0b09
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::load_factor (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对每个存储桶的平均元素数进行计数。  
  
## 语法  
  
```  
float load_factor();  
```  
  
## 备注  
 此成员函数返回 `(float)`[hash\_multiset::size](../dotnet/hash-multiset-size-stl-clr.md)`() /` [hash\_multiset::bucket\_count](../dotnet/hash-multiset-bucket-count-stl-clr.md)`()`。  使用它确定存储桶的平均大小。  
  
## 示例  
  
```  
// cliext_hash_multiset_load_factor.cpp   
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
  
  **a b c**  
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
 **Header:** \<cliext\/hash\_set\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::bucket\_count](../dotnet/hash-multiset-bucket-count-stl-clr.md)   
 [hash\_multiset::max\_load\_factor](../dotnet/hash-multiset-max-load-factor-stl-clr.md)