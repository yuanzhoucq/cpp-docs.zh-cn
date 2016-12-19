---
title: "operator= (deque) (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 成员 [STL/CLR]"
ms.assetid: 0851c6e2-29a2-45da-8c5a-e0b2f5357fb6
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator= (deque) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

替换控件序列。  
  
## 语法  
  
```  
deque<Value>% operator=(deque<Value>% right);  
```  
  
#### 参数  
 right  
 容器复制。  
  
## 备注  
 成员运算符将复制 `right` 给对象，然后返回 `*this`。  你使用它以在 `right`中控制序列的一个副本替换控制序列。  
  
## 示例  
  
```  
// cliext_deque_operator_as.cpp   
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
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**   
## 要求  
 **标头:** \<cliext\/deque\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::assign](../dotnet/deque-assign-stl-clr.md)