---
title: "multiset::lower_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multiset::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lower_bound 成员 [STL/CLR]"
ms.assetid: 5e3d1ba0-8b03-436e-b502-dbdb764f452b
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# multiset::lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找与指定的键范围的开头。  
  
## 语法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### 参数  
 键  
 要搜索的键值。  
  
## 备注  
 成员函数确定。具有相同订单给 `key`的控制序列中的第一个 `X` 元素。  如果不存在此类元素，则返回`()`; [multiset::end](../dotnet/multiset-end-stl-clr.md)否则它返回将 `X`的迭代器。  使用其当前找到的元素序列的开头与指定的键在控制序列。  
  
## 示例  
  
```  
// cliext_multiset_lower_bound.cpp   
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
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
  **a b c**  
**lower\_bound\(L'x'\)\=\=end\(\) \= True**  
**\*lower\_bound\(L'a'\) \= a**  
**\*lower\_bound \(L'b \= b\)**   
## 要求  
 **标头:** \<cliext\/set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::count](../dotnet/multiset-count-stl-clr.md)   
 [multiset::equal\_range](../dotnet/multiset-equal-range-stl-clr.md)   
 [multiset::find](../dotnet/multiset-find-stl-clr.md)   
 [multiset::upper\_bound](../dotnet/multiset-upper-bound-stl-clr.md)