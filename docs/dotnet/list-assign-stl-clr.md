---
title: "list::assign (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::assign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "assign 成员 [STL/CLR]"
ms.assetid: c5f2b131-d0e1-4188-9d4b-d617280e4032
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::assign (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

替换任何元素。  
  
## 语法  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
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
  
## 备注  
 第一个成员函数为 `val`值的 `count` 元素控制的重复替换序列。  使用它填充元素的容器都具有相同的值。  
  
 如果 `InIt` 为整数类型，第二个成员函数行为与 `assign((size_type)``first``, (value_type)``last``)`相同。  否则，它会序列 `[``first``,` `last``)`替换序列控制。  使用会使控制序列复制另一个序列。  
  
 第三个成员函数为枚举数指定的顺序控制 `right`替换序列。  使用会使控制序列描述枚举数的序列复制。  
  
## 示例  
  
```  
// cliext_list_assign.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    cliext::list<wchar_t>::iterator it = c1.end();   
    c2.assign(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **x x x x x x**  
 **b**  
 **a b c**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::operator\=](../dotnet/list-operator-assign-stl-clr.md)