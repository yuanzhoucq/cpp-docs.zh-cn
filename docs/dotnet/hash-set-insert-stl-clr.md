---
title: "hash_set::insert (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成员 [STL/CLR]"
ms.assetid: 0a9bc9aa-012e-4101-9e8c-f1f4b6b76af7
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::insert (STL/CLR)
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
 首先  
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
// cliext_hash_set_insert.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
typedef Myhash_set::pair_iter_bool Pairib;   
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
  
// insert a single value, unique and duplicate   
    Pairib pair1 = c1.insert(L'x');   
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    pair1 = c1.insert(L'b');   
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
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
    Myhash_set c2;   
    Myhash_set::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_set c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**insert\(L'x'\) \= \[x True\]**  
**insert\(L'b'\) \= \[b False\]**  
 **a b c x**  
**insert\(begin\(\), L'y'\) \= y**  
 **a b c x y**  
 **a b c x**  
 **a b c x y**   
## 要求  
 **Header:** \<cliext\/hash\_set\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [hash\_set](../dotnet/hash-set-stl-clr.md)