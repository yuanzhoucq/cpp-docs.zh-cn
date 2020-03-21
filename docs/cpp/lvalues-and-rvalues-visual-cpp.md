---
title: 值类别：左值和右（C++）
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 23625ddf44d16a4dc408b87f27b9cdfba7a9cbd4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077238"
---
# <a name="lvalues-and-rvalues-c"></a>Lvalues 和 Rvalues (C++)

每C++个表达式都具有类型，属于*值类别*。 值类别是编译器在表达式计算过程中创建、复制和移动临时对象时必须遵循的规则的基础。

C++ 17 标准定义表达式值的分类，如下所示：

- *Glvalue*是一个表达式，其计算确定对象、位域或函数的标识。
- *Prvalue*是一个表达式，其计算初始化对象或位域，或计算运算符的操作数的值，由其出现的上下文指定。
- *Xvalue*是一个 glvalue，它表示可重复使用其资源的对象或位域（通常是因为它接近生存期的末尾）。 示例：涉及 rvalue 引用（8.3.2）的某些类型的表达式生成 xvalues，如对其返回类型为右值引用或强制转换为右值引用类型的函数的调用。
- *左*值是不是 xvalue 的 glvalue。
- *右*值为 prvalue 或 xvalue。

下图说明了类别之间的关系：

![C++表达式值类别](media/value_categories.png "C++表达式值类别")

左值具有程序可以访问的地址。 左值表达式的示例包括变量名称，包括**常量**变量、数组元素、返回 lvalue 引用、位字段、联合和类成员的函数调用。

Prvalue 表达式没有可通过程序访问的地址。 Prvalue 表达式的示例包括：文本、返回非引用类型的函数调用，以及在表达式评估期间创建但仅由编译器访问的临时对象。

Xvalue 表达式的地址不能再由您的程序访问，但可用于初始化 rvalue 引用，后者提供对表达式的访问。 示例包括返回右值引用的函数调用，以及数组下标、成员和指针到数组或对象为右值引用的成员表达式。

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

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;

    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> 此主题中的示例阐释了未重载运算符时的正确和错误用法。 通过重载运算符，可以使表达式（如 `j * 4`）成为左值。

当引用对象引用时，通常使用字词*lvalue*和*右*值。 有关引用的详细信息，请参阅[Lvalue 引用声明符： &](../cpp/lvalue-reference-declarator-amp.md)和[右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另请参阅

[基本概念](../cpp/basic-concepts-cpp.md)<br/>
[Lvalue 引用声明符：&](../cpp/lvalue-reference-declarator-amp.md)<br/>
[规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)
