---
title: "multimap::upper_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "upper_bound 成员 [STL/CLR]"
ms.assetid: bfb8cf64-cecf-4685-8ac9-e7228ecee809
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

查找与指定的键范围的末尾。  
  
## 语法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### 参数  
 键  
 搜索的键值。  
  
## 备注  
 成员函数确定。具有相同订单给 `key`的控制序列中的最后一个 `X`。  如果不存在此类元素，或者，如果 `X` 位于控制序列中的最后一个元素，则返回`()`; [multimap::end](../dotnet/multimap-end-stl-clr.md)否则它返回指定除 `X`外的第一个元素的次数的迭代器。  使用其当前找到的元素序列的末尾与指定的键在控制序列。  
  
## 示例  
  
```  
// cliext_multimap_upper_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Mymultimap::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**upper\_bound\(L'x'\)\=\=end\(\) 为 True**  
**\*upper\_bound \(\=\) L'a \[b 2\]**  
**\*upper\_bound \(\=\) L'b \[c 3\]**   
## 要求  
 **页眉：** \<\/cliext 映射\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::count](../dotnet/multimap-count-stl-clr.md)   
 [multimap::equal\_range](../dotnet/multimap-equal-range-stl-clr.md)   
 [multimap::find](../dotnet/multimap-find-stl-clr.md)   
 [multimap::lower\_bound](../dotnet/multimap-lower-bound-stl-clr.md)