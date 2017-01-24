---
title: "list::erase (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::erase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erase 成员 [STL/CLR]"
ms.assetid: 78705058-1e83-441d-b267-d4fb56451c0b
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::erase (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除指定位置处的元素。  
  
## 语法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### 参数  
 first  
 清除的范围开头。  
  
 last  
 清除的范围末尾。  
  
 where  
 要清除的元素。  
  
## 备注  
 第一个成员函数中移除`where`指向的控件序列元素 。  使用其删除一个元素。  
  
 第二个成员中移除函数控制元素在序列的范围的 `[``first``,` `last``)`。  您移除它使用零个或更多连续的元素。  
  
 前两个成员函数返回指定保持在所有移除元素外的第一个元素中的迭代器，或者 [list::end](../dotnet/list-end-stl-clr.md)`()`，如果不存在这样的元素。  
  
 当清除元素时，元素副本数是线性的中元素的数量。抹除的结尾和序列之间的接近结束的。\(当在序列中的任一端删除一个或多个元素，元素副本不发生。\)  
  
## 示例  
  
```  
// cliext_list_erase.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::list<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**erase\(begin\(\)\= b\)**  
 **b c d e**  
**erase\(begin\(\), end\(\)\-1\) \= e**  
**size\(\) \= 1**   
## 要求  
 **标头:** \<cliext\/list\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::clear](../dotnet/list-clear-stl-clr.md)