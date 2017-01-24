---
title: "__restrict | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__restrict"
  - "__restrict_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__restrict 关键字 [C++]"
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __restrict
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

与 **\_\_declspec \( [restrict](../cpp/restrict.md) \)** 修饰符一样，`__restrict` 关键字指示某个符号在当前范围中未使用别名。  `__restrict` 关键字与 `__declspec ( restrict )` 修饰符在下列方面不同：  
  
-   `__restrict` 关键字仅对变量有效，而 `__declspec ( restrict )` 仅对函数声明和函数定义有效。  
  
-   `__restrict` 类似于 C99 规范中的 `restrict`，但 `__restrict` 可在 C\+\+ 或 C 程序中使用。  
  
-   使用 `__restrict` 时，编译器将不会传播变量的非别名属性。  即，如果你向非 `__restrict` 变量分配 `__restrict` 变量，则编译器仍允许非 \_\_restrict 变量使用别名。  这与 C99 规范中的 `restrict` 关键字的行为不同。  
  
 通常，如果你影响整个函数的行为，则使用 `__declspec ( restrict )` 要好过使用关键字。  
  
 在 Visual Studio 2015 及更高版本中，可以对 C\+\+ 引用使用 `__restrict`。  
  
> [!NOTE]
>  在同时包含 [volatile](../cpp/volatile-cpp.md) 关键字的变量上使用时，`volatile` 将优先。  
  
## 示例  
  
```  
// __restrict_keyword.c  
// compile with: /LD  
// In the following function, declare a and b as disjoint arrays  
// but do not have same assurance for c and d.  
void sum2(int n, int * __restrict a, int * __restrict b,   
          int * c, int * d) {  
   int i;  
   for (i = 0; i < n; i++) {  
      a[i] = b[i] + c[i];  
      c[i] = b[i] + d[i];  
    }  
}  
  
// By marking union members as __restrict, tell compiler that  
// only z.x or z.y will be accessed in any given scope.  
union z {  
   int * __restrict x;  
   double * __restrict y;  
};  
```  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)