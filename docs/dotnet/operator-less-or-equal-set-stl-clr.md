---
title: "operator&lt;= (set) (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator<= 成员 [STL/CLR]"
ms.assetid: acb5997b-cdc1-44d6-80c1-e20b01b4db02
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt;= (set) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

列表小于或等于比较。  
  
## 语法  
  
```  
template<typename Key>  
    bool operator<=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### 参数  
 left  
 比较左边的容器。  
  
 right  
 比较右边的容器。  
  
## 备注  
 运算符函数返回 `!(``right` `<` `left``)`。  当一个个元素地比较两种多集时，您可以用它测试 `left` 是否在 `right` 之后排序。  
  
## 示例  
  
```  
// cliext_set_operator_le.cpp   
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
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b d**  
**\[a b c\] \<\= \[a b c\] 为True**  
**\[a b d\] \<\= \[a b c\] 为 false**   
## 要求  
 **标头:** \<cliext\/set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [集合](../dotnet/set-stl-clr.md)   
 [operator\=\= \(set\)](../dotnet/operator-equality-set-stl-clr.md)   
 [operator\!\= \(set\)](../dotnet/operator-inequality-set-stl-clr.md)   
 [operator\< \(set\)](../dotnet/operator-less-than-set-stl-clr.md)   
 [operator\>\= \(set\)](../dotnet/operator-greater-or-equal-set-stl-clr.md)   
 [operator\> \(set\)](../dotnet/operator-greater-than-set-stl-clr.md)