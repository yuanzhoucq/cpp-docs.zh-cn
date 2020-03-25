---
title: C++ 常量表达式
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: d4d9803c7f80caba3c33d011e4df433491b9b591
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170574"
---
# <a name="c-constant-expressions"></a>C++ 常量表达式

*常*数值是指不会更改的值。 C + + 提供了两个关键字，它们使你能够表达不打算修改对象的意图，还可让你实现该意图。

C++ 需要常量表达式（计算结果为常量的表达式）以便声明：

- 数组边界

- case 语句中的选择器

- 位域长度规范

- 枚举初始值设定项

常量表达式中合法的唯一操作数是：

- 文字

- 枚举常量

- 声明为使用常量表达式初始化的常量的值

- **sizeof**表达式

必须将非整型常量（显式或隐式）转换为常量表达式中合法的整型。 因此，以下代码是合法的：

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

到整型的显式转换在常量表达式中是合法的;除用作**sizeof**运算符的操作数时，所有其他类型和派生类型都是非法的。

逗号运算符和赋值运算符不能用于常量表达式。

## <a name="see-also"></a>另请参阅

[表达式类型](../cpp/types-of-expressions.md)
