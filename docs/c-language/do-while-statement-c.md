---
title: do-while 语句 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do
- while
dev_langs:
- C++
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0638e10d87ed52de49b027aea1e06bee838867d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385427"
---
# <a name="do-while-statement-c"></a>do-while 语句 (C)
利用 `do-while` 语句，您可以重复语句或复合语句，直到指定的表达式的计算结果为 false。  
  
## <a name="syntax"></a>语法  
 *iteration-statement*:  
 do  statement  while (  expression  ) ;  
  
 在执行循环体后，将计算 `do-while` 语句中的 expression。 因此，总是至少执行一次循环体。  
  
 expression 必须具有算法或指针类型。 执行过程如下所示：  
  
1.  执行语句体。  
  
2.  接着，计算 expression。 如果 expression 为 false，则 `do-while` 语句将终止，控制将传递到程序中的下一条语句。 如果 expression 为 true（非零），则将从第 1 步开始重复此过程。  
  
 当 break、`goto` 或 `return` 语句在语句体中执行时，`do-while` 语句也会终止。  
  
 以下是 `do-while` 语句的示例：  
  
```  
do   
{  
    y = f( x );  
    x--;  
} while ( x > 0 );  
```  
  
 在此 `do-while` 语句中，无论 `y = f( x );` 的初始值是什么，`x--;` 和 `x` 这两个语句都会执行。 然后将计算 `x > 0`。 如果 `x` 大于 0，则会再次执行语句体并重新计算 `x > 0`。 只要 `x` 保持大于 0，语句主体就会重复执行。 当 `do-while` 变为 0 或负值时，`x` 语句的执行将终止。 将至少执行一次循环体。  
  
## <a name="see-also"></a>请参阅  
 [do-while 语句 (C++)](../cpp/do-while-statement-cpp.md)