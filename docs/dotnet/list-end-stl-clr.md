---
title: "list::end (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "end 成员 [STL/CLR]"
ms.assetid: c3444164-2c6e-4cbd-8765-1ce7d30fc43e
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# list::end (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定受控序列的末尾。  
  
## 语法  
  
```  
iterator end();  
```  
  
## 备注  
 成员函数返回序列仅控制。结束点的随机访问迭代器。  使用该控制获取指定序列的结尾的迭代器；，如果控制更改序列的长度，其状态不会发生更改。  
  
## 示例  
  
```  
// cliext_list_end.cpp   
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
  
// inspect last two items   
    cliext::list<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*\-\- \-\-end\(\) \= b**  
**\*\-\-end\(\) 为 c**  
 **个 x \- Y**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::back](../dotnet/list-back-stl-clr.md)   
 [list::back\_item](../dotnet/list-back-item-stl-clr.md)   
 [list::begin](../dotnet/list-begin-stl-clr.md)