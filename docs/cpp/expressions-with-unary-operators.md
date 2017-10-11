---
title: "使用一元运算符的表达式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: adde5e6fdb20924b633de60eba07390edad57907
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="expressions-with-unary-operators"></a>使用一元运算符的表达式
一元运算符仅作用于表达式中的某个操作数。 一元运算符如下所示：  
  
-   [间接寻址运算符 （*）](../cpp/indirection-operator-star.md)  
  
-   [Address-of 运算符 (&)](../cpp/address-of-operator-amp.md)  
  
-   [一元加运算符 （+）](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [一元求反运算符 （-）](../cpp/unary-plus-and-negation-operators-plus-and.md)  
  
-   [逻辑求反运算符 （！）](../cpp/logical-negation-operator-exclpt.md)  
  
-   [二进制求补运算符 （~）](../cpp/one-s-complement-operator-tilde.md)  
  
-   [前缀递增运算符 （+ +）](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [前缀递减运算符 （-）](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)  
  
-   [强制转换运算符 （）](../cpp/cast-operator-parens.md)  
  
-   [sizeof 运算符](../cpp/sizeof-operator.md)  
  
-   [__uuidof 运算符](../cpp/uuidof-operator.md)  
  
-   [__alignof 运算符](../cpp/alignof-operator.md)  
  
-   [new 运算符](../cpp/new-operator-cpp.md)  
  
-   [delete 运算符](../cpp/delete-operator-cpp.md)  
  
 这些运算符具有从右向左的关联性。 一元表达式通常涉及后缀或主表达式前面的语法。  
  
 下面是一元表达式的可能的形式。  
  
-   *postfix-expression*  
  
-   `++`*一元表达式*  
  
-   `--`*一元表达式*  
  
-   *一元运算符**强制转换表达式*  
  
-   `sizeof`*一元表达式*  
  
-   `sizeof(`*类型名称*`)`  
  
-   `decltype(`*表达式*`)`  
  
-   *分配表达式*  
  
-   *释放表达式*  
  
 任何*后缀表达式*被视为*一元表达式*，而且因为任何主表达式被视为*后缀表达式*，任何主表达式是被视为*一元表达式*还。 有关详细信息，请参阅[后缀表达式](../cpp/postfix-expressions.md)和[主表达式](../cpp/primary-expressions.md)。  
  
 A*一元运算符*组成一个或多个以下符号：`* & + - ! ~`  
  
 *强制转换表达式*是可选的强制转换，以更改类型的一元表达式。 有关详细信息请参阅[强制转换运算符: （)](../cpp/cast-operator-parens.md)。  
  
 *表达式*可以是任何表达式。 有关详细信息，请参阅[表达式](../cpp/expressions-cpp.md)。  
  
 *分配表达式*指`new`运算符。 *释放表达式*指`delete`运算符。 有关详细信息，请参阅本主题前面的链接。  
  
## <a name="see-also"></a>另请参阅  
 [表达式类型](../cpp/types-of-expressions.md)
