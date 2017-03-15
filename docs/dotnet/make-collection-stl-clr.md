---
title: "make_collection (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::make_collection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_collection 函数 [STL/CLR]"
ms.assetid: c25fb0cb-ebd8-4198-a565-bad28d32ee19
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# make_collection (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从一个迭代器对执行 `range_adapter`。  
  
## 语法  
  
```  
template<typename Iter>  
    range_adapter<Iter> make_collection(Iter first, Iter last);  
```  
  
#### 参数  
 Iter  
 包装的迭代器的类型。  
  
 首先  
 包装的第一个迭代器。  
  
 last  
 包装的第二个迭代器。  
  
## 备注  
 模板函数返回 `gcnew range_adapter<Iter>(``first``,` `last``)`。  使用它从一个对 `range_adapter`对象`<Iter>` 迭代器。  
  
## 示例  
  
```  
// cliext_make_collection.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in d1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Collections::ICollection^ p1 =   
        cliext::make_collection(d1.begin(), d1.end());   
    System::Console::WriteLine("Count = {0}", p1->Count);   
    System::Console::WriteLine("IsSynchronized = {0}",   
        p1->IsSynchronized);   
    System::Console::WriteLine("SyncRoot not nullptr = {0}",   
        p1->SyncRoot != nullptr);   
  
// copy the sequence   
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);   
  
    a1[0] = L'|';   
    p1->CopyTo(a1, 1);   
    a1[4] = L'|';   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **a b c**  
**计数为 3**  
**IsSynchronized \= false**  
**不是 SyncRoot nullptr 为 True**  
 **&#124;为 c&#124;**   
## 要求  
 **页眉：** \<\/cliext 适配器\>  
  
 **命名空间：** cliext  
  
## 请参阅  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)