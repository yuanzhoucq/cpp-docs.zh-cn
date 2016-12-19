---
title: "operator== (multiset) (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator== 成员 [STL/CLR]"
ms.assetid: 327918f8-ed9b-4549-a85e-11632757b317
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator== (multiset) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列出相等比较。  
  
## 语法  
  
```  
template<typename Key>  
    bool operator==(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### 参数  
 left  
 比较左边的容器。  
  
 right  
 比较右边的容器。  
  
## 备注  
 当由 `left` 和 `right` 控制的顺序具有相同长度，并且，对每个位置 `i`，`left``[i] ==` `right``[i]`，该运算符函数返回 true。  当一个个元素地比较多元集合时，您可以用它测试 `left` 是否在 `right` 之后排序。  
  
## 示例  
  
```  
// cliext_multiset_operator_eq.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b d**  
**\[a b c\] \=\= \[a b c\] 为True**  
**\[a b c\] \=\= \[a b d\] 为 False**   
## 要求  
 **标头:** \<cliext\/set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [operator\!\= \(multiset\)](../dotnet/operator-inequality-multiset-stl-clr.md)   
 [operator\< \(multiset\)](../dotnet/operator-less-than-multiset-stl-clr.md)   
 [operator\>\= \(multiset\)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)   
 [operator\> \(multiset\)](../dotnet/operator-greater-than-multiset-stl-clr.md)   
 [operator\<\= \(multiset\)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)