---
title: "list::resize (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::resize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resize 成员 [STL/CLR]"
ms.assetid: c4b8d41f-a62b-4dbc-8568-0e0a9da24016
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::resize (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

更改元素的数量。  
  
## 语法  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### 参数  
 new\_size  
 控制序列的新范围。  
  
 val  
 填充元素的值。  
  
## 备注  
 成员函数都从此确保 [list::size](../dotnet/list-size-stl-clr.md)`()` 返回 `new_size`。  如果它必须能够控制序列较长，第一个成员函数将具有值 `value_type()`的元素，第二个成员函数，而附加有值 `val`的元素。  若要使控制序列较短，同时有效成员函数`() -` `new_size` 元素清除上 [list::size](../dotnet/list-size-stl-clr.md)时间。  使用可以通过调整填充或确保序列具有控制范围，`new_size`当前控件序列。  
  
## 示例  
  
```  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **0 0 0 0**  
**size\(\) \= 0**  
 **x x x x x**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::clear](../dotnet/list-clear-stl-clr.md)   
 [list::erase](../dotnet/list-erase-stl-clr.md)   
 [list::insert](../dotnet/list-insert-stl-clr.md)