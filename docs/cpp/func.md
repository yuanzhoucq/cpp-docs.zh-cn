---
title: "__func__ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__func__"
  - "__func___cpp"
dev_langs: 
  - "C++"
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# __func__
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\(C\+\+11\)** 预定义标识符 \_\_func\_\_ 隐式定义为包含封闭函数的未限定和未修饰名称的字符串。  \_\_func\_\_ 由 c \+ \+ 标准规定，且不是 Microsoft 扩展。  
  
## 语法  
  
```vb  
__func__  
```  
  
## 返回值  
 返回以 null 结尾的 const char 字符数组，该数组包含函数名称。  
  
## 示例  
  
```  
  
#include <string>  
#include <iostream>  
  
namespace Test  
{  
    struct Foo  
    {  
        static void DoSomething(int i, std::string s)  
        {  
           std::cout << __func__ << std::endl; // Output: DoSomething  
        }  
    };  
}  
int main()  
{  
    Test::Foo::DoSomething(42, "Hello");  
  
    return 0;  
}  
  
```  
  
## 要求  
 C\+\+11