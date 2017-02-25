---
title: "deque::push_back (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::push_back"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "push_back 成员 [STL/CLR]"
ms.assetid: dafd5a4d-1fc7-434c-b129-a523099f8701
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# deque::push_back (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

添加一个新的元素之前。  
  
## 语法  
  
```  
void push_back(value_type val);  
```  
  
## 备注  
 成员函数插入与值 `val` 的元素控制在序列末尾。  使用它附加另一个元素添加到 deque。  
  
## 示例  
  
```  
// cliext_deque_push_back.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
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
 **页眉：** \<cliext\/deque\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::pop\_back](../dotnet/deque-pop-back-stl-clr.md)   
 [deque::pop\_front](../dotnet/deque-pop-front-stl-clr.md)   
 [deque::push\_front](../dotnet/deque-push-front-stl-clr.md)