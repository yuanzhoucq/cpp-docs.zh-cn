---
title: "一元加号和非运算符：+ 和 - | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "+"
  - "-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "- 运算符"
  - "+ 运算符"
  - "+ 运算符, 一元运算符"
  - "非运算符"
  - "一元运算符, plus"
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一元加号和非运算符：+ 和 -
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
+ cast-expression  
```  
  
```  
  
- cast-expression  
  
```  
  
## \+ 运算符  
 一元加运算符 \(**\+**\) 的结果是其操作数的值。  一元加运算符的操作数必须是一个算术类型。  
  
 整型提升是对整型操作数执行的。  结果类型是操作数将提升到的类型。  因此，表达式 `+ch`（其中 `ch` 的类型为 `char`）的结果类型为 `int`；值不会进行修改。  有关提升是如何完成的详细信息，请参阅[整型提升](../misc/integral-promotions.md)。  
  
## \- 运算符  
 一元求反运算符 \(**–**\) 生成其操作数的负数。  一元求反运算符的操作数必须是算术类型。  
  
 将对整型操作数执行整型提升，并且结果类型将是操作数将提升到的类型。  有关如何执行提升的详细信息，请参阅[整型提升](../misc/integral-promotions.md)。  
  
## Microsoft 专用  
 通过从 2^n 中减去操作数的值来执行无符号数量的一元求反运算，其中 n 是给定的无符号类型的对象的位数。  （Microsoft C\+\+ 运行于利用 2 的补数算法的处理器上。  在其他处理器上，负数的算法可以不同。）  
  
## 请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)