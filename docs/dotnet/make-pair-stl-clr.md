---
title: "make_pair (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::make_pair"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_pair 函数 [STL/CLR]"
ms.assetid: 74733f2c-97b0-4d69-b431-5ab8f0de9e3e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# make_pair (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从一对值执行 `pair`。  
  
## 语法  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### 参数  
 Value1  
 第一个包装值的类型。  
  
 Value2  
 第二个包装值的类型。  
  
 first  
 包装的第一个值。  
  
 第二个  
 其次包装的值。  
  
## 备注  
 模板函数返回  `pair<``Value1``,` `Value2``>(``first``,` `second``)`。  使用它通过一对键值构造 `pair``<``Value1``,` `Value2``>` 对象。  
  
## 示例  
  
```  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
  **\[x, 3\]**  
**\[y, 4\]**   
## 要求  
 **标头:** \<cliext\/utility\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)