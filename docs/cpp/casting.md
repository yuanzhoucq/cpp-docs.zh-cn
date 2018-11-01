---
title: 强制转换
ms.date: 11/04/2016
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
ms.openlocfilehash: eb309319a4af6d604d8558552ce313ba1d0fb629
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560792"
---
# <a name="casting"></a>强制转换

在 C++ 语言中，如果类从包含虚函数的基类派生，则指向基类类型的指针可用于调用派生类对象中包含的虚函数的实现。 包含虚函数的类有时被称为“多态类”。

由于派生类完全包含它派生自的所有基类的定义，因此在类层次结构上将指针转换至这些基类中的任何一个是安全的。 提供一个指向基类的指针，在层次结构中向下转换指针可能是安全的。 如果将指向的对象实际上是从基类派生的类型，则是安全的。 在这种情况下，实际对象称为“完整对象”。 指向基类的指针称为指向完整对象的“子对象”。 例如，考虑下图中显示的类层次结构。

![类层次结构](../cpp/media/vc38zz1.gif "vc38ZZ1")类层次结构

如下图所示，可对类型为 `C` 的对象进行可视化。

![C 类子&#45;对象 B 和 A](../cpp/media/vc38zz2.gif "vc38ZZ2") B 子对象和子对象的类 C

给定 `C` 类的一个实例，存在 `B` 子对象和 `A` 子对象。 包括 `C` 和 `A` 子对象的 `B` 实例是“完整对象。”

通过使用运行时类型信息，可以检查指针实际是否指向完整对象，并可以安全转换以指向其层次结构中的另一个对象。 [Dynamic_cast](../cpp/dynamic-cast-operator.md)运算符可用于使这些类型的转换。 它还执行必要的运行时检查以确保操作安全。

对于非多态类型的转换，可以使用[static_cast](../cpp/static-cast-operator.md)运算符 （本主题说明以及何时适合使用每个静态和动态强制转换之间的差异）。

此节涵盖以下主题：

- [强制转换运算符](../cpp/casting-operators.md)

- [运行时类型信息](../cpp/run-time-type-information.md)

## <a name="see-also"></a>请参阅

[表达式](../cpp/expressions-cpp.md)