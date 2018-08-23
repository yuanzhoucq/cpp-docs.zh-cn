---
title: 表达式语句 (C) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18d28cdc695ae600616d63575328eeaf171bc28c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385892"
---
# <a name="expression-statement-c"></a>表达式语句 (C)
在执行表达式语句时，将根据[表达式和赋值](../c-language/expressions-and-assignments.md)中概述的规则来计算表达式。  
  
## <a name="syntax"></a>语法  
 expression-statement：  
 expression opt;  
  
 在执行下一个语句前，完成表达式计算的所有副作用。 空表达式语句被称为 null 语句。 有关详细信息，请参阅 [Null 语句](../c-language/null-statement-c.md)。  
  
 这些示例演示了表达式语句。  
  
```  
x = ( y + 3 );            /* x is assigned the value of y + 3  */  
x++;                      /* x is incremented                  */  
x = y = 0;                /* Both x and y are initialized to 0 */  
proc( arg1, arg2 );       /* Function call returning void      */  
y = z = ( f( x ) + 3 );   /* A function-call expression        */  
```  
  
 在最后一个语句中，函数调用表达式的值（包括函数返回的任何值）增加 3，然后被赋给变量 `y` 和 `z`。  
  
## <a name="see-also"></a>请参阅  
 [语句](../c-language/statements-c.md)