---
title: "__restrict |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __restrict_cpp
dev_langs: C++
helpviewer_keywords: __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6e854c87355831980f768fd0027f8ac70d9001a1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="restrict"></a>__restrict
如**__declspec ([限制](../cpp/restrict.md))**修饰符，`__restrict`关键字指示某个符号是否不在当前范围中的有别名。 `__restrict` 关键字与 `__declspec ( restrict )` 修饰符在下列方面不同：  
  
-   `__restrict` 关键字仅对变量有效，而 `__declspec ( restrict )` 仅对函数声明和函数定义有效。  
  
-   `__restrict` 类似于 C99 规范中的 `restrict`，但 `__restrict` 可在 C++ 或 C 程序中使用。  
  
-   使用 `__restrict` 时，编译器将不会传播变量的非别名属性。 即，如果你向非 `__restrict` 变量分配 `__restrict` 变量，则编译器仍允许非 __restrict 变量使用别名。 这与 C99 规范中的 `restrict` 关键字的行为不同。  
  
 通常，如果你影响整个函数的行为，则使用 `__declspec ( restrict )` 要好过使用关键字。  
  
 在 Visual Studio 2015 及更高版本中，可以对 C++ 引用使用 `__restrict`。  
  
> [!NOTE]
>  此外具有的变量上使用时[易失性](../cpp/volatile-cpp.md)关键字，`volatile`将优先。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)