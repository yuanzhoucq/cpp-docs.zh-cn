---
title: "vector::resize (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::vector::resize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resize 成员 [STL/CLR]"
ms.assetid: a3556fbc-67d9-463a-9ffc-cb43ee15657f
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# vector::resize (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

更改元素的数量。  
  
## 语法  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### 参数  
 new\_size  
 受控序列的新大小。  
  
 val  
 填充元素的值。  
  
## 备注  
 成员函数都从此确保 [vector::size](../dotnet/vector-size-stl-clr.md)`()` 返回 `new_size`。  如果它必须能够控制序列较长，第一个成员函数将具有值 `value_type()`的元素，第二个成员函数，而附加有值 `val`的元素。  若要使控制序列较短，同时有效成员函数`() -` `new_size` 元素清除上 [vector::size](../dotnet/vector-size-stl-clr.md)时间。  使用可以通过调整填充或确保序列具有控制范围，`new_size`当前控件序列。  
  
## 示例  
  
```  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
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
 **标头:** \<cliext\/vector\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::clear](../dotnet/vector-clear-stl-clr.md)   
 [vector::erase](../dotnet/vector-erase-stl-clr.md)   
 [vector::insert](../dotnet/vector-insert-stl-clr.md)