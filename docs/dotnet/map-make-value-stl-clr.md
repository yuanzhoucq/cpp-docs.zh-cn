---
title: "map::make_value (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::make_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_value 成员 [STL/CLR]"
ms.assetid: a0bc4081-b8b7-450e-b041-a49ac42b279f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# map::make_value (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造一个值对象。  
  
## 语法  
  
```  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### 参数  
 键  
 可以使用的键值。  
  
 已映射  
 要搜索的映射值。  
  
## 备注  
 成员函数返回键值是 `key`，映射值为 `mapped`的 `value_type` 对象。  使用它创建一个适合其他成员函数使用的对象。  
  
## 示例  
  
```  
// cliext_map_make_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
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
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**   
## 要求  
 **标头:** \<cliext\/map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [map](../dotnet/map-stl-clr.md)   
 [map::key\_type](../dotnet/map-key-type-stl-clr.md)   
 [map::mapped\_type](../dotnet/map-mapped-type-stl-clr.md)   
 [map::value\_type](../dotnet/map-value-type-stl-clr.md)