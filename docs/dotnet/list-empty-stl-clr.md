---
title: "list::empty (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::empty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "empty 成员 [STL/CLR]"
ms.assetid: f45edf8a-927d-41ff-9c09-cb0fba4f08b8
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# list::empty (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试元素不存在。  
  
## 语法  
  
```  
bool empty();  
```  
  
## 备注  
 成员函数返回 true 一个空序列控制。  它与`() == 0`等效。[list::size](../dotnet/list-size-stl-clr.md) 使用该测试列表是否为空。  
  
## 示例  
  
```  
// cliext_list_empty.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size\(\) \= 3**  
**empty\(\) \= false**  
**size\(\) \= 0**  
**empty\(\) 为 True**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::size](../dotnet/list-size-stl-clr.md)