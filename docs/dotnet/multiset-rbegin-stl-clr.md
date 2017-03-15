---
title: "multiset::rbegin (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multiset::rbegin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rbegin 成员 [STL/CLR]"
ms.assetid: beec0024-9565-4809-86f9-8b2c4e533923
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# multiset::rbegin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定反转的受控序列的开头。  
  
## 语法  
  
```  
reverse_iterator rbegin();  
```  
  
## 备注  
 指定控件成员函数返回序列中的最后一个元素，或进行反向迭代器对象一个空序列的开头之外。  因此，它指定反向序列的 `beginning`。  用于获取一个迭代器，该迭代器指定相反顺序的受控序列的 `current` 开头，但如果受控序列的长度发生更改，则该迭代器的状态也会发生更改。  
  
## 示例  
  
```  
// cliext_multiset_rbegin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymultiset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*rbegin\(\) 为 c**  
**\*\+\+rbegin\(\) \= b**   
## 要求  
 **页眉：** \<cliext\/设置\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::begin](../dotnet/multiset-begin-stl-clr.md)   
 [multiset::end](../dotnet/multiset-end-stl-clr.md)   
 [multiset::rend](../dotnet/multiset-rend-stl-clr.md)