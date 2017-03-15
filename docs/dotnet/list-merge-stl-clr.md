---
title: "list::merge (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::merge"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "merge 成员 [STL/CLR]"
ms.assetid: f8e93cd3-bd08-4086-859b-08a2899cc9a6
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# list::merge (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

合并两个有序受控序列。  
  
## 语法  
  
```  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### 参数  
 pred  
 比较器的元素对。  
  
 right  
 合并的容器。  
  
## 备注  
 第一个成员函数。移除所有元素顺序控制由 `right` 并插入它们控制在序列。  必须由 `operator<` 前面两个序列排序\-\-，当通过的任何序列，继续元素不能减小。值。  产生的序列。`operator<`还顺序。  使用该成员函数还将两个序列该增值到该的增值序列。  
  
 第二个成员函数行为与第一个相同，不同之处在于，`pred` 排序序列。\-\- `pred`的`(X, Y)` 必须是错误的。按照序列的 `Y` 元素的所有 `X` 元素。  使用将谓词函数进行排序的两个序列或委托指定。  
  
 两个函数以稳定的组合\-\-对原始序列中的元素控制在生成的控制序列不会撤消。  此外，如果，一对在生成的序列的元素控制 `X` 和 `Y` 具有相同订单\-\- `!(X < Y) && !(X < Y)` \-\-原始序列的元素控制在自的元素之前出现顺序控制的 `right`。  
  
## 示例  
  
```  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **" e.**  
 **a bc d f**  
 **a b c d e f**  
**c2.size\(\) \= 0**  
 **e.c。**  
 **f\-e 的 c d b。**  
 **f\-e 的 c d、b 和 c**  
**c1.size\(\) \= 0**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::sort](../dotnet/list-sort-stl-clr.md)   
 [list::splice](../dotnet/list-splice-stl-clr.md)