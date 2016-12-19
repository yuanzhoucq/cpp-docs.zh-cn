---
title: "range_adapter::operator= (STL/CLR) | Microsoft Docs"
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
  - "cliext::operator="
  - "cliext::range_adapter::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 成员 [STL/CLR]"
ms.assetid: ac378ccc-a42c-4a90-bc27-9b416bee7fa9
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# range_adapter::operator= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

替换存储的迭代器对。  
  
## 语法  
  
```  
range_adapter<Iter>% operator=(range_adapter<Iter>% right);  
```  
  
#### 参数  
 right  
 复制的适配器。  
  
## 备注  
 成员运算符将复制 `right` 给对象，然后返回 `*this`。  使用它用存储的迭代器对副本在 `right`中替换存储的迭代器对。  
  
## 示例  
  
```  
// cliext_range_adapter_operator_as.cpp   
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
    Myrange c1(d1.begin(), d1.end());   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myrange c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**   
## 要求  
 **标头:** \<cliext\/adapter\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)