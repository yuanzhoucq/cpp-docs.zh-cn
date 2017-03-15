---
title: "deque::deque (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::deque"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "deque 成员 [STL/CLR]"
ms.assetid: e5bc9511-619e-469c-b50a-e06858e7fce7
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# deque::deque (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造容器对象。  
  
## 语法  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### 参数  
 count  
 插入的元素数。  
  
 首先  
 插入范围的开头。  
  
 last  
 插入的范围末尾。  
  
 right  
 插入的对象或值范围。  
  
 val  
 插入元素的值。  
  
## 备注  
 构造函数：  
  
 `deque();`  
  
 初始化控制序列的元素。  可以使用它来指定空的初始序列控制。  
  
 构造函数：  
  
 `deque(deque<Value>% right);`  
  
 初始化与序列 `[``right``.``(),` `right``.``())`的控制。序列[deque::end](../dotnet/deque-end-stl-clr.md)[deque::begin](../dotnet/deque-begin-stl-clr.md) 将它指定为顺序复制由 deque 对象控制 `right`控件的初始序列。  
  
 构造函数：  
  
 `deque(deque<Value>^ right);`  
  
 初始化与序列 `[``right``->``(),` `right``->``())`的控制。序列[deque::end](../dotnet/deque-end-stl-clr.md)[deque::begin](../dotnet/deque-begin-stl-clr.md) 将它指定为复制由 deque 对象顺序控制柄是 `right`的初始序列控制。  
  
 构造函数：  
  
 `explicit deque(size_type count);`  
  
 初始化 `count` 的序列元素控制每个使用 `value_type()`值。  使用它填充元素的容器具有的所有默认值。  
  
 构造函数：  
  
 `deque(size_type count, value_type val);`  
  
 初始化 `count` 的序列元素控制每个使用 `val`值。  使用它填充元素的容器都具有相同的值。  
  
 构造函数：  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 初始化与序列 `[``first``,` `last``)`的顺序控制。  使用会使控制序列复制另一个序列。  
  
 构造函数：  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化枚举数指定的顺序控制序列 `right`。  使用会使控制序列描述枚举器副本另一个序列。  
  
## 示例  
  
```  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
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
 **页眉：** \<cliext\/deque\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::assign](../dotnet/deque-assign-stl-clr.md)   
 [deque::generic\_container](../dotnet/deque-generic-container-stl-clr.md)   
 [operator\= \(deque\)](../dotnet/operator-assign-deque-stl-clr.md)