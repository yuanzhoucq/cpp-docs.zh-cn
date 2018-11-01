---
title: 编译器警告 （等级 C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: 0345b730b8fc37329f632bb5d8486c67efd8e3b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462213"
---
# <a name="compiler-warning-level-4-c4471"></a>编译器警告 （等级 C4471

'*枚举*： 无范围枚举的前向声明必须有基础类型 (假定为 int)

无范围枚举的前向声明的基础类型找到不带说明符。 默认情况下，Visual c + + 假定`int`是枚举的基础类型。 如果使用不同类型在枚举定义中，例如，如果指定了不同的显式类型，或其他类型隐式设置初始值设定项，这可能会导致问题。 您可能还必须可移植性问题;其他编译器不要假定`int`是枚举的基础类型。

默认情况下; 此警告处于关闭状态可以使用 /Wall 或 /w*N*4471 启用命令行上或使用 #pragma[警告](../../preprocessor/warning.md)在源文件中。

在某些情况下，此警告是虚假的。 如果枚举的前向声明出现在定义之后，可能会激发此警告。 例如，此代码是有效的即使它可能会导致 C4471 也是如此：

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>示例

一般情况下，它是安全的完整定义用于未区分范围枚举而不是前向声明。 可以将定义放入标头文件，并将其包含在引用它的源文件中。 这可以编写 C + + 98 及更高版本的代码。 我们建议针对可移植性和易维护性的此解决方案。

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>示例

在 C + + 11，您可以给未区分范围枚举，其前向声明添加显式类型。 仅当复杂标头包含的逻辑可以防止使用而不是前向声明定义的我们建议此解决方案。 此解决方案可能会导致维护问题： 如果更改用于枚举定义的基础类型，则还必须更改所有前向声明都匹配，或必须在代码中无提示的错误。 可以将前向声明放入标头文件，以尽量减少此问题。

```cpp
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```

```cpp
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```

如果指定显式类型枚举，我们建议你还可以启用警告[C4369](compiler-warning-level-1-C4369.md)，默认情况下处于打开。 此列标识用例的枚举项要求显式指定类型属于不同类型的位置。

## <a name="example"></a>示例

可以更改代码以使用范围的枚举中，C + + 11 中的新增功能的功能。 定义和使用枚举类型的任何客户端代码必须更改为使用范围的枚举。 我们建议用作范围的枚举中如果有命名空间污染的问题仅限于枚举的作用域定义的枚举项的名称。 作用域内枚举的另一个功能是其成员不能隐式转换为另一个整数或枚举类型，这可以是细微错误的源。

```cpp
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```

```cpp
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```

