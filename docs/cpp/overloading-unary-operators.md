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
ms.openlocfilehash: 971ef08c5e79f851c502ea872c541517065797c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372033"
---
# <a name="overloading-unary-operators"></a>重载一元运算符

可重载的一元运算符如下：

1. `!`（[逻辑不](../cpp/logical-negation-operator-exclpt.md)）

1. `&`（[地址](../cpp/address-of-operator-amp.md)）

1. `~`（[一个人的补品](../cpp/one-s-complement-operator-tilde.md)）

1. `*`（[指针取消引用](../cpp/indirection-operator-star.md)）

1. `+`（[一元加](../cpp/additive-operators-plus-and.md)）

1. `-`（[一元否定](../cpp/additive-operators-plus-and.md)）

1. `++`（[增量](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)）

1. `--`（[减分](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)）

1. 转换运算符

后缀增量和递减运算符 （`++`和`--`） 以[增量和递减](../cpp/increment-and-decrement-operator-overloading-cpp.md)分别处理。

转换运算符也在单独的主题中讨论;请参阅[用户定义的类型转换](../cpp/user-defined-type-conversions-cpp.md)。

以下规则适用于所有其他一元运算符。 若要将一元运算符函数声明为非静态成员，则必须用以下形式声明它：

> *ret 型***运算符***操作* **（）**

其中*ret 类型*是返回类型，*操作*是上表中列出的运算符之一。

若要将一元运算符函数声明为全局函数，则必须用以下形式声明它：

> *ret 型***运算符** *op* **（** *arg* **）**

其中*ret 类型*和*op*与成员运算符函数的描述相同 *，arg*是要操作的类类型的参数。

> [!NOTE]
> 一元运算符的返回类型没有限制。 例如，逻辑“非”(`!`) 返回整数值是合理的，但并非强制性的。

## <a name="see-also"></a>另请参阅

[操作员重载](../cpp/operator-overloading.md)
