---
title: "hash_set::size (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_set::size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size 成员 [STL/CLR]"
ms.assetid: e006590e-8710-4294-b3a3-dcded0668a24
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_set::size (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计算元素的数量。  
  
## 语法  
  
```  
size_type size();  
```  
  
## 备注  
 成员函数返回控制序列的长度。  使用其当前确定元素的数目。控制序列。  如果您关注的是序列是否具有非零大小，请参见 [hash\_set::empty](../dotnet/hash-set-empty-stl-clr.md)`()`。  
  
## 示例  
  
```  
// cliext_hash_set_size.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size\(\) \= 以 3 为 3**  
**size\(\) \= 0。之后清除**  
**size\(\) \= 2 在" 2 "之后**   
## 要求  
 **页眉：** \<cliext\/hash\_set\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::empty](../dotnet/hash-set-empty-stl-clr.md)