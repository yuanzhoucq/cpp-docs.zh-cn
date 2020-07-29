---
title: 使用一元运算符的表达式
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: 032ebd99041de9308d16710b2a27e0db3cddd4df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233751"
---
# <a name="expressions-with-unary-operators"></a>使用一元运算符的表达式

一元运算符仅作用于表达式中的某个操作数。 一元运算符如下所示：

- [间接寻址运算符（*）](../cpp/indirection-operator-star.md)

- [Address 运算符（&）](../cpp/address-of-operator-amp.md)

- [一元加号运算符（+）](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [一元求反运算符（-）](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [逻辑求反运算符（！）](../cpp/logical-negation-operator-exclpt.md)

- [1的补数运算符（~）](../cpp/one-s-complement-operator-tilde.md)

- [前缀递增运算符 (++)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [前缀减量运算符（--）](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Cast 运算符（）](../cpp/cast-operator-parens.md)

- [`sizeof`操作员](../cpp/sizeof-operator.md)

- [`__uuidof`操作员](../cpp/uuidof-operator.md)

- [`alignof`操作员](../cpp/alignof-operator.md)

- [`new`操作员](../cpp/new-operator-cpp.md)

- [`delete`操作员](../cpp/delete-operator-cpp.md)

这些运算符具有从右向左的关联性。 一元表达式通常涉及后缀或主表达式前面的语法。

下面是一元表达式的可能的形式。

- *后缀表达式*

- `++` *unary-expression*

- `--` *unary-expression*

- *一元运算符**转换表达式*

- **`sizeof`***一元表达式*

- `sizeof(`*类型名称*`)`

- `decltype(`*表达式*`)`

- *分配表达式*

- *释放表达式*

任何*后缀表达式*都被视为*一元表达式*，因为任何主表达式都被视为*后缀表达式*，所以任何主表达式也被视为*一元表达式*。 有关详细信息，请参阅[后缀表达式](../cpp/postfix-expressions.md)和[主表达式](../cpp/primary-expressions.md)。

*一元运算符*包含以下一个或多个符号：`* & + - ! ~`

*强制转换表达式*是带有可选强制转换以更改类型的一元表达式。 有关详细信息，请参阅[Cast 运算符：（）](../cpp/cast-operator-parens.md)。

*表达式*可以是任何表达式。 有关详细信息，请参阅[表达式](../cpp/expressions-cpp.md)。

*分配表达式*引用 **`new`** 运算符。 *释放表达式*引用 **`delete`** 运算符。 有关详细信息，请参阅本主题前面的链接。

## <a name="see-also"></a>另请参阅

[表达式的类型](../cpp/types-of-expressions.md)
