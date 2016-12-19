---
title: "hash_set::hash_delegate (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::hash_delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_delegate 成员 [STL/CLR]"
ms.assetid: 34e39d2d-f2ef-4755-9201-3cdb4e41ea56
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::hash_delegate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找与指定键匹配的元素。  
  
## 语法  
  
```  
hasher^ hash_delegate();  
```  
  
## 备注  
 成员函数返回委托用于转换一个键值为整数。  使用该哈希键。  
  
## 示例  
  
```  
// cliext_hash_set_hash_delegate.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
  **hash\(L'a'\) \= 1616896120**  
**哈希 \(L'b\)\/570892832**   
## 要求  
 **标头:** \<cliext\/hash\_set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::hasher](../dotnet/hash-set-hasher-stl-clr.md)