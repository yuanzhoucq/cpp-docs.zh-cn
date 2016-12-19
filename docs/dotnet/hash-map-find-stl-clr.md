---
title: "hash_map::find (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "find 成员 [STL/CLR]"
ms.assetid: 53ff8d57-2ea4-485e-9419-aed5e3f5affb
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::find (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找与指定键匹配的元素。  
  
## 语法  
  
```  
iterator find(key_type key);  
```  
  
#### 参数  
 键  
 要搜索的键值。  
  
## 备注  
 如果在控制序列的一个元素至少具有等效排序，使用 `key`成员函数返回指定这些元素之一的迭代器；否则返回`()`。[hash\_map::end](../dotnet/hash-map-end-stl-clr.md) 使用该属性当前设置一个元素位于与指定键的顺序控制。  
  
## 示例  
  
```  
// cliext_hash_map_find.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Myhash_map::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**查找 A \= false**  
**查找以 \= \[b 2\]**  
**查找 C\# 为错误**   
## 说明  
 请注意 `find` 不若干元素看起来的保证。  
  
## 要求  
 **标头:** \<cliext\/hash\_map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::equal\_range](../dotnet/hash-map-equal-range-stl-clr.md)   
 [hash\_map::lower\_bound](../dotnet/hash-map-lower-bound-stl-clr.md)   
 [hash\_map::upper\_bound](../dotnet/hash-map-upper-bound-stl-clr.md)