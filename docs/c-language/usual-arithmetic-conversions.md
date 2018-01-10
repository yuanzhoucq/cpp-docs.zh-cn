---
title: "常用算术转换 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- arithmetic conversions [C++]
- type conversion [C++], arithmetic
- operators [C], arithmetic conversions
- data type conversion [C++], arithmetic
- conversions [C++], arithmetic
- arithmetic operators [C++], type conversions
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a73da6d96b0dc03fa3f4c4807d6a2dff4fef2879
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="usual-arithmetic-conversions"></a>常用算术转换
大多数 C 运算符执行类型转换以将表达式的操作数引入常见类型或将较短的值扩展到计算机运算中使用的整数大小。    C 运算符执行的转换取决于特定的运算符和操作数的类型。 但是，许多运算符对整型和浮点型的操作数执行相似的转换。 这些转换称为“算术转换”。 从操作数值到兼容类型的转换会导致不改变其值。  
  
 以下汇总的算术转换称为“常用算术转换”。 这些步骤仅应用于需要算术类型的二元运算符。 目的是为了产生常见类型（它也是结果的类型）。 若要确定实际执行的转换，编译器可将以下算法应用于表达式中的二元运算。 下面的步骤不具有优先级。  
  
1.  如果任一操作数是 `long double` 类型，则将另一个操作数转换为 `long double` 类型。  
  
2.  如果未满足上述条件，并且任一操作数是 double 类型，则将另一个操作数转换为 double 类型。  
  
3.  如果未满足上述两个条件，并且任一操作数是 float 类型，则将另一个操作数转换为 float 类型。  
  
4.  如果未满足上述三个条件（所有操作数都不是浮点型），则对操作数执行整型转换，如下所示：  
  
    -   如果任一操作数是 `unsigned long` 类型，则将另一个操作数转换为 `unsigned long` 类型。  
  
    -   如果未满足上述条件，并且任一操作数是 long 类型且另一个操作数是 `unsigned int` 类型，则将两个操作数都转换为 `unsigned long` 类型。  
  
    -   如果未满足上述两个条件，并且任一操作数是 long 类型，则将另一个操作数转换为 long 类型。  
  
    -   如果未满足上述三个条件，并且任一操作数是 `unsigned int`类型，则将另一个操作数转换为 `unsigned int` 类型。  
  
    -   如果未满足上述任何条件，则将两个操作数转换为 `int` 类型。  
  
 以下代码阐释了这些转换规则：  
  
```  
float   fVal;  
double  dVal;  
int   iVal;  
unsigned long ulVal;  
  
dVal = iVal * ulVal; /* iVal converted to unsigned long  
                      * Uses step 4.  
                      * Result of multiplication converted to double   
                      */  
dVal = ulVal + fVal; /* ulVal converted to float  
                      * Uses step 3.  
                      * Result of addition converted to double   
                      */   
```  
  
## <a name="see-also"></a>请参阅  
 [C 运算符](../c-language/c-operators.md)