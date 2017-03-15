---
title: "map::map (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "map 成员 [STL/CLR]"
ms.assetid: c91f699a-4742-4859-b2b3-c2a01a750bea
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# map::map (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
```  
map();  
explicit map(key_compare^ pred);  
map(map<Key, Mapped>% right);  
map(map<Key, Mapped>^ right);  
template<typename InIter>  
    mapmap(InIter first, InIter last);  
template<typename InIter>  
    map(InIter first, InIter last,  
        key_compare^ pred);  
map(System::Collections::Generic::IEnumerable<GValue>^ right);  
map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### 参数  
 首先  
 插入范围的开头。  
  
 last  
 插入的范围末尾。  
  
 pred  
 排序规则序列的谓词。  
  
 right  
 插入的对象或值范围。  
  
## 备注  
 构造函数：  
  
 `map();`  
  
 初始化控制序列没有元素，并且默认排序 `key_compare()`谓词。  使用它来指定空的初始序列，以控制默认排序谓词中。  
  
 构造函数：  
  
 `explicit map(key_compare^ pred);`  
  
 初始化控制序列没有元素，与顺序 `pred`的谓词。  使用该指定一个空控件，使用初始序列指定顺序匹配的谓词。  
  
 构造函数：  
  
 `map(map<Key, Mapped>% right);`  
  
 初始化与序列 `[``right``.``(),` `right``.`中的[map::end](../dotnet/map-end-stl-clr.md)[map::begin](../dotnet/map-begin-stl-clr.md)并且默认`())`的序列顺序控制，谓词。  使用指定它是顺序控制由映射复制对象 `right`的初始序列，以控制默认排序谓词中。  
  
 构造函数：  
  
 `map(map<Key, Mapped>^ right);`  
  
 初始化与序列 `[``right``->``(),` `right``->`中的[map::end](../dotnet/map-end-stl-clr.md)[map::begin](../dotnet/map-begin-stl-clr.md)并且默认`())`的序列顺序控制，谓词。  使用指定它是顺序控制由映射复制对象 `right`的初始序列，以控制默认排序谓词中。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `map(InIter first, InIter last);`  
  
 初始化与序列 `[``first``,` 并默认`last`的`)`的序列顺序控制，谓词。  使用会使控制序列复制另一个序列，其中包含默认排序谓词中。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `map(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 初始化与序列 `[``first``,` 。排序的谓词 `pred``last``)`的控制，序列。  使用会使控制序列复制其他序列，具有指定顺序的谓词。  
  
 构造函数：  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化时使用其默认的枚举数指定的顺序控制 `right`序列排序，谓词。  使用会使控制枚举数的序列描述复制另一个序列，其中包含默认排序谓词。  
  
 构造函数：  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化具有排序谓词的 `pred`枚举数指定的顺序控制序列，`right`。  使用会使控制枚举数的序列描述复制其他序列，具有指定顺序的谓词的。  
  
## 示例  
  
```  
// cliext_map_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
// construct an empty container   
    Mymap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymap c3(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3);   
    for each (Mymap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymap c7(c4);   
    for each (Mymap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymap c8(%c3);   
    for each (Mymap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **\[a 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[a 1\] \[b 2\] \[c 3\]**   
## 要求  
 **页眉：** \<\/cliext 映射\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [map](../dotnet/map-stl-clr.md)   
 [map::generic\_container](../dotnet/map-generic-container-stl-clr.md)   
 [map::operator\=](../dotnet/map-operator-assign-stl-clr.md)