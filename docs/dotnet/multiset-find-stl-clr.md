---
title: "multiset::find (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "find 成员 [STL/CLR]"
ms.assetid: 162c9002-fb34-44f9-8e42-6bacecd0ebbc
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::find (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找与指定键匹配的元素。  
  
## 语法  
  
```  
iterator find(key_type key);  
```  
  
#### 参数  
 键  
 要搜索的键值。  
  
## 备注  
 如果在控制序列的一个元素至少具有等效排序，使用 `key`成员函数返回指定这些元素之一的迭代器；否则返回`()`。[multiset::end](../dotnet/multiset-end-stl-clr.md) 使用它定位当前在控制序列中的一个元素，与指定键匹配。  
  
## 示例  
  
```  
// cliext_multiset_find.cpp   
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
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**查找 A \= false**  
**查找b \= b**  
**查找 C \= False**   
## 说明  
 请注意 `find` 不能保证它找到的若干元素。  
  
## 要求  
 **标头:** \<cliext\/set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::equal\_range](../dotnet/multiset-equal-range-stl-clr.md)   
 [multiset::lower\_bound](../dotnet/multiset-lower-bound-stl-clr.md)   
 [multiset::upper\_bound](../dotnet/multiset-upper-bound-stl-clr.md)