---
title: "multimap::key_compare (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::key_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_compare 成员 [STL/CLR]"
ms.assetid: a6b04cfa-fef9-44dc-a328-1208fd01899f
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# multimap::key_compare (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

两个键的排序委托。  
  
## 语法  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
## 备注  
 类型确定其排序关键字变量委托的同义词。  
  
## 示例  
  
```  
// cliext_multimap_key_compare.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    Mymultimap::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymultimap c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
  **比较\(L'a', L'a'\) \= False**  
**比较 \(L'a，L'b\) \= true**  
**比较\(L'b', L'a'\) \= False**  
**比较\(L'a', L'a'\) \= False**  
**比较\(L'a', L'b'\) \= False**  
**比较\(L'b', L'a'\) \= True**   
## 要求  
 **标头:** \<cliext\/map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::key\_comp](../dotnet/multimap-key-comp-stl-clr.md)   
 [multimap::key\_type](../dotnet/multimap-key-type-stl-clr.md)   
 [multimap::value\_compare](../dotnet/multimap-value-compare-stl-clr.md)