---
title: "operator!= (set) (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator!= 成员 [STL/CLR]"
ms.assetid: cb82d6a4-0954-49a4-b979-a9ae39df9553
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator!= (set) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列出不相等比较。  
  
## 语法  
  
```  
template<typename Key>  
    bool operator!=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### 参数  
 left  
 比较的容器。  
  
 right  
 比较的正确的容器。  
  
## 备注  
 运算符函数返回 `!(``left` `==` `right``)`。  您可用它测试 `left` 是否没有排序与 `right` 相同，当两集是比较的元素由元素。  
  
## 示例  
  
```  
// cliext_set_operator_ne.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a bc d**  
**\[a b c\] \!\= \[a b c\] 为 false**  
**\[a b c\] \!\= \[a b d\] 为 true**   
## 要求  
 **页眉：** \<cliext\/设置\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [集合](../dotnet/set-stl-clr.md)   
 [operator\=\= \(set\)](../dotnet/operator-equality-set-stl-clr.md)   
 [operator\< \(set\)](../dotnet/operator-less-than-set-stl-clr.md)   
 [operator\>\= \(set\)](../dotnet/operator-greater-or-equal-set-stl-clr.md)   
 [operator\> \(set\)](../dotnet/operator-greater-than-set-stl-clr.md)   
 [operator\<\= \(set\)](../dotnet/operator-less-or-equal-set-stl-clr.md)