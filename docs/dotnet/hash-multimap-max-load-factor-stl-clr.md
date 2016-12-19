---
title: "hash_multimap::max_load_factor (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::max_load_factor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_load_factor 成员 [STL/CLR]"
ms.assetid: acea6293-9c6f-4c5e-a9a3-998e755ba1fd
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::max_load_factor (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取或设置每个存储桶的最多元素数。  
  
## 语法  
  
```  
float max_load_factor();  
void max_load_factor(float new_factor);  
```  
  
#### 参数  
 new\_factor  
 存储的新最大负载以便因素。  
  
## 备注  
 第一个成员函数返回存储的最大负载因素。  使用它确定存储桶大小。  
  
 第二个成员函数用 `new_factor`替换存储最大负载以便因素。  不会改作的发生之前后续插入。  
  
## 示例  
  
```  
// cliext_hash_multimap_max_load_factor.cpp   
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
 **标头:** \<cliext\/hash\_map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::bucket\_count](../dotnet/hash-multimap-bucket-count-stl-clr.md)   
 [hash\_multimap::load\_factor](../dotnet/hash-multimap-load-factor-stl-clr.md)   
 [hash\_multimap::rehash](../dotnet/hash-multimap-rehash-stl-clr.md)