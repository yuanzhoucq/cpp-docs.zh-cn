---
title: "collection_adapter::swap (STL/CLR) | Microsoft Docs"
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
  - "cliext::collection_adapter::swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap 成员 [STL/CLR]"
ms.assetid: 778f85bf-c6e3-48ff-bc97-0488f3e8f143
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# collection_adapter::swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

交换两个容器的内容。  
  
## 语法  
  
```  
void swap(collection_adapter<Coll>% right);  
```  
  
#### 参数  
 right  
 要与其交换内容的容器。  
  
## 备注  
 成员函数将交换了 `*this` 和 `right`之间的存储 BCL 句柄。  
  
## 示例  
  
```  
// cliext_collection_adapter_swap.cpp   
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
  
// construct another container with repetition of values   
    cliext::deque<wchar_t> d2(5, L'x');   
    Mycoll c2(%d2);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **x x x x x**  
 **x x x x x**  
 **a b c**   
## 要求  
 **标头:** \<cliext\/adapter\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)   
 [collection\_adapter::operator\=](../dotnet/collection-adapter-operator-assign-stl-clr.md)