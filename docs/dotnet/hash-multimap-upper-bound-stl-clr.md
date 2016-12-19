---
title: "hash_multimap::upper_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "upper_bound 成员 [STL/CLR]"
ms.assetid: 4fa58df6-63ec-411d-bcf9-301d3c88569a
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找与指定键匹配的范围。  
  
## 语法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### 参数  
 键  
 要搜索的键值。  
  
## 备注  
 成员函数确定受控序列中可散列为与 `key` 相同的存储桶并具有与 `key` 等效的顺序的第一个元素`X`。  如果不存在此类元素，或者，如果 `X` 位于控制序列中的最后一个元素，则返回`()`; [hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)否则它返回指定除 `X`外的第一个元素的次数的迭代器。  使用其当前找到的元素序列的开头与指定的键在控制序列。  
  
## 示例  
  
```  
// cliext_hash_multimap_upper_bound.cpp   
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
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Myhash_multimap::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**upper\_bound\(L'x'\)\=\=end\(\) \= True**  
**\*upper\_bound\(L'a'\) \= \[b 2\]**  
**\*upper\_bound\(L'b'\) \= \[c 3\]**   
## 要求  
 **标头:** \<cliext\/hash\_map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::count](../dotnet/hash-multimap-count-stl-clr.md)   
 [hash\_multimap::equal\_range](../dotnet/hash-multimap-equal-range-stl-clr.md)   
 [hash\_multimap::find](../dotnet/hash-multimap-find-stl-clr.md)   
 [hash\_multimap::lower\_bound](../dotnet/hash-multimap-lower-bound-stl-clr.md)