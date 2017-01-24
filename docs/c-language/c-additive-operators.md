---
title: "C 加法运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "+ 运算符, 加法运算符"
  - "加法运算符"
  - "算术运算符 [C++], 加法运算符"
  - "运算符 [C], 加法"
  - "常用算术转换"
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 加法运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

相加运算符执行加法 \(**\+**\) 和减法 \(**–**\) 运算。  
  
## 语法  
 *additive\-expression*:  
 *multiplicative\-expression*  
  
 *additive\-expression*  **\+**  *multiplicative\-expression*  
  
 *additive\-expression*  **–**  *multiplicative\-expression*  
  
> [!NOTE]
>  虽然 *additive\-expression* 的语法包括 *multiplicative\-expression*，但这并不表示需要使用乘法的表达式。  对于 *multiplicative\-expression*、*cast\-expression* 和 *unary\-expression*，请参阅 [C 语言语法摘要](../c-language/c-language-syntax-summary.md)中的语法。  
  
 操作数可以是整型值或浮点值。  还可以对指针值执行一些加法运算，如针对每个运算符的讨论中所述。  
  
 相加运算符对整型和浮点型操作数执行常用算术转换。  结果的类型是转换后操作数的类型。  由于相加运算符执行的转换不提供溢出或下溢条件，因此，如果在转换后，无法用操作数类型表示加法运算的结果，则信息可能会丢失。  
  
## 请参阅  
 [加法运算符：\+ 和 \-](../cpp/additive-operators-plus-and.md)