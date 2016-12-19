---
title: "hash_multiset::erase (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::erase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erase 成员 [STL/CLR]"
ms.assetid: bddd329d-aece-4b93-8355-005351c3aa45
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::erase (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除指定位置处的元素。  
  
## 语法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### 参数  
 首先  
 清除的范围开头。  
  
 键  
 清除的键值。  
  
 last  
 清除的范围末尾。  
  
 where  
 清除的元素。  
  
## 备注  
 第一移除成员函数控制序列的元素由 `where`指向，并返回指定保持了元素外的第一个元素。移除的迭代器，或者 [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`()`，如果不存在这样的元素。  使用它将删除一个元素。  
  
 第二个成员中移除函数控制元素在序列的范围的 `[``first``,` `last``)`，并返回指定保持超过所有元素外的第一个元素。移除的迭代器，或 `end()`，如果不存在这样的元素。  您移除它使用零个或更多连续的元素。  
  
 第三个成员函数移除键有等效排序到 `key`控件序列的所有元素，并返回元素的数目的计数中移除。  使用它、移除和计数与指定键的所有元素。  
  
 每个元素抹除需要时间比例。元素数为底的对数控制在序列中。  
  
## 示例  
  
```  
// cliext_hash_multiset_erase.cpp   
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
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myhash_multiset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**erase\(begin\(\)\= b\)**  
 **b 和 c d**  
**erase\(begin\(\)，end\(\)e \= \-1\)**  
**size\(\) \= 1**   
## 要求  
 **页眉：** \<cliext\/hash\_set\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::clear](../dotnet/hash-multiset-clear-stl-clr.md)