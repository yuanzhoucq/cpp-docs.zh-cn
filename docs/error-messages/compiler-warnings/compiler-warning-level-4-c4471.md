---
title: 编译器警告（等级4） C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: b107b25714dd3333c3adcb8c83bf56775bf91823
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228747"
---
# <a name="compiler-warning-level-4-c4471"></a>编译器警告（等级4） C4471

"*enumeration*"：未区分范围的枚举的前向声明必须有基础类型（假定为 int）

找到未区分范围的枚举的前向声明，但未提供基础类型的说明符。 默认情况下，Visual C++ 假设 **`int`** 是枚举的基础类型。 如果在枚举定义中使用了不同的类型（例如，如果指定了不同的显式类型），或者如果初始值设定项隐式设置其他类型，则这可能会导致问题。 您还可能具有可移植性问题;其他编译器不假定 **`int`** 为枚举的基础类型。

默认情况下，此警告处于关闭状态。您可以使用/Wall 或/w*N*4471 在命令行上启用它，或在您的源文件中使用 #pragma[警告](../../preprocessor/warning.md)。

在某些情况下，此警告是虚假的。 如果在定义后出现枚举的前向声明，则会触发此警告。 例如，此代码是有效的，尽管它可能会导致 C4471：

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>示例

通常，使用未区分范围的枚举的完整定义，而不是前向声明。 你可以将定义放置在头文件中，并将其包含在引用它的源文件中。 这适用于为 c + + 98 和更高版本编写的代码。 建议此解决方案实现可移植性和易维护性。

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>示例

在 c + + 11 中，可以向未区分范围的枚举及其前向声明添加显式类型。 仅当复杂标头包含逻辑阻止使用定义而不是前向声明时，才建议使用此解决方案。 此解决方案可能导致维护问题：如果更改用于枚举定义的基础类型，则还必须更改要匹配的所有前向声明，否则代码中可能会出现缄默错误。 可以将前向声明放在标头文件中，以最大程度地减少此问题。

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

如果为枚举指定显式类型，则建议你同时启用[C4369](compiler-warning-level-1-C4369.md)警告（默认情况下启用）。 这会标识枚举项需要与显式指定的类型不同的类型的情况。

## <a name="example"></a>示例

可以将代码更改为使用范围枚举，这是 c + + 11 中新增的一项功能。 必须将定义和使用枚举类型的任何客户端代码更改为使用限定范围的枚举。 如果遇到命名空间污染问题，建议使用范围枚举，因为定义的枚举项的名称限制为枚举的范围。 范围枚举的另一个功能是，其成员不能隐式转换为另一种整型或枚举类型，这可能是微妙错误的根源。

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
