---
title: "deque::front (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::front"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "front 成员 [STL/CLR]"
ms.assetid: eb8cb5f2-346d-4d7a-bb7b-cf67fe4318e8
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# deque::front (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

访问第一个元素。  
  
## 语法  
  
```  
reference front();  
```  
  
## 备注  
 成员函数返回控制到序列中的第一个元素的引用，必须非空。  使用它读取或写入第一个元素，因此，如果您知道存在时。  
  
## 示例  
  
```  
// cliext_deque_front.cpp   
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
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**front\(\) \=。**  
 **x 为 c**   
## 要求  
 **页眉：** \<cliext\/deque\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::back](../dotnet/deque-back-stl-clr.md)   
 [deque::back\_item](../dotnet/deque-back-item-stl-clr.md)   
 [deque::front\_item](../dotnet/deque-front-item-stl-clr.md)