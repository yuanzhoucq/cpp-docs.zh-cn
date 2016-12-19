---
title: "operator&lt; (deque) (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator< 成员 [STL/CLR]"
ms.assetid: f2fa1bb1-bc0a-4e9e-826b-6b72a5543b29
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt; (deque) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Deque 小于比较。  
  
## 语法  
  
```  
template<typename Value>  
    bool operator<(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### 参数  
 left  
 比较的容器。  
  
 right  
 比较的正确的容器。  
  
## 备注  
 运算符函数返回 TRUE，如果，则最低位置的 `!(``right``[i] <` `left``[i])` 是它还 `left``[i] <` `right``[i]`的 `i`。  否则，它返回 `left``->size() <` `right`可以用它测试的`->size()``left` 是 `right` 之前排序，当两 deques 是比较的元素由元素。  
  
## 示例  
  
```  
// cliext_deque_operator_lt.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a bc d**  
**\[a b c\] \< \[a b c\] 为 c b 的错误**  
**\[a b c\] \< \[a b d\] 为 true**   
## 要求  
 **页眉：** \<cliext\/deque\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [operator\=\= \(deque\)](../dotnet/operator-equality-deque-stl-clr.md)   
 [deque::operator\!\=](../dotnet/deque-operator-inequality-stl-clr.md)   
 [operator\>\= \(deque\)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)   
 [operator\> \(deque\)](../dotnet/operator-greater-than-deque-stl-clr.md)   
 [operator\<\= \(deque\)](../dotnet/operator-less-or-equal-deque-stl-clr.md)