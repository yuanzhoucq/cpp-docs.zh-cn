---
title: "map::operator(STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator 成员 [] [STL/CLR]"
ms.assetid: 50e494c5-62d4-4469-8da3-7432ee4dff97
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# map::operator(STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

映射到键映射及其关联的值。  
  
## 语法  
  
```  
mapped_type operator[](key_type key);  
```  
  
#### 参数  
 键  
 要搜索的键值。  
  
## 备注  
 成员函数、查找具有等效的元素顺序为 `key`。  如果找到了一个对象，它返回关联映射值；否则，其插入 `value_type(``key``, mapped_type())` 并返回关联 \(默认\) 映射值。  使用它查找提供的映射的值关联的键，或者确保输入的键存在，如果没有找到。  
  
## 示例  
  
```  
// cliext_map_operator_sub.cpp   
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
  
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'A', c1[L'A']);   
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'b', c1[L'b']);   
  
// redisplay altered contents   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// alter mapped values and redisplay   
    c1[L'A'] = 10;   
    c1[L'c'] = 13;   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**c1\[A\] \= 0**  
**c1\[b\] \= 2**  
 **\[A 0\] \[a 1\] \[b 2\] \[c 3\]**  
 **\[A 10\] \[a 1\] \[b 2\] \[c 13\]**   
## 要求  
 **标头:** \<cliext\/map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [map](../dotnet/map-stl-clr.md)   
 [map::find](../dotnet/map-find-stl-clr.md)   
 [map::insert](../dotnet/map-insert-stl-clr.md)