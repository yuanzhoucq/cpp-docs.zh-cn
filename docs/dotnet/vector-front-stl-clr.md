---
title: "vector::front (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::front"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "front 成员 [STL/CLR]"
ms.assetid: 37a36157-8220-4d5b-85b5-c6a63211a322
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::front (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

访问第一个元素。  
  
## 语法  
  
```  
reference front();  
```  
  
## 备注  
 成员函数返回控制到序列中第一个的元素的引用，必须非空。  如果您知道存在时，使用它读取或写入第一个元素。  
  
## 示例  
  
```  
// cliext_vector_front.cpp   
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
**front\(\) \= a**  
 **x b c**   
## 要求  
 **标头:** \<cliext\/vector\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::back](../dotnet/vector-back-stl-clr.md)   
 [vector::back\_item](../dotnet/vector-back-item-stl-clr.md)   
 [vector::front\_item](../dotnet/vector-front-item-stl-clr.md)