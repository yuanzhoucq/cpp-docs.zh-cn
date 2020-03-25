---
title: partial（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: ad8faa08a2c85e777cbc8721e5842e708b9e6cb1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181845"
---
# <a name="partial--ccli-and-ccx"></a>partial（C++/CLI 和 C++/CX）

使用 partial 关键字，可以在不同文件中单独编写同一个 ref class 的不同部分。

## <a name="all-runtimes"></a>所有运行时

（此语言功能仅适用于 Windows 运行时。）

## <a name="windows-runtime"></a>Windows 运行时

对于有两个分部定义的 ref class，partial 关键字应用于第一次出现的定义，而这通常是通过自动生成的代码来完成，所以人工程序员不经常使用此关键字。 对于此类的所有后续分部定义，请从 class-key 关键字和类标识符中省略 partial 修饰符。 如果编译器遇到先前定义的 ref class 和类标识符，但其中没有 partial 关键字，它就会在内部将 ref class 定义的所有部分都合并到一个定义中。

### <a name="syntax"></a>语法

```cpp
partial class-key identifier {
   /* The first part of the partial class definition.
      This is typically auto-generated */
}
// ...
class-key identifier {
   /* The subsequent part(s) of the class definition. The same
      identifier is specified, but the "partial" keyword is omitted. */
}
```

### <a name="parameters"></a>parameters

class-key<br/>
声明 Windows 运行时支持的类或结构的关键字。 可取值为 ref class、value class、ref struct 或 value struct。

*identifier*<br/>
已定义类型的名称。

### <a name="remarks"></a>备注

分部类支持由你在一个文件中修改类定义的一部分，并由自动代码生成软件（例如 XAML 设计器）在另一个文件中修改同一个类的代码。 通过使用分部类，可以防止自动代码生成器覆盖代码。 在 Visual Studio 项目中，partial 修饰符自动应用于生成的文件。

内容：如果省略**partial**关键字，则分部类定义可以包含完整类定义可包含的任何内容。 不过，无法指定类可访问性（例如 `public partial class X { ... };`）或 declspec。

identifier 的分部类定义中使用的访问说明符不会影响，identifier 的后续分部类定义或完整类定义中的默认可访问性。 允许使用静态数据成员的内联定义。

声明：类*标识符*的分部定义只引入 name*标识符*，但不能以需要类定义的方式使用*标识符*。 在编译器遇到 identifier 的完整定义之前，名称 identifier 无法用于确定 identifier 的大小，也无法用于使用 identifier 的基或成员。

数量和顺序：*标识符*可以有零个或多个分部类定义。 identifier 的每个分部类定义都必须在词法上排在 identifier 的一个完整定义前（如果有完整定义的话；否则，无法使用类，除非有前向声明），但不必排在 identifier 的前向声明前。 所有 class-key 都必须匹配。

完全定义：在类*标识符*的完整定义点处，行为与*标识符*的定义已按照在分部类中遇到和定义它们的顺序声明了所有基类、成员等的情况相同。

模板：分部类不能是模板。

泛型：如果完整定义可以是泛型，则分部类可以是泛型。 但每个分部类和完整类都必须有完全相同的泛型参数，包括形式参数名称。

若要详细了解如何使用 partial 关键字，请参阅[分部类 (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

（此语言功能不适用于公共语言运行时。）

## <a name="see-also"></a>另请参阅

[分部类 (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)
