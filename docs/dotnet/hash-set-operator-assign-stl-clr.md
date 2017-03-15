---
title: "hash_set::operator= (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 成员 [STL/CLR]"
ms.assetid: 25ee3afd-90cd-483f-ae03-b52ce1396090
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::operator= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

替换控件序列。  
  
## 语法  
  
```  
hash_set<Key>% operator=(hash_set<Key>% right);  
```  
  
#### 参数  
 right  
 容器复制。  
  
## 备注  
 成员运算符将复制 `right` 给对象，然后返回 `*this`。  你使用它以在 `right`中控制序列的一个副本替换控制序列。  
  
## 示例  
  
```  
// cliext_hash_set_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myhash_set::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_set c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myhash_set::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**   
## 要求  
 **标头:** \<cliext\/hash\_set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_set](../dotnet/hash-set-stl-clr.md)