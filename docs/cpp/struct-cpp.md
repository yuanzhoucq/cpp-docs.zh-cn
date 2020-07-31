---
title: struct (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: 5f247a99d3f04a15ebd54718a46dae8512a580d6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231112"
---
# <a name="struct-c"></a>struct (C++)

**`struct`** 关键字定义结构类型和/或结构类型的变量。

## <a name="syntax"></a>语法

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>参数

*template-规范*<br/>
可选模板规范。 有关详细信息，请参阅[模板规范](templates-cpp.md)。

*struct*<br/>
**`struct`** 关键字。

*decl-规范*<br/>
可选存储类规范。 有关详细信息，请参阅[__declspec](../cpp/declspec.md)关键字。

*标记*<br/>
为结构提供的类型名称。 标记将变成结构范围内的保留字。 标记是可选项。 如果省略，则定义匿名结构。 有关详细信息，请参阅[匿名类类型](../cpp/anonymous-class-types.md)。

base-list**<br/>
此结构将从中派生其成员的类或结构的可选列表。 有关详细信息，请参阅[基类](../cpp/base-classes.md)。 每个基类或结构名称的前面都可以是访问说明符（[public](../cpp/public-cpp.md)、 [private](../cpp/private-cpp.md)、 [protected](../cpp/protected-cpp.md)）和[virtual](../cpp/virtual-cpp.md)关键字。 有关详细信息，请参阅[控制对类成员的访问](member-access-control-cpp.md)中的成员访问表。

*成员列表*<br/>
结构成员列表。 有关详细信息，请参阅[类成员概述](../cpp/class-member-overview.md)。 此处的唯一区别在于， **`struct`** 用于代替 **`class`** 。

*声明符*<br/>
指定结构名称的声明符列表。 声明符列表声明了一个或多个结构类型实例。 如果结构的所有数据成员都为，则声明符可以包含初始值设定项列表 **`public`** 。 初始值设定项列表在结构中很常见，因为 **`public`** 默认情况下数据成员为。  有关详细信息，请参阅[声明符的概述](../cpp/overview-of-declarators.md)。

## <a name="remarks"></a>备注

结构类型是用户定义的复合类型。 它由可具有不同类型的字段或成员构成。

在 c + + 中，结构与类相同，不同之处在于其成员 **`public`** 默认为。

有关 c + +/CLI 中的托管类和结构的信息，请参阅[类和结构](../extensions/classes-and-structs-cpp-component-extensions.md)。

## <a name="using-a-structure"></a>使用结构

在 C 中，必须显式使用 **`struct`** 关键字来声明结构。 在 c + + 中，不需要在 **`struct`** 定义类型后使用关键字。

可以选择在定义结构类型时，通过在右大括号和分号之间放置一个或多个逗号分隔的变量名称来声明变量。

可以初始化结构变量。 每个变量的初始化必须括在大括号中。

有关相关信息，请参阅[类](../cpp/class-cpp.md)、[联合](../cpp/unions.md)和[枚举](../cpp/enumerations-cpp.md)。

## <a name="example"></a>示例

```cpp
#include <iostream>
using namespace std;

struct PERSON {   // Declare PERSON struct type
    int age;   // Declare member types
    long ss;
    float weight;
    char name[25];
} family_member;   // Define object of type PERSON

struct CELL {   // Declare CELL bit field
    unsigned short character  : 8;  // 00000000 ????????
    unsigned short foreground : 3;  // 00000??? 00000000
    unsigned short intensity  : 1;  // 0000?000 00000000
    unsigned short background : 3;  // 0???0000 00000000
    unsigned short blink      : 1;  // ?0000000 00000000
} screen[25][80];       // Array of bit fields

int main() {
    struct PERSON sister;   // C style structure declaration
    PERSON brother;   // C++ style structure declaration
    sister.age = 13;   // assign values to members
    brother.age = 7;
    cout << "sister.age = " << sister.age << '\n';
    cout << "brother.age = " << brother.age << '\n';

    CELL my_cell;
    my_cell.character = 1;
    cout << "my_cell.character = " << my_cell.character;
}
// Output:
// sister.age = 13
// brother.age = 7
// my_cell.character = 1
```
