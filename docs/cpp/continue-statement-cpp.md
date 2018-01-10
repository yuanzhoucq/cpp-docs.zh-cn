---
title: "继续语句 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: continue_cpp
dev_langs: C++
helpviewer_keywords: continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3e4dd91489bfe22fca875f98110dadcb75def39d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="continue-statement-c"></a>continue 语句 (C++)
强制控件的传输到的控制表达式的最小封闭[执行](../cpp/do-while-statement-cpp.md)，[为](../cpp/for-statement-cpp.md)，或[时](../cpp/while-statement-cpp.md)循环。  
  
## <a name="syntax"></a>语法  
  
```  
continue;  
```  
  
## <a name="remarks"></a>备注  
 将不会执行当前迭代中的所有剩余语句。 确定循环的下一次迭代，如下所示：  
  
-   在 `do` 或 `while` 循环中，下一个迭代首先会重新计算 `do` 或 `while` 语句的控制表达式。  
  
-   在 `for` 循环中（使用语法 `for`(`init-expr`; `cond-expr`; `loop-expr`)），将执行 `loop-expr` 子句。 然后，重新计算 `cond-expr` 子句，并根据结果确定该循环结束还是进行另一个迭代。  
  
 下面的示例演示了如何使用 `continue` 语句跳过代码部分并启动循环的下一个迭代。  
  
## <a name="example"></a>示例  
  
```  
// continue_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        i++;  
        printf_s("before the continue\n");  
        continue;  
        printf("after the continue, should never print\n");  
     } while (i < 3);  
  
     printf_s("after the do loop\n");  
}  
```  
  
```Output  
before the continue  
before the continue  
before the continue  
after the do loop  
```  
  
## <a name="see-also"></a>请参阅  
 [跳转语句](../cpp/jump-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)