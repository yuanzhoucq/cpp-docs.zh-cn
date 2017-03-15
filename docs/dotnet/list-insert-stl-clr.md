---
title: "list::insert (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成员 [STL/CLR]"
ms.assetid: 399ed30f-6b76-41a8-b180-6070e3ca1c68
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# list::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

添加元素到一个指定位置处。  
  
## 语法  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### 参数  
 count  
 要插入的元素数。  
  
 first  
 插入范围的开头。  
  
 last  
 插入范围的末尾。  
  
 right  
 插入的枚举。  
  
 val  
 要插入的元素的值。  
  
 where  
 在之前插入的容器。  
  
## 备注  
 每个成员函数，在控制序列中`where`指向元素之后，插入由剩余的操作数所指定的序列，  
  
 第一个成员函数插入值`val`的元素，并返回指定新插入的元素的迭代器。  使用它在迭代器指定的位置之前插入一个元素。  
  
 第二个成员函数插入重复 `val`次 的元素 \(`count`\)。  使用它来插入零或相同值的所有副本的更多连续的元素。  
  
 如果`InIt`是一个整数类型，第三个成员函数的行为和`insert(``where``, (size_type)``first``, (value_type)``last``)`相同。  否则，其插入序列 `[``first``,` `last``)`。  将它粘贴从其他序列复制的零个或多个连续元素。  
  
 第四个成员函数 `right`插入选定的序列。  使用插入它枚举器描述的顺序。  
  
 当插入单个元素时，元素副本数是线性的中元素的数量插入点且序列之间的接近序列结束的结尾。\(当在一个或多个元素在序列中的任一端，元素副本不发生。\)如果 `InIt` 是输入迭代器，第三个成员函数。序列有效运行每个元素的单个插入。  否则，插入`N`元件时，元件的份数是线性的`N`加在插入点和序列的较近端之间的元素数。  
  
## 示例  
  
```  
// cliext_list_insert.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using index   
    it = c2.begin();   
    ++it, ++it, ++it;   
    c2.insert(it, L'z');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **a b c**  
**insert\(begin\(\)\+1, L'x'\) \= x**  
 **a x b c**  
 **y y**  
 **y y a x b**  
 **a x b c y y a x b**   
## 要求  
 **标头:** \<cliext\/list\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::assign](../dotnet/list-assign-stl-clr.md)