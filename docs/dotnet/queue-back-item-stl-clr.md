---
title: "queue::back_item (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::queue::back_item"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "back_item 成员 [STL/CLR]"
ms.assetid: 721e44e1-eb46-41bf-8b3c-0fcbc02fb155
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# queue::back_item (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

访问最后一个元素。  
  
## 语法  
  
```  
property value_type back_item;  
```  
  
## 备注  
 属性访问最后一个元素，该元素必须为非空元素。  如果您知道存在时，使用它读取或写入最后一个元素。  
  
## 示例  
  
```  
// cliext_queue_back_item.cpp   
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
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**back\_item 为 c**  
 **a b x**   
## 要求  
 **标头:** \<cliext\/queue\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::back](../dotnet/queue-back-stl-clr.md)   
 [queue::front](../dotnet/queue-front-stl-clr.md)   
 [queue::front\_item](../dotnet/queue-front-item-stl-clr.md)