---
title: "list::list (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "列表成员 [STL/CLR]"
ms.assetid: 51b58f63-c65a-4d54-b746-0c10635b123b
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::list (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
```  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### 参数  
 count  
 要插入的元素数。  
  
 first  
 插入范围的开头。  
  
 last  
 插入的范围末尾。  
  
 right  
 要插入的对象或 。  
  
 val  
 要插入的元素的值。  
  
## 备注  
 构造函数：  
  
 `list();`  
  
 初始化控制序列的元素。  可以使用它来指定空的初始序列控制。  
  
 构造函数：  
  
 `list(list<Value>% right);`  
  
 初始化与序列 `[``right``.``(),` `right``.``())`的控制。序列[list::end](../dotnet/list-end-stl-clr.md)[list::begin](../dotnet/list-begin-stl-clr.md) 将它指定为复制顺序控制是由列表对象 `right`的初始序列控制。  
  
 构造函数：  
  
 `list(list<Value>^ right);`  
  
 用序列初始化控制序列 `[``right``->`[list::begin](../dotnet/list-begin-stl-clr.md)`(),` `right``->`[list::end](../dotnet/list-end-stl-clr.md)`())`.  将它指定为复制顺序控制是由列表对象 `right`的初始序列控制。  
  
 构造函数：  
  
 `explicit list(size_type count);`  
  
 初始化 `count` 的序列元素控制每个使用 `value_type()`值。  使用它填充元素的容器具有的所有默认值。  
  
 构造函数：  
  
 `list(size_type count, value_type val);`  
  
 初始化 `count` 的序列元素控制每个使用 `val`值。  使用它填充元素的容器具有的所有相同的默认值。  
  
 构造函数：  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 初始化与序列 `[``first``,` `)`的控制。序列`last` 使用会使控制序列复制另一个序列。  
  
 构造函数：  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化枚举数指定的顺序控制序列 `right`。  使用会使控制序列描述枚举器副本另一个序列。  
  
## 示例  
  
```  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **0 0 0**  
 **x x x x x x**  
 **x x x x x**  
 **x x x x x x**  
 **x x x x x x**  
 **x x x x x x**   
## 要求  
 **标头:** \<cliext\/list\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::assign](../dotnet/list-assign-stl-clr.md)   
 [list::generic\_container](../dotnet/list-generic-container-stl-clr.md)   
 [list::operator\=](../dotnet/list-operator-assign-stl-clr.md)