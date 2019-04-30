---
title: 重载一元运算符
ms.date: 11/04/2016
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
ms.openlocfilehash: 802380bad59534e8402020142e394b3948032476
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377219"
---
# <a name="overloading-unary-operators"></a>重载一元运算符

可重载的一元运算符如下：

1. `!` ([逻辑非](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([address-of](../cpp/address-of-operator-amp.md))

1. `~` ([的二进制反码](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([指针取消引用](../cpp/indirection-operator-star.md))

1. `+` ([一元加](../cpp/additive-operators-plus-and.md))

1. `-` ([一元求反](../cpp/additive-operators-plus-and.md))

1. `++` ([增量](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([递减](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. 转换运算符

后缀递增和递减运算符 (`++`并`--`) 将被视为单独在[递增和递减](../cpp/increment-and-decrement-operator-overloading-cpp.md)。

单独的主题; 中还讨论了转换运算符请参阅[用户定义类型的转换](../cpp/user-defined-type-conversions-cpp.md)。

以下规则适用于所有其他一元运算符。 若要将一元运算符函数声明为非静态成员，则必须用以下形式声明它：

> *ret-type* **operator** *op* **()**

其中*ret 类型*是返回类型和*op*运算符之一上表中列出。

若要将一元运算符函数声明为全局函数，则必须用以下形式声明它：

> *ret-type* **operator** *op* **(** *arg* **)**

其中*ret 类型*并*op*如上所述用于成员运算符函数并*arg*是用于执行操作的类类型的自变量。

> [!NOTE]
>  一元运算符的返回类型没有限制。 例如，逻辑“非”(`!`) 返回整数值是合理的，但并非强制性的。

## <a name="see-also"></a>请参阅

[运算符重载](../cpp/operator-overloading.md)