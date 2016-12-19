---
title: "not1 (STL/CLR) | Microsoft Docs"
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
  - "cliext::not1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "not1 函数 [STL/CLR]"
ms.assetid: a50cd819-10de-4d81-84da-8a34c5414a43
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# not1 (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成 functor 的 `unary_negate`。  
  
## 语法  
  
```  
template<typename Fun>  
    unary_negate<Fun> not1(Fun% functor);  
```  
  
## Template Parameters  
 Fun  
 函数对象的类型。  
  
## 函数参数  
 functor  
 包装的 functor。  
  
## 备注  
 第三个模板函数返回 [unary\_negate](../dotnet/unary-negate-stl-clr.md)`<``Fun``>(functor)`。  使用它作为一种简便方法包装在提供其逻辑非的 functor 的一个参数 functor。  
  
## 示例  
  
```  
// cliext_not1.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 0**  
 **1 0**  
 **1 0**   
## 要求  
 **头文件:** \<cliext\/functional\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [unary\_negate](../dotnet/unary-negate-stl-clr.md)