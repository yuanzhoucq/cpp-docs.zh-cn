---
title: "multiset::insert (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multiset::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成员 [STL/CLR]"
ms.assetid: 7a3b1cc8-ec60-4ed0-ace5-46cb5872e6e7
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# multiset::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

添加元素。  
  
## 语法  
  
```  
iterator insert(value_type val);  
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
  
 第一个成员函数插入值`val`的元素，并返回指定新插入的元素的迭代器。  使用其插入一个元素。  
  
 第二个成员函数插入与值 `val`的元素，使用 `where` 作为提示 \(提高性能\) 和返回新指定插入元素的迭代器。  使用插入它可能靠近您知道元素周围的一个元素。  
  
 第三个成员函数将序列 `[``first``,` `last``)`。  将它粘贴从其他序列复制的零个或多个元素。  
  
 第四个成员函数 `right`插入选定的序列。  使用插入它枚举器描述的顺序。  
  
 每个元素需要插入时间比例。元素数为底的对数控制在序列中。  插入的常数在、时间发生，但是公开停靠将插入点周围的元素指定提示。  
  
## 示例  
  
```  
// cliext_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymultiset c2;   
    Mymultiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymultiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**insert\(L'x'\) \= x**  
**insert\(L'b'\) \= b**  
 **a b b c x**  
**insert\(begin\(\), L'y'\) \= y**  
 **a b b c x y**  
 **a b b c x**  
 **a b b c x y**   
## 要求  
 **标头:** \<cliext\/set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [multiset](../dotnet/multiset-stl-clr.md)