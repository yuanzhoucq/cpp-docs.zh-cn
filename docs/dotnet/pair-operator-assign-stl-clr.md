---
title: "pair::operator= (STL/CLR) | Microsoft Docs"
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
  - "cliext::pair::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 成员 [STL/CLR]"
ms.assetid: b6228037-914e-4efa-8491-65dbb0e93f61
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# pair::operator= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

替换存储对的值。  
  
## 语法  
  
```  
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);  
```  
  
#### 参数  
 right  
 对复制的。  
  
## 备注  
 运算符将 `right` 对该对象的成员，然后返回 `*this`。  使用它用存储对的副本替换存储的值对 `right`中的值。  
  
## 示例  
  
```  
// cliext_pair_operator_as.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
// assign to a new pair   
    cliext::pair<wchar_t, int> c2;   
    c2 = c1;   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
    return (0);   
    }  
  
```  
  
  **\[x，3\]**  
**\[x，3\]**   
## 要求  
 **页眉：** \<\/cliext 实用工具\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [pair](../dotnet/pair-stl-clr.md)