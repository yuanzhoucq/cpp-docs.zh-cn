---
title: "list::unique (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::unique"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unique 成员 [STL/CLR]"
ms.assetid: c3a29e4e-0ec1-4472-b050-7a9511037132
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::unique (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除通过指定测试的相邻元素。  
  
## 语法  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### 参数  
 pred  
 比较器的元素对。  
  
## 备注  
 第一个成员函数。控制序列 \(取消\) 移除比较等于其前面的元素中的每个元素。\-\-如果元素在 `X` 元素的 `Y` 和 `X == Y`成员函数，则移除 `Y`。  将它删除除的相邻元素的每个 subsequence 副本相等比较。  注意控制排序，如果序列，如 [list::sort](../dotnet/list-sort-stl-clr.md)`()`，通过调用成员函数仅保留元素唯一值。\(该名称\)。  
  
 第二个成员函数行为与第一个相同，不同之处在于，它将删除每个元素都紧跟在元素的 `pred``(X, Y)``X` 的 `Y`。  将它删除除的相邻元素的每个 subsequence 副本满足某一谓词函数或委托指定。  注意，如果序列顺序控制，例如通过调用 `sort(``pred``)`，使成员函数没有等效排序与任何其他元素的元素。  
  
## 示例  
  
```  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **为 c**  
 **a b c**  
 **。**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::remove](../dotnet/list-remove-stl-clr.md)   
 [list::remove\_if](../dotnet/list-remove-if-stl-clr.md)   
 [list::sort](../dotnet/list-sort-stl-clr.md)