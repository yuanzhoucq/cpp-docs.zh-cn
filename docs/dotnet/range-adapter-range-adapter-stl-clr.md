---
title: "range_adapter::range_adapter (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::range_adapter::range_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range_adapter 成员 [STL/CLR]"
ms.assetid: b16af13f-3358-4e82-927d-d0d4986bcb18
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# range_adapter::range_adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造适配器对象。  
  
## 语法  
  
```  
range_adapter();  
range_adapter(range_adapter<Iter>% right);  
range_adapter(range_adapter<Iter>^ right);  
range_adapter(Iter first, Iter last);  
```  
  
#### 参数  
 first  
 包装的第一个迭代器。  
  
 last  
 包装的第二个迭代器。  
  
 right  
 要复制的对象。  
  
## 备注  
 构造函数：  
  
 `range_adapter();`  
  
 初始化的默认构造的迭代器的存储的迭代器对。  
  
 构造函数：  
  
 `range_adapter(range_adapter<Iter>% right);`  
  
 通过重复存储在 `right`中对初始化存储的迭代器对。  
  
 构造函数：  
  
 `range_adapter(range_adapter<Iter>^ right);`  
  
 通过重复存储在 `*right`中对初始化存储的迭代器对。  
  
 构造函数：  
  
 `range_adapter(Iter^ first, last);`  
  
 初始化 `first` 和 `last`的存储对。  
  
## 示例  
  
```  
// cliext_range_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// construct an empty adapter   
    Myrange c1;   
  
// construct with an iterator pair   
    Myrange c2(d1.begin(), d1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another adapter   
    Myrange c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying an adapter handle   
    Myrange c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**  
 **a b c**   
## 要求  
 **标头:** \<cliext\/adapter\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)   
 [range\_adapter::operator\=](../dotnet/range-adapter-operator-assign-stl-clr.md)