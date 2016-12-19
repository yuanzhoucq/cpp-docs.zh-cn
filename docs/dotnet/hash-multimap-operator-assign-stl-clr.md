---
title: "hash_multimap::operator= (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 成员 [STL/CLR]"
ms.assetid: f4c1a961-e8af-44f3-b61c-83d4dda3b403
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::operator= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控件替换序列。  
  
## 语法  
  
```  
hash_multimap<Key, Mapped>% operator=(hash_multimap<Key, Mapped>% right);  
```  
  
#### 参数  
 right  
 复制的容器。  
  
## 备注  
 运算符将 `right` 对该对象的成员，然后返回 `*this`。  使用它将控制的序列复制在 `right`中替换控件序列。  
  
## 示例  
  
```  
// cliext_hash_multimap_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_multimap c2;   
    c2 = c1;   
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[c 3\]**   
## 要求  
 **页眉：** \<cliext\/hash\_map\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)