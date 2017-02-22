---
title: "vector::push_back (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::vector::push_back"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "push_back 成员 [STL/CLR]"
ms.assetid: 4a4c302b-e29f-4b68-b759-2f831814d896
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# vector::push_back (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

添加新的末尾元素。  
  
## 语法  
  
```  
void push_back(value_type val);  
```  
  
## 备注  
 成员函数在控制的序列末尾插入值为 `val` 的元素。  使用它附加另一元素到 vector。  
  
## 示例  
  
```  
// cliext_vector_push_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 要求  
 **标头:** \<cliext\/vector\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::pop\_back](../dotnet/vector-pop-back-stl-clr.md)