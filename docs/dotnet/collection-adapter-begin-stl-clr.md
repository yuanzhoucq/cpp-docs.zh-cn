---
title: "collection_adapter::begin (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::collection_adapter::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin 成员 [STL/CLR]"
ms.assetid: fba55a3f-c1c6-4679-8c94-54cbb468e44c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# collection_adapter::begin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定受控序列的开头。  
  
## 语法  
  
```  
iterator begin();  
```  
  
## 备注  
 指定控件成员函数返回序列中的第一个元素的输入迭代器，或者除一个空序列的结尾。  
  
## 示例  
  
```  
// cliext_collection_adapter_begin.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mycoll::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*begin\(\) \=。**  
**\*\+\+begin\(\) \= b**   
## 要求  
 **页眉：** \<\/cliext 适配器\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)   
 [collection\_adapter::end](../dotnet/collection-adapter-end-stl-clr.md)