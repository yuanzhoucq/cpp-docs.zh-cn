---
title: 强制转换
ms.date: 11/19/2018
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
ms.openlocfilehash: bb06db3af6aee031b6cb2d69b38a9404304420fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190117"
---
# <a name="casting"></a>强制转换

在 C++ 语言中，如果类从包含虚函数的基类派生，则指向基类类型的指针可用于调用派生类对象中包含的虚函数的实现。 包含虚函数的类有时被称为“多态类”。

由于派生类完全包含它派生自的所有基类的定义，因此在类层次结构上将指针转换至这些基类中的任何一个是安全的。 提供一个指向基类的指针，在层次结构中向下转换指针可能是安全的。 如果将指向的对象实际上是从基类派生的类型，则是安全的。 在这种情况下，实际对象称为“完整对象”。 指向基类的指针称为指向完整对象的“子对象”。 例如，考虑下图中显示的类层次结构。

![类层次结构](../cpp/media/vc38zz1.gif "类层次结构") <br/>
类层次结构

如下图所示，可对类型为 `C` 的对象进行可视化。

![类 C 与子&#45;对象 B 和 A](../cpp/media/vc38zz2.gif "类 C 与子&#45;对象 B 和 A") <br/>
具有子对象 B 和 A 的类 C

给定 `C` 类的一个实例，存在 `B` 子对象和 `A` 子对象。 包括 `C` 和 `A` 子对象的 `B` 实例是“完整对象。”

通过使用运行时类型信息，可以检查指针实际是否指向完整对象，并可以安全转换以指向其层次结构中的另一个对象。 [Dynamic_cast](../cpp/dynamic-cast-operator.md)运算符可用于进行这些类型的强制转换。 它还执行必要的运行时检查以确保操作安全。

对于非多态类型的转换，可以使用[static_cast](../cpp/static-cast-operator.md)运算符（本主题说明静态和动态强制转换转换之间的差异，以及何时适合使用每个转换）。

本部分涵盖了以下主题：

- [转换运算符](../cpp/casting-operators.md)

- [运行时类型信息](../cpp/run-time-type-information.md)

## <a name="see-also"></a>另请参阅

[表达式](../cpp/expressions-cpp.md)
