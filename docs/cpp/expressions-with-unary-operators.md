---
title: "使用一元运算符的表达式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "表达式 [C++], 运算符"
  - "表达式 [C++], 一元运算符"
  - "一元运算符, 表达式，具有"
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用一元运算符的表达式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一元运算符仅作用于表达式中的某个操作数。  一元运算符如下所示：  
  
-   [间接运算符 \(\*\)](../cpp/indirection-operator-star.md)  
  
-   [Address\-of 运算符 \(&\)](../cpp/address-of-operator-amp.md)  
  
-   [一元加运算符 \(\+\)](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [一元求反运算符 \(–\)](../misc/unary-negation-operator.md)  
  
-   [逻辑求反运算符 \(\!\)](../cpp/logical-negation-operator-exclpt.md)  
  
-   [二进制反码运算符 \(~\)](../cpp/one-s-complement-operator-tilde.md)  
  
-   [前缀递增运算符 \(\+\+\)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [前缀减量运算符 \(––\)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [强制转换运算符 \(\)](../cpp/cast-operator-parens.md)  
  
-   [sizeof 运算符](../cpp/sizeof-operator.md)  
  
-   [\_\_uuidof 运算符](../cpp/uuidof-operator.md)  
  
-   [\_\_alignof 运算符](../cpp/alignof-operator.md)  
  
-   [new 运算符](../cpp/new-operator-cpp.md)  
  
-   [delete 运算符](../cpp/delete-operator-cpp.md)  
  
 这些运算符具有从右向左的关联性。  一元表达式通常涉及后缀或主表达式前面的语法。  
  
 下面是一元表达式的可能的形式。  
  
-   *postfix\-expression*  
  
-   `++` *unary\-expression*  
  
-   `––` *unary\-expression*  
  
-   *unary\-operator* *cast\-expression*  
  
-   `sizeof` *unary\-expression*  
  
-   `sizeof(` *type\-name* `)`  
  
-   `decltype(` *expression* `)`  
  
-   *allocation\-expression*  
  
-   *deallocation\-expression*  
  
 任何 *postfix\-expression* 均被视为 *unary\-expression*，因为任何主表达式被视为 *postfix\-expression*，并且任何主表达式也被视为 *unary\-expression*。  有关详细信息，请参阅[后缀表达式](../cpp/postfix-expressions.md)和[主表达式](../cpp/primary-expressions.md)。  
  
 *unary\-operator* 包含以下一个或多个符号：`* &` `+` `–` `!` `~`  
  
 *cast\-expression* 是具有用来更改类型的可选强制转换的一元表达式。  有关详细信息，请参阅[强制转换运算符：\(\)](../cpp/cast-operator-parens.md)。  
  
 *expression* 可以是任何表达式。  有关详细信息，请参阅[表达式](../cpp/expressions-cpp.md)。  
  
 *allocation\-expression* 引用 `new` 运算符。  *deallocation\-expression* 引用 `delete` 运算符。  有关详细信息，请参阅本主题前面的链接。  
  
## 请参阅  
 [表达式的类型](../cpp/types-of-expressions.md)