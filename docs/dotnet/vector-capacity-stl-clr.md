---
title: "vector::capacity (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::capacity"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "capacity 成员 [STL/CLR]"
ms.assetid: f82d8da9-8b4d-4288-8d18-8e9ca5911d87
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::capacity (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

报告为容器分配的存储大小。  
  
## 语法  
  
```  
size_type capacity();  
```  
  
## 备注  
 成员函数返回当前分配的存储顺序，使控件的大小的值至少与 [vector::size](../dotnet/vector-size-stl-clr.md)`()`。  使用它来确定有多少容器可以增长，则需要重新分配控制序列中的前存储。  
  
## 示例  
  
```  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**capacity\(\) \= 4，好为 True**  
**capacity\(\) \= 9，好为 True**   
## 说明  
 注意实际容量可能与显示的值不同，只要为，此处 `ok` 的所有报告。  
  
## 要求  
 **页眉：** \<cliext\/矢量\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::reserve](../dotnet/vector-reserve-stl-clr.md)