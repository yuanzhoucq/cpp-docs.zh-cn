---
title: "C 常量表达式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 596f558ea5c22f1850800d95b0d4ad0b5edd6a8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="c-constant-expressions"></a>C 常量表达式
常量表达式将在编译时而不是运行时计算，并且可在可使用常量的任何位置使用。 常量表达式的计算结果必须是位于该类型的可表示值范围内的常量。 常量表达式的操作数可以是整数常量、字符常量、浮点常量、枚举常量、类型强制转换、`sizeof` 表达式和其他常量表达式。  
  
## <a name="syntax"></a>语法  
 *constant-expression*:  
 *conditional-expression*  
  
 *conditional-expression*:  
 *logical-OR-expression*  
  
 *logical-OR-expression* **?**  *expression* **:**  *conditional-expression*  
  
 *expression*:  
 *assignment-expression*  
  
 *expression* **,**  *assignment-expression*  
  
 *assignment-expression*:  
 *conditional-expression*  
  
 *unary-expression assignment-operator assignment-expression*  
  
 *assignment-operator*: one of  
 **= \*= /= %= += -= <\<= >>= &= ^= &#124;=**  
  
 结构声明符、枚举数、直接声明符、直接抽象声明符和标记语句的非终止符包含 *constant-expression* 非终止符。  
  
 整数常量表达式必须用于指定结构的位域成员的大小、枚举常量的值、数组的大小或 **case** 常量的值。  
  
 预处理器指令中使用的常量表达式受其他限制的约束。 因此，它们被称为“受限制的常量表达式”。 受限制的常量表达式不能包含 `sizeof` 表达式、枚举常量、到任何类型的类型强制转换或浮点类型常量。 但它可包含特殊常量表达式 `defined (`identifier`)`。  
  
## <a name="see-also"></a>请参阅  
 [操作数和表达式](../c-language/operands-and-expressions.md)