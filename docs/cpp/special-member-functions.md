---
title: 特殊成员函数
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: b15a0e50774bbc4e70912a31f9a57ea0439f2c12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178686"
---
# <a name="special-member-functions"></a>特殊成员函数

*特殊成员函数*是类（或结构）成员函数，在某些情况下，编译器会自动为你生成。 这些函数是[默认构造函数](constructors-cpp.md#default_constructors)、[析构函数](destructors-cpp.md)、[复制构造函数和复制赋值运算符](copy-constructors-and-copy-assignment-operators-cpp.md)，以及[移动构造函数和移动赋值运算符](move-constructors-and-move-assignment-operators-cpp.md)。 如果类未定义一个或多个特殊成员函数，则编译器可能会隐式声明和定义使用的函数。 编译器生成的实现称为*默认*特殊成员函数。 编译器不会生成不需要的函数。

您可以通过使用 **= default**关键字来显式声明默认的特殊成员函数。 这会导致编译器仅在需要时定义函数，其方式与根本不声明函数的方式相同。

在某些情况下，编译器可能会生成*已删除*的特殊成员函数，这些函数未定义，因此无法调用。 在给定类的其他属性的情况下，对类调用特定特殊成员函数时，可能会发生这种情况。 若要显式阻止自动生成特殊成员函数，可以使用 **= delete**关键字将其声明为已删除。

编译器将生成一个*默认构造函数*，这是一个不采用任何参数的构造函数，仅在未声明任何其他构造函数时使用。 如果仅声明了采用参数的构造函数，则尝试调用默认构造函数的代码会导致编译器生成错误消息。 编译器生成的默认构造函数执行对象的简单成员[默认初始化](initializers.md#default_initialization)。 默认初始化会使所有成员变量处于不确定状态。

默认析构函数执行对象的成员析构。 仅当基类析构函数是虚拟时，它才是虚拟的。

默认复制和移动构造和分配操作执行非静态数据成员的成员的位模式复制或移动。 仅当未声明析构函数或移动或复制操作时，才会生成移动操作。 仅当未声明复制构造函数时，才会生成默认的复制构造函数。 如果已声明移动操作，则会被隐式删除。 仅当没有显式声明复制赋值运算符时才会生成默认的复制赋值运算符。 如果已声明移动操作，则会被隐式删除。

## <a name="see-also"></a>另请参阅

[C++ 语言参考](cpp-language-reference.md)
