---
title: "一元加号和非运算符: + 和-|Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs: C++
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12aba6e13f10d05c8559439427d2d28bcdad089d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="unary-plus-and-negation-operators--and--"></a>一元加号和非运算符：+ 和 -
## <a name="syntax"></a>语法  
  
```  
  
+ cast-expression  
```  
  
```  
  
- cast-expression  
```  
  
## <a name="-operator"></a>+ 运算符  
 一元加运算符的结果 (**+**) 是其操作数的值。 一元加运算符的操作数必须是一个算术类型。  
  
 整型提升是对整型操作数执行的。 结果类型是操作数将提升到的类型。 因此，表达式 `+ch`（其中 `ch` 的类型为 `char`）的结果类型为 `int`；值不会进行修改。 请参阅[标准转换](standard-conversions.md)有关如何完成提升的详细信息。  
  
## <a name="--operator"></a>- 运算符  
 一元求反运算符 (**-**) 生成其操作数的负值。 一元求反运算符的操作数必须是算术类型。  
  
 将对整型操作数执行整型提升，并且结果类型将是操作数将提升到的类型。 请参阅[标准转换](standard-conversions.md)有关如何执行提升的详细信息。  
  
## <a name="microsoft-specific"></a>Microsoft 专用  
 通过从 2^n 中减去操作数的值来执行无符号数量的一元求反运算，其中 n 是给定的无符号类型的对象的位数。 （Microsoft C++ 运行于利用 2 的补数算法的处理器上。 在其他处理器上，负数的算法可以不同。）  
  
## <a name="see-also"></a>请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)