---
title: "vector::size_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::size_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size_type 成员 [STL/CLR]"
ms.assetid: 0789e887-e79a-42f9-a162-fc27f1341900
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::size_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

两个元素间的带符号距离的类型。  
  
## 语法  
  
```  
typedef int size_type;  
```  
  
## 备注  
 这个类型描述了一个非整数元素的数量。  
  
## 示例  
  
```  
// cliext_vector_size_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**end\(\)\-begin\(\) \= 3**   
## 要求  
 **标头:** \<cliext\/vector\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::empty](../dotnet/vector-empty-stl-clr.md)