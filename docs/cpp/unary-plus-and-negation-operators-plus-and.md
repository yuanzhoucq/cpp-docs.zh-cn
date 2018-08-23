---
title: '一元加号和非运算符: + 和-|Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs:
- C++
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06e7f6bd089866619d82798bb220580e8a11b04b
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460888"
---
# <a name="unary-plus-and-negation-operators--and--"></a>一元加号和非运算符：+ 和 -
## <a name="syntax"></a>语法  
  
```  
+ cast-expression  
- cast-expression  
```  
  
## <a name="-operator"></a>+ 运算符  
 一元加运算符的结果 (**+**) 是其操作数的值。 一元加运算符的操作数必须是一个算术类型。  
  
 整型提升是对整型操作数执行的。 结果类型是操作数将提升到的类型。 因此，表达式`+ch`，其中`ch`属于类型**char**，导致类型**int**; 的值是未修改。 请参阅[标准转换](standard-conversions.md)有关如何完成提升的详细信息。  
  
## <a name="--operator"></a>- 运算符  
 一元求反运算符 (**-**) 生成其操作数的负值。 一元求反运算符的操作数必须是算术类型。  
  
 将对整型操作数执行整型提升，并且结果类型将是操作数将提升到的类型。 请参阅[标准转换](standard-conversions.md)有关如何执行提升的详细信息。  
  
## <a name="microsoft-specific"></a>Microsoft 专用  
 通过从 2^n 中减去操作数的值来执行无符号数量的一元求反运算，其中 n 是给定的无符号类型的对象的位数。
  
## <a name="see-also"></a>请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)