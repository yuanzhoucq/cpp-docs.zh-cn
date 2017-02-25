---
title: "multimap::count (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::count"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "count 成员 [STL/CLR]"
ms.assetid: f8e3700c-b968-4ab0-86f1-d4ae7d9e0093
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# multimap::count (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查看与指定键的元素的数目。  
  
## 语法  
  
```  
size_type count(key_type key);  
```  
  
#### 参数  
 键  
 搜索的键值。  
  
## 备注  
 成员函数返回具有相同订单的 `key`元素的数目控制在序列中。  用于确定受控序列中当前与指定键匹配的元素数。  
  
## 示例  
  
```  
// cliext_multimap_count.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**计数 \(L'A\)\/0**  
**计数 \(L'b\)\/1**  
**计数 \(L'C\)\/0**   
## 要求  
 **页眉：** \<\/cliext 映射\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::equal\_range](../dotnet/multimap-equal-range-stl-clr.md)