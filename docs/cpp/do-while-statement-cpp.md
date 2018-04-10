---
title: 执行-while 语句 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e03a20ad2b49d5c9337e0c8250e5d7c321ee882
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="do-while-statement-c"></a>do-while 语句 (C++)
执行*语句*重复直到指定的终止条件 (*表达式*) 计算结果为零。  
  
## <a name="syntax"></a>语法  
  
```  
do  
   statement  
while ( expression ) ;  
```  
  
## <a name="remarks"></a>备注  
 终止条件的测试将在每次执行循环后进行；因此 `do-while` 循环将执行一次或多次，具体取决于终止表达式的值。 `do-while`时，还可以终止语句[中断](../cpp/break-statement-cpp.md)， [goto](../cpp/goto-statement-cpp.md)，或[返回](../cpp/return-statement-cpp.md)在语句体中执行语句。  
  
 expression 必须具有算法或指针类型。 执行过程如下所示：  
  
1.  执行语句体。  
  
2.  接着，计算 expression。 如果 expression 为 false，则 `do-while` 语句将终止，控制将传递到程序中的下一条语句。 如果 expression 为 true（非零），则将从第 1 步开始重复此过程。  
  
## <a name="example"></a>示例  
 以下示例演示了 `do-while` 语句：  
  
```  
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