---
title: "collection_adapter::mapped_type (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::collection_adapter::mapped_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapped_type 成员 [STL/CLR]"
ms.assetid: eece6a47-611a-47d4-8dfc-cfbbc4aeb67b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# collection_adapter::mapped_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

字典的值的类型。  
  
## 语法  
  
```  
typedef Value mapped_type;  
```  
  
## 备注  
 类型是的同义词模板参数 `Value`，`IDictionary` 或 `IDictionary<Value>`中的专用化；为未定义。  
  
## 示例  
  
```  
// cliext_collection_adapter_mapped_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**   
## 要求  
 **页眉：** \<\/cliext 适配器\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)   
 [collection\_adapter::key\_type](../dotnet/collection-adapter-key-type-stl-clr.md)