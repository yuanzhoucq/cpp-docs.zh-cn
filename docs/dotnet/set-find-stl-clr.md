---
title: "set::find (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "find 成员 [STL/CLR]"
ms.assetid: 916e581c-2815-4c07-a51a-6c5ddfa730c1
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# set::find (STL/CLR)
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
 如果在控制序列的一个元素至少具有等效排序，使用 `key`成员函数返回指定这些元素之一的迭代器；否则返回`()`。[set::end](../dotnet/set-end-stl-clr.md) 使用该属性当前设置一个元素位于与指定键的顺序控制。  
  
## 示例  
  
```  
// cliext_set_find.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
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
 请注意 `find` 不若干元素看起来的保证。  
  
## 要求  
 **标头:** \<cliext\/set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [集合](../dotnet/set-stl-clr.md)   
 [set::equal\_range](../dotnet/set-equal-range-stl-clr.md)   
 [set::lower\_bound](../dotnet/set-lower-bound-stl-clr.md)   
 [set::upper\_bound](../dotnet/set-upper-bound-stl-clr.md)