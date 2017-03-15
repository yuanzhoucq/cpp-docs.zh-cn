---
title: "deque::back (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::back"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "back 成员 [STL/CLR]"
ms.assetid: 5608cdda-212d-42f6-866b-b04aec04ef8e
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# deque::back (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

访问最后一个元素。  
  
## 语法  
  
```  
reference back();  
```  
  
## 备注  
 成员函数返回控制到序列中最后面的元素的引用，必须非空。  使用它访问，最后一个元素，在您知道存在\)。  
  
## 示例  
  
```  
// cliext_deque_back.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**back\(\) \= c**  
 **a b x**   
## 要求  
 **标头:** \<cliext\/deque\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::back\_item](../dotnet/deque-back-item-stl-clr.md)   
 [deque::front](../dotnet/deque-front-stl-clr.md)   
 [deque::front\_item](../dotnet/deque-front-item-stl-clr.md)