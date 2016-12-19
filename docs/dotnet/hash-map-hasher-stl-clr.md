---
title: "hash_map::hasher (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::hasher"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hasher 成员 [STL/CLR]"
ms.assetid: 72e4c4c9-ea35-4f75-98bb-e53979706de1
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::hasher (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

键的哈希委托。  
  
## 语法  
  
```  
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>  
    hasher;  
```  
  
## 备注  
 类型描述转换一个键值到整数的委托。  
  
## 示例  
  
```  
// cliext_hash_map_hasher.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
  **hash\(L'a'\) \= 1616896120**  
**hash\(L'b'\) \= 570892832**   
## 要求  
 **标头:** \<cliext\/hash\_map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::hash\_delegate](../dotnet/hash-map-hash-delegate-stl-clr.md)