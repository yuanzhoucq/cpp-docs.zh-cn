---
title: "queue::reference (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::queue::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "引用成员 [STL/CLR]"
ms.assetid: cca05237-5b95-4cca-ac21-b786aa8a3c96
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# queue::reference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

元素的引用的类型。  
  
## 语法  
  
```  
typedef value_type% reference;  
```  
  
## 备注  
 类型描述对元素的引用。  
  
## 示例  
  
```  
// cliext_queue_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify back of queue and redisplay   
    Myqueue::reference ref = c1.back();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **x b**   
## 要求  
 **页眉：** \<\/cliext 队列\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::const\_reference](../dotnet/queue-const-reference-stl-clr.md)   
 [queue::value\_type](../dotnet/queue-value-type-stl-clr.md)