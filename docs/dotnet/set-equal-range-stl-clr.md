---
title: "set::equal_range (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::equal_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "equal_range 成员 [STL/CLR]"
ms.assetid: f0b20a65-f37a-44b1-a291-09c33c10c355
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::equal_range (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找数组与指定键的。  
  
## 语法  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### 参数  
 键  
 搜索的键值。  
  
## 备注  
 成员函数返回一对迭代器 `cliext::pair<iterator, iterator>(` [set::lower\_bound](../dotnet/set-lower-bound-stl-clr.md)[set::upper\_bound](../dotnet/set-upper-bound-stl-clr.md)`(``key``),` `(``key``))`。  使用它确定当前与指定键的范围控制元素在序列。  
  
## 示例  
  
```  
// cliext_set_equal_range.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_iter Pairii;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**equal\_range \(空\) L'x 为 True**  
 **b**   
## 要求  
 **页眉：** \<cliext\/设置\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [集合](../dotnet/set-stl-clr.md)   
 [set::count](../dotnet/set-count-stl-clr.md)   
 [set::find](../dotnet/set-find-stl-clr.md)   
 [set::lower\_bound](../dotnet/set-lower-bound-stl-clr.md)   
 [set::upper\_bound](../dotnet/set-upper-bound-stl-clr.md)