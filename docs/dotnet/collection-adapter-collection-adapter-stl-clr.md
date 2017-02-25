---
title: "collection_adapter::collection_adapter (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::collection_adapter"
  - "cliext::collection_adapter::collection_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collection_adapter 成员 [STL/CLR]"
ms.assetid: 7e2bb75b-d735-4135-9523-719683e06fe9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# collection_adapter::collection_adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造适配器对象。  
  
## 语法  
  
```  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### 参数  
 集合  
 包装 BCL 句柄。  
  
 right  
 要复制的对象。  
  
## 备注  
 构造函数：  
  
 `collection_adapter();`  
  
 初始化用 `nullptr`的存储的句柄。  
  
 构造函数：  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 初始化用`right``.`[collection\_adapter::base](../dotnet/collection-adapter-base-stl-clr.md)`()`的存储的句柄。  
  
 构造函数：  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 初始化用 `right``->`[collection\_adapter::base](../dotnet/collection-adapter-base-stl-clr.md)`()`的存储的句柄。  
  
 构造函数：  
  
 `collection_adapter(Coll^ collection);`  
  
 初始化包含具有 `collection`的存储的句柄。  
  
## 示例  
  
```  
// cliext_collection_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
  
// construct an empty container   
    Mycoll c1;   
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);   
  
// construct with a handle   
    Mycoll c2(%d6x);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **base\(\) 空为 True**  
 **x x x x x x**  
 **x x x x x x**  
 **x x x x x x**   
## 要求  
 **标头:** \<cliext\/adapter\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)   
 [collection\_adapter::operator\=](../dotnet/collection-adapter-operator-assign-stl-clr.md)