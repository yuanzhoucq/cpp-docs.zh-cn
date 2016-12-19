---
title: "编译器错误 C2385 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2385"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2385"
ms.assetid: 6d3dd1f2-e56d-49d7-865c-6a9acdb17417
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2385
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”的访问不明确  
  
 该成员可从多个对象派生（它是从多个对象继承的）。要解决此错误,  
  
-   通过提供转换使成员明确。  
  
-   在基类中重命名不明确的成员。  
  
## 示例  
 下面的示例生成 C2385。  
  
```  
// C2385.cpp  
// C2385 expected  
#include <stdio.h>  
  
struct A   
{  
    void x(int i)   
    {  
        printf_s("\nIn A::x");  
    }  
};  
  
struct B   
{  
    void x(char c)   
    {  
        printf_s("\nIn B::x");  
    }  
};  
  
// Delete the following line to resolve.  
struct C : A, B {}  
  
// Uncomment the following 4 lines to resolve.  
// struct C : A, B   
// {  
//     using B::x;  
//     using A::x;  
// };  
  
int main()   
{  
    C aC;  
    aC.x(100);  
    aC.x('c');  
}  
  
struct C : A, B   
{  
    using B::x;  
    using A::x;  
};  
```