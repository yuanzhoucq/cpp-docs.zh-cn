---
title: "operator!= (pair) (STL/CLR) | Microsoft Docs"
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
  - "cliext::pair::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator!= 成员 [STL/CLR]"
ms.assetid: 167005f9-727d-40af-8d6d-2793d0daa96a
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator!= (pair) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

匹配不相等比较。  
  
## 语法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator!=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### 参数  
 left  
 左对比较。  
  
 right  
 右对比较。  
  
## 备注  
 操作符函数返回`!(``left` `==` `right``)` 。  当一个个元素地比较两个对集时，您可以用它测试 `left` 是否在 `right` 之后排序。  
  
## 示例  
  
```  
// cliext_pair_operator_ne.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] != [x 3] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[x 3] != [x 4] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
  **\[x, 3\]**  
**\[x, 4\]**  
**\[x 3\] \!\= \[x 3\] 为 false**  
**\[x 3\] \!\= \[x 4\] 为 true**   
## 要求  
 **标头:** \<cliext\/utility\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [pair](../dotnet/pair-stl-clr.md)   
 [operator\=\= \(pair\)](../dotnet/operator-equality-pair-stl-clr.md)   
 [operator\< \(pair\)](../dotnet/operator-less-than-pair-stl-clr.md)   
 [operator\>\= \(pair\)](../dotnet/operator-greater-or-equal-pair-stl-clr.md)   
 [operator\> \(pair\)](../dotnet/operator-greater-than-pair-stl-clr.md)   
 [operator\<\= \(pair\)](../dotnet/operator-less-or-equal-pair-stl-clr.md)