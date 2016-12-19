---
title: "map::equal_range (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::equal_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "equal_range 成员 [STL/CLR]"
ms.assetid: c0d7409c-344d-4102-99c4-aeab8643a073
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::equal_range (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找数组与指定键的。  
  
## 语法  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### 参数  
 键  
 搜索的键值。  
  
## 备注  
 成员函数返回一对迭代器 `cliext::pair<iterator, iterator>(` [map::lower\_bound](../dotnet/map-lower-bound-stl-clr.md)[map::upper\_bound](../dotnet/map-upper-bound-stl-clr.md)`(``key``),` `(``key``))`。  使用它确定当前与指定键的范围控制元素在序列。  
  
## 示例  
  
```  
// cliext_map_equal_range.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_iter Pairii;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" [{0} {1}]",   
            pair1.first->first, pair1.first->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**equal\_range \(空\) L'x 为 True**  
 **\[b 2\]**   
## 要求  
 **页眉：** \<\/cliext 映射\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [map](../dotnet/map-stl-clr.md)   
 [map::count](../dotnet/map-count-stl-clr.md)   
 [map::find](../dotnet/map-find-stl-clr.md)   
 [map::lower\_bound](../dotnet/map-lower-bound-stl-clr.md)   
 [map::upper\_bound](../dotnet/map-upper-bound-stl-clr.md)