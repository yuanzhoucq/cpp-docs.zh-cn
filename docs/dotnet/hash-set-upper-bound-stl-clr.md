---
title: "hash_set::upper_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_set::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "upper_bound 成员 [STL/CLR]"
ms.assetid: dc8815f1-8b45-4f3d-a51f-54050d434d8f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# hash_set::upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找与指定的键范围的末尾。  
  
## 语法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### 参数  
 键  
 搜索的键值。  
  
## 备注  
 成员函数确定。散列为存储桶与 `key` 相同并且具有相同订单给 `key`的控制序列中的最后一个 `X`。  如果不存在此类元素，或者，如果 `X` 位于控制序列中的最后一个元素，则返回`()`; [hash\_set::end](../dotnet/hash-set-end-stl-clr.md)否则它返回指定除 `X`外的第一个元素的次数的迭代器。  使用其当前找到的元素序列的末尾与指定的键在控制序列。  
  
## 示例  
  
```  
// cliext_hash_set_upper_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
  **a b c**  
**upper\_bound\(L'x'\)\=\=end\(\) 为 True**  
**\*upper\_bound \(L'a \= b\)**  
**\*upper\_bound \(\=\) L'b c**   
## 要求  
 **页眉：** \<cliext\/hash\_set\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::count](../dotnet/hash-set-count-stl-clr.md)   
 [hash\_set::equal\_range](../dotnet/hash-set-equal-range-stl-clr.md)   
 [hash\_set::find](../dotnet/hash-set-find-stl-clr.md)   
 [hash\_set::lower\_bound](../dotnet/hash-set-lower-bound-stl-clr.md)