---
title: "operator&gt;= (vector) (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator>= 成员 [STL/CLR]"
ms.assetid: c06f4489-f65a-4bd6-944f-9b23a2bb4e35
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&gt;= (vector) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大于的向量或等于比较。  
  
## 语法  
  
```  
template<typename Value>  
    bool operator>=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### 参数  
 left  
 比较的容器。  
  
 right  
 比较的正确的容器。  
  
## 备注  
 运算符函数返回 `!(``left` `<` `right``)`。  您可用它测试 `left` 是否没有 `right` 之前排序，当两个矢量是比较的元素由元素。  
  
## 示例  
  
```  
// cliext_vector_operator_ge.cpp   
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
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a bc d**  
**\[a b c\] \>\= \[a b c\] 为 true 为 c**  
**\[a b c\] \>\= \[a b d\] 为 b 的错误**   
## 要求  
 **页眉：** \<cliext\/矢量\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [operator\=\= \(vector\)](../dotnet/operator-equality-vector-stl-clr.md)   
 [operator\!\= \(vector\)](../dotnet/operator-inequality-vector-stl-clr.md)   
 [operator\< \(vector\)](../dotnet/operator-less-than-vector-stl-clr.md)   
 [operator\> \(vector\)](../dotnet/operator-greater-than-vector-stl-clr.md)   
 [operator\<\= \(vector\)](../dotnet/operator-less-or-equal-vector-stl-clr.md)