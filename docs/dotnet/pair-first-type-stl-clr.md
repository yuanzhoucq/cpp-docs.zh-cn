---
title: "pair::first_type (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::pair::first_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "first_type 成员 [STL/CLR]"
ms.assetid: 8a7792ee-a2f6-4e17-9d0b-9c78007202d9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# pair::first_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

第一个包装值的类型。  
  
## 语法  
  
```  
typedef Value1 first_type;  
```  
  
## 备注  
 表示模板参数的 `Value1`同义词。  
  
## 示例  
  
```  
// cliext_pair_first_type.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
  **\[x, 3\]**   
## 要求  
 **标头:** \<cliext\/utility\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [pair](../dotnet/pair-stl-clr.md)   
 [pair::first](../dotnet/pair-first-stl-clr.md)   
 [pair::second](../dotnet/pair-second-stl-clr.md)   
 [pair::second\_type](../dotnet/pair-second-type-stl-clr.md)