---
title: "vector::insert (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成员 [STL/CLR]"
ms.assetid: f240cabf-f9d1-40c1-9cfb-975a90955546
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将元素中的指定位置。  
  
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
 插入的元素数。  
  
 首先  
 插入范围的开头。  
  
 last  
 插入的范围末尾。  
  
 right  
 插入的枚举。  
  
 val  
 插入元素的值。  
  
 where  
 在之前插入的容器。  
  
## 备注  
 每个成员函数在元素前插入，指向受控制的 `where` 序列，其余操作数指定的顺序。  
  
 第一个成员函数插入与值 `val` 的元素并返回指定新插入元素的迭代器。  使用它在迭代器指定的位置之前插入一个元素。  
  
 第二个成员函数插入重复 `val`次 的元素 \(`count`\)。  使用它、零或相同值的所有副本的更多连续的元素。  
  
 如果 `InIt` 为整数类型，第三个成员函数行为与 `insert(``where``, (size_type)``first``, (value_type)``last``)`相同。  否则，其插入序列 `[``first``,` `last``)`。  使用它、零或从其他序列复制的更多连续的元素。  
  
 第四个成员函数 `right`插入选定的序列。  使用插入它枚举器描述的顺序。  
  
 当插入单个元素时，元素副本数是线性的中元素的数量。插入点且序列之间的接近结束的。\(当在一个或多个元素在序列中的任一端，元素副本不发生。\)如果 `InIt` 是输入迭代器，第三个成员函数。序列有效运行每个元素的单个 Insert。  否则，在中，当在 `N` 元素时，元素副本数是线性的。`N` 和的元素数目在插入点和序列之间的接近结束的。  
  
## 示例  
  
```  
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
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
    return (0);   
    }  
  
```  
  
  **a b c**  
**insert\(begin\(\)\+1，L'x \= x\)**  
 **x 为 c**  
 **y y**  
 **y y x b**  
 **x 为 c y y x b**   
## 要求  
 **页眉：** \<cliext\/矢量\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::assign](../dotnet/vector-assign-stl-clr.md)