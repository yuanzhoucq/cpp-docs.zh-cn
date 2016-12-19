---
title: "multimap::multimap (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multimap 成员 [STL/CLR]"
ms.assetid: cdf9c5dc-774c-424e-aeea-7554643e401c
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::multimap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
```  
multimap();  
explicit multimap(key_compare^ pred);  
multimap(multimap<Key, Mapped>% right);  
multimap(multimap<Key, Mapped>^ right);  
template<typename InIter>  
    multimapmultimap(InIter first, InIter last);  
template<typename InIter>  
    multimap(InIter first, InIter last,  
        key_compare^ pred);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `multimap();`  
  
 初始化控制序列没有元素，并且默认排序 `key_compare()`谓词。  使用它来指定空的初始序列，以控制默认排序谓词中。  
  
 构造函数：  
  
 `explicit multimap(key_compare^ pred);`  
  
 初始化控制序列没有元素，与顺序 `pred`的谓词。  使用该指定一个空控件，使用初始序列指定顺序匹配的谓词。  
  
 构造函数：  
  
 `multimap(multimap<Key, Mapped>% right);`  
  
 初始化与序列 `[``right``.``(),` `right``.`中的[multimap::end](../dotnet/multimap-end-stl-clr.md)[multimap::begin](../dotnet/multimap-begin-stl-clr.md)并且默认`())`的序列顺序控制，谓词。  使用指定它是控制 multimap 对象顺序复制由 `right`的初始序列，以控制默认排序谓词中。  
  
 构造函数：  
  
 `multimap(multimap<Key, Mapped>^ right);`  
  
 初始化与序列 `[``right``->``(),` `right``->`中的[multimap::end](../dotnet/multimap-end-stl-clr.md)[multimap::begin](../dotnet/multimap-begin-stl-clr.md)并且默认`())`的序列顺序控制，谓词。  使用指定它是控制 multimap 对象顺序复制由 `right`的初始序列，以控制默认排序谓词中。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `multimap(InIter first, InIter last);`  
  
 初始化与序列 `[``first``,` 并默认`last`的`)`的序列顺序控制，谓词。  使用会使控制序列复制另一个序列，其中包含默认排序谓词中。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `multimap(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 初始化与序列 `[``first``,` 。排序的谓词 `pred``last``)`的控制，序列。  使用会使控制序列复制其他序列，具有指定顺序的谓词。  
  
 构造函数：  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化时使用其默认的枚举数指定的顺序控制 `right`序列排序，谓词。  使用会使控制枚举数的序列描述复制另一个序列，其中包含默认排序谓词。  
  
 构造函数：  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化具有排序谓词的 `pred`枚举数指定的顺序控制序列，`right`。  使用会使控制枚举数的序列描述复制其他序列，具有指定顺序的谓词的。  
  
## 示例  
  
```  
// cliext_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
// construct an empty container   
    Mymultimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymultimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymultimap c3(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymultimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymultimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3);   
    for each (Mymultimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymultimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymultimap c7(c4);   
    for each (Mymultimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymultimap c8(%c3);   
    for each (Mymultimap::value_type elem in c8)   
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
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::generic\_container](../dotnet/multimap-generic-container-stl-clr.md)   
 [multimap::operator\=](../dotnet/multimap-operator-assign-stl-clr.md)