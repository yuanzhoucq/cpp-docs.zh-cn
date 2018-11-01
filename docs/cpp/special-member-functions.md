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
ms.openlocfilehash: 3b26628fd18749bd19819fe787888fd3264a79d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535754"
---
# <a name="special-member-functions"></a>特殊成员函数

*特殊成员函数*是类 （或结构），在某些情况下，编译器会自动为您生成的成员函数。 这些函数是[默认构造函数](constructors-cpp.md#default_constructors)，则[析构函数](destructors-cpp.md)，则[复制构造函数和复制赋值运算符](copy-constructors-and-copy-assignment-operators-cpp.md)，和[移动构造函数和移动赋值运算符](move-constructors-and-move-assignment-operators-cpp.md)。 如果您的类未定义一个或多个特殊成员函数，然后编译器可能会隐式声明和定义使用的函数。 编译器生成的实现调用*默认*特殊成员函数。 如果不需要它们，编译器不生成函数。

您可以通过使用显式声明默认特殊成员函数 **= default**关键字。 这将导致编译器定义的函数仅在需要时，相同的方式如同根本不声明函数。

在某些情况下，编译器可能会生成*删除*没有定义，且因此没有可调用的特殊成员函数。 这可以在其中为特定的特殊成员函数的类上调用没有任何意义，给定类的其他属性的情况下。 若要显式防止自动生成特殊成员函数，您可将其声明为已删除通过使用 **= 删除**关键字。

编译器将生成*默认构造函数*，仅当你未声明任何其他构造函数时不采用任何参数的构造函数。 如果声明采用参数的构造函数后，尝试调用默认构造函数的代码会导致编译器生成一条错误消息。 编译器生成的默认构造函数执行简单 member-wise[默认值初始化](initializers.md#default_initialization)的对象。 默认值初始化使处于不确定状态的所有成员变量。

默认析构函数执行 member-wise 析构的对象。 仅当基类析构函数是虚拟的它是虚拟的。

默认复制和移动构造和分配操作执行位模式 member-wise 复制或移动的非静态数据成员。 移动声明不析构函数或移动或复制操作时，才会生成操作。 当声明没有复制构造函数时，才会生成默认复制构造函数。 如果声明移动操作，它将隐式删除。 仅当显式声明没有复制赋值运算符时生成默认复制赋值运算符。 如果声明移动操作，它将隐式删除。

## <a name="see-also"></a>请参阅

[C++ 语言参考](cpp-language-reference.md)