---
title: "编译器警告 （等级 2） C4146 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4146
dev_langs: C++
helpviewer_keywords: C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d7a9a67beb4dc122c25318c1796e22a4c35dbe38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4146"></a>编译器警告 （等级 2） C4146
一元减号运算符应用于无符号类型，结果仍未签名  
  
 无符号的类型可以保存仅非负值，因此，在一元负运算 （求反） 没有通常意义时应用于无符号类型。 操作数和结果为非负值。  
  
 实际上，当程序员试图表达最小整数值，该值是介于-2147483648 发生此问题。 不能作为介于-2147483648 写入此值，因为表达式处理分两个阶段：  
  
1.  数字 2147483648 进行计算。 因为它是大于 2147483647 的最大整数值，2147483648 的类型不是[int](../../c-language/integer-types.md)，但`unsigned int`。  
  
2.  一元负应用于的值，与无符号的结果，也会发生要 2147483648。  
  
 结果的无符号的类型可能导致意外的行为。 如果在比较中，使用该结果，则可能会使用的无符号的比较，例如，当另一个操作数是`int`。 本部分说明为什么下面的示例程序将打印只需编写一行。  
  
 预期的第二个行， `1 is greater than the most negative int`，未输出，因为`((unsigned int)1) > 2147483648`为 false。  
  
 你可以通过从 limits.h，具有类型使用 INT_MIN 避免 C4146**带符号整型**。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4146:  
  
```  
// C4146.cpp  
// compile with: /W2  
#include <stdio.h>  
  
void check(int i)   
{  
    if (i > -2147483648)   // C4146  
        printf_s("%d is greater than the most negative int\n", i);  
}  
  
int main()   
{  
    check(-100);  
    check(1);  
}  
```