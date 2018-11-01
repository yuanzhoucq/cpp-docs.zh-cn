---
title: 值的类别： Lvalues 和 Rvalues （Visual c + +）
ms.date: 04/06/2018
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 261453d5640c122f23491304b71e53e27c06eb7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546345"
---
# <a name="lvalues-and-rvalues-visual-c"></a>左值和右值 （Visual C++）

每个 C++ 表达式有一个类型，并且属于*值类别*。 值类别是在创建、 复制和移动在表达式计算期间的临时对象时，编译器必须遵循的规则的基础。

C++ 17 标准定义表达式值的分类，如下所示：

- 一个*glvalue*是的表达式的求值结果确定标识的对象、 位域或函数。
- 一个*prvalue*是的表达式的求值结果初始化对象或一个位字段，或在它所出现的上下文中的指定计算运算符的操作数的值。
- *Xvalue*是 glvalue 表示的对象或位域可以重复使用的资源，（通常是因为它即将达到其生命周期结束）。 [示例： 特定类型的表达式涉及右值引用 (8.3.2) 产生 xvalues，如对其返回类型是右值引用的函数的调用或强制转换为右值引用类型。 ]
- *左值*是不是 xvalue glvalue。
- *右值*prvalue 或 xvalue。

下图演示了两个分类之间的关系：

![C++ 表达式值的分类](media/value_categories.png "C++ 表达式值的分类")

左值具有您的程序可以访问的地址。 左值表达式的示例包括变量的名称，包括**const**变量，数组元素、 函数返回的左值引用、 位域、 联合和类成员的调用。

Prvalue 表达式具有可访问你的程序没有地址。 Prvalue 表达式的示例包括文本、 非引用类型返回的函数调用和仅由编译器创建表达式评估期间，但可访问的临时对象。

Xvalue 表达式具有一个地址，无法再访问你的程序，但可用于初始化右值引用，它提供与表达式的访问。 示例包括返回右值引用的数组下标、 成员和指针到成员表达式，数组或对象是右值引用的函数调用。

## <a name="example"></a>示例

以下示例演示左值和右值的多种正确的和错误的用法：

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    const int ci = 7;
    // Incorrect usage: the variable is a non-modifiable lvalue (C3892).
    ci = 9; // C3892

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;
}
```

> [!NOTE]
> 此主题中的示例阐释了未重载运算符时的正确和错误用法。 通过重载运算符，可以使表达式（如 `j * 4`）成为左值。

条款*左值*并*右值*通常用于在引用对象的引用时。 有关引用的详细信息，请参阅[左值引用声明符： &](../cpp/lvalue-reference-declarator-amp.md)并[右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>请参阅

[基本概念](../cpp/basic-concepts-cpp.md)<br/>
[Lvalue 引用声明符：&](../cpp/lvalue-reference-declarator-amp.md)<br/>
[规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)
