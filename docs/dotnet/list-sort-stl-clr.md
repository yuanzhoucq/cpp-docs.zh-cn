---
title: "list::sort (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::sort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sort 成员 [STL/CLR]"
ms.assetid: f811d5f4-a19e-4194-8765-1e68097c52f0
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# list::sort (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对受控序列进行排序。  
  
## 语法  
  
```  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### 参数  
 pred  
 比较器的元素对。  
  
## 备注  
 第一个成员函数重新排列控制序列的元素，以便由 `operator<` 排序\-\-，当通过序列，元素不继续减小。值。  使用该成员函数以递增的顺序排序的序列。  
  
 第二个成员函数行为与第一个相同，不同之处在于，`pred` 排序序列。\-\- `pred``(X, Y)` 用于按照为序列的元素的所有 `Y` 元素 `X` 为 false。  使用此顺序。通过谓词函数或委托指定的排序的序列。  
  
 两个函数执行一个稳定排序\-\-对原始序列在控件的元素在生成的控制序列不会撤消。  
  
## 示例  
  
```  
// cliext_list_sort.cpp   
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
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **c b。**  
 **a b c**   
## 要求  
 **页眉：** \<\/cliext 列表\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [list](../dotnet/list-stl-clr.md)   
 [list::merge](../dotnet/list-merge-stl-clr.md)   
 [list::reverse](../dotnet/list-reverse-stl-clr.md)   
 [list::splice](../dotnet/list-splice-stl-clr.md)   
 [list::unique](../dotnet/list-unique-stl-clr.md)