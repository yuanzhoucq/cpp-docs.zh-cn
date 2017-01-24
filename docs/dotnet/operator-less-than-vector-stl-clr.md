---
title: "operator&lt; (vector) (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator< 成员 [STL/CLR]"
ms.assetid: 41fbd028-e937-4337-9429-57e79a993eef
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt; (vector) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Vector 小于比较  
  
## 语法  
  
```  
template<typename Value>  
    bool operator<(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### 参数  
 left  
 比较左边的容器。  
  
 right  
 比较右边的容器。  
  
## 备注  
 如果运算符函数返回 TRUE，最低位置的`i`，其中，`!(``right``[i] <` `left``[i])` 是正确的，`left``[i] <` `right``[i]`。  否则，返回`left``->size() <` `right``->size()` 您使用它测试 `left` 在 `right` 之前是否有序，当2个 vector 按元素比较时。  
  
## 示例  
  
```  
// cliext_vector_operator_lt.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
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
 **a b d**  
**\[a b c\] \< \[a b c\] 为 False**  
**\[a b c\] \< \[a b d\] 为 True**   
## 要求  
 **标头:** \<cliext\/vector\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [operator\=\= \(vector\)](../dotnet/operator-equality-vector-stl-clr.md)   
 [operator\!\= \(vector\)](../dotnet/operator-inequality-vector-stl-clr.md)   
 [operator\>\= \(vector\)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)   
 [operator\> \(vector\)](../dotnet/operator-greater-than-vector-stl-clr.md)   
 [operator\<\= \(vector\)](../dotnet/operator-less-or-equal-vector-stl-clr.md)