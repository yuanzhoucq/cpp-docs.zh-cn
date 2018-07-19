---
title: 执行-while 语句 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do_cpp
dev_langs:
- C++
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2de180d58c31f4bd6c8b15eb69076b99f8b57b0
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942529"
---
# <a name="do-while-statement-c"></a>do-while 语句 (C++)
执行*语句*重复之前指定的终止条件 (*表达式*) 计算结果为零。  
  
## <a name="syntax"></a>语法  
  
```  
do  
   statement  
while ( expression ) ;  
```  
  
## <a name="remarks"></a>备注  
 在每次执行循环; 后进行终止条件的测试因此，**执行操作-虽然**循环将执行一个或多个时间，具体取决于终止表达式的值。 **执行操作-虽然**时，还可以终止语句[中断](../cpp/break-statement-cpp.md)， [goto](../cpp/goto-statement-cpp.md)，或[返回](../cpp/return-statement-cpp.md)在语句体中执行语句。  
  
 expression 必须具有算法或指针类型。 执行过程如下所示：  
  
1.  执行语句体。  
  
2.  接着，计算 expression。 如果*表达式*为 false，**执行-虽然**语句将终止，控制权将传递给程序中的下一个语句。 如果 expression 为 true（非零），则将从第 1 步开始重复此过程。  
  
## <a name="example"></a>示例  
 下面的示例演示如何**执行操作-虽然**语句：  
  
```cpp 
// do_while_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        printf_s("\n%d",i++);  
    } while (i < 3);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [迭代语句](../cpp/iteration-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [while Statement (C++)](../cpp/while-statement-cpp.md) （while 语句 (C++)）  
 [for 语句 (C++)](../cpp/for-statement-cpp.md)   
 [基于范围的 for 语句 (C++)](../cpp/range-based-for-statement-cpp.md)