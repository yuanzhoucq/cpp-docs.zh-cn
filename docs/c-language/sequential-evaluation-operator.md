---
title: "顺序计算运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 59e3fa3daec861d580fda1d5605fdd33e7e955cc
ms.lasthandoff: 04/01/2017

---
# <a name="sequential-evaluation-operator"></a>顺序评估运算符
顺序计算运算符（也称为“逗号运算符”）按从左到右的顺序计算其两个操作数。  
  
## <a name="syntax"></a>语法  
 *expression*:  
 *assignment-expression*  
  
 *expression*  **,**  *assignment-expression*  
  
 顺序计算运算符的左操作数的计算结果为 `void` 表达式。 该运算的结果与右操作数具有相同的值和类型。 所有操作数都可以是任意类型。 顺序计算运算符在其操作数之间不执行类型转换，也不产生左值。 第一个操作数后有一个序列点，这意味着来自左操作数的计算的所有副作用在开始右操作数的计算前已完成。 有关详细信息，请参阅[序列点](../c-language/c-sequence-points.md)。  
  
 顺序计算运算符通常用于计算只允许有一个表达式的上下文中的两个或多个表达式。  
  
 逗号可以在上下文中用作分隔符。 但是，您务必小心，不要混淆将逗号用作分隔符与将逗号用作运算符；这两种用法完全不同。  
  
## <a name="example"></a>示例  
 以下示例演示顺序计算运算符：  
  
```  
for ( i = j = 1; i + j < 20; i += i, j-- );  
```  
  
 在本示例中，**for** 语句的第三个表达式的每个操作数都是单独计算的。 首先计算左操作数 `i += i`，然后计算右操作数 `j--`。  
  
```  
func_one( x, y + 2, z );  
func_two( (x--, y + 2), z );  
```  
  
 在对 `func_one` 的函数调用中，将传递以逗号分隔的三个参数：`x`、`y + 2` 和 `z`。 在对 `func_two` 的函数调用中，圆括号强制编译器将第一个逗号解释为顺序计算运算符。 此函数调用将两个参数传递给 `func_two`。 第一个参数是顺序计算运算 `(x--, y + 2)` 的结果，具有表达式 `y + 2` 的值和类型；第二个参数为 `z`。  
  
## <a name="see-also"></a>另请参阅  
 [逗号运算符：,](../cpp/comma-operator.md)