---
title: "map::insert (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成员 [STL/CLR]"
ms.assetid: 599c702e-7db0-45b8-8247-4ff041a3639c
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# map::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

添加元素。  
  
## 语法  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### 参数  
 first  
 插入范围的开头。  
  
 last  
 插入范围的末尾。  
  
 right  
 插入的枚举。  
  
 val  
 要插入的键值。  
  
 where  
 在插入的容器 \(仅\) 提示。  
  
## 备注  
 每个成员函数插入剩余操作数指定的顺序。  
  
 第一个成员函数竭力插入的值 `val`的元素，并返回一对值 `X`。  如果 `X.second` 为 true，则 `X.first` 指定新插入的元素；否则 `X.first` 指定一个具有等效顺序的现有元素，不插入新元素。  使用其插入一个元素。  
  
 第二个成员函数插入与值 `val`的元素，使用 `where` 作为提示 \(提高性能\) 和返回新指定插入元素的迭代器。  使用插入它可能靠近您知道元素周围的一个元素。  
  
 第三个成员函数将序列 `[``first``,` `last``)`。  将它粘贴从其他序列复制的零个或多个元素。  
  
 第四个成员函数 `right`插入选定的序列。  使用插入它枚举器描述的顺序。  
  
 每个元素需要插入时间比例。元素数为底的对数控制在序列中。  插入的常数在、时间发生，但是公开停靠将插入点周围的元素指定提示。  
  
## 示例  
  
```  
// cliext_map_insert.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_bool Pairib;   
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
  
// insert a single value, unique and duplicate   
// insert a single value, success and failure   
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    pair1 = c1.insert(Mymap::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    Mymap::iterator it =   
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymap c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymap c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Mymap::value_type>^)%c1);   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**insert\(\[L'x' 24\]\) \= \[\[x 24\] True\]**  
**insert\(\[L'b' 2\]\) \= \[\[b 2\] False\]**  
 **\[a 1\] \[b 2\] \[c 3\] \[x 24\]**  
**insert\(begin\(\), \[L'y' 25\]\) \= \[y 25\]**  
 **\[a 1\] \[b 2\] \[c 3\] \[x 24\] \[y 25\]**  
 **\[a 1\] \[b 2\] \[c 3\] \[x 24\]**  
 **\[a 1\] \[b 2\] \[c 3\] \[x 24\] \[y 25\]**   
## 要求  
 **标头:** \<cliext\/map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [map](../dotnet/map-stl-clr.md)