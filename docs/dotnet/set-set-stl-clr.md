---
title: "set::set (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "集成员 [STL/CLR]"
ms.assetid: 0cce8501-92ed-431c-b711-14e0b7be7375
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# set::set (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
```  
set();  
explicit set(key_compare^ pred);  
set(set<Key>% right);  
set(set<Key>^ right);  
template<typename InIter>  
    setset(InIter first, InIter last);  
template<typename InIter>  
    set(InIter first, InIter last,  
        key_compare^ pred);  
set(System::Collections::Generic::IEnumerable<GValue>^ right);  
set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### 参数  
 first  
 插入范围的开头。  
  
 last  
 插入范围的末尾。  
  
 pred  
 排序规则序列的谓词。  
  
 right  
 要插入的对象或范围。  
  
## 备注  
 构造函数：  
  
 `set();`  
  
 初始化没有元素的控制序列，并且默认排序 `key_compare()`谓词。  使用它来指定空的初始序列，使用控制默认排序谓词。  
  
 构造函数：  
  
 `explicit set(key_compare^ pred);`  
  
 初始化没有元素的控制序列，并且默认排序 `pred`谓词。  使用它来指定空的初始序列，使用指定的默认排序谓词。  
  
 构造函数：  
  
 `set(set<Key>% right);`  
  
 初始化 `[``right``.`[set::begin](../dotnet/set-begin-stl-clr.md)`(),` `right``.`[set::end](../dotnet/set-end-stl-clr.md)`())`序列的控制序列，使用默认排序谓词。  可以使用它来指定初始化的控制序列，该序列是由该集对象`right`控制序列的副本并使用默认的排序谓词。  
  
 构造函数：  
  
 `set(set<Key>^ right);`  
  
 初始化 `[``right``->`[set::begin](../dotnet/set-begin-stl-clr.md)`(),` `right``->`[set::end](../dotnet/set-end-stl-clr.md)`())`序列的控制序列，使用默认排序谓词。  可以使用它来指定初始化的控制序列，该序列是由该集对象`right`控制序列的副本并使用默认的排序谓词。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `set(InIter first, InIter last);`  
  
 初始化 `[``first``,` `last``)`序列的控制序列，使用默认排序谓词。  使用它来为另一个序列创建一个控制序列副本，其中包含默认排序谓词。  
  
 构造函数：  
  
 `template<typename InIter>`  
  
 `set(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 初始化 `[``first``,` `last``)`序列的控制序列，使用默认排序谓词`pred`。  使用它来为控制序列创建另一个序列的副本，其中包含指定排序谓词。  
  
 构造函数：  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化控制序列时，使用由枚举数`right`指定的默认排序谓词的序列。  使用它来为控制序列创建一个另一个由枚举器指定的序列副本，其中包含默认排序谓词。  
  
 构造函数：  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化由枚举数`right`指定序列的控制序列，使用排序谓词`pred`。  使用它来为控制序列创建一个另一个由枚举器指定序列的副本，其中包含指定排序谓词。  
  
## 示例  
  
```  
// cliext_set_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
// construct an empty container   
    Myset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **a b c**  
**size\(\) \= 0**  
 **c b a**  
 **a b c**  
 **c b a**  
 **a b c**  
 **c b a**  
 **c b a**  
 **a b c**   
## 要求  
 **标头:** \<cliext\/set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [集合](../dotnet/set-stl-clr.md)   
 [set::generic\_container](../dotnet/set-generic-container-stl-clr.md)   
 [set::operator\=](../dotnet/set-operator-assign-stl-clr.md)