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
ms.openlocfilehash: eb9b3907008147cb21f04aec5f42e4896fa35b3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516472"
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

### <a name="parameters"></a>参数

class-key<br/>
声明 Windows 运行时支持的类或结构的关键字。 可取值为 ref class、value class、ref struct 或 value struct。

*identifier*<br/>
已定义类型的名称。

### <a name="remarks"></a>备注

分部类支持由你在一个文件中修改类定义的一部分，并由自动代码生成软件（例如 XAML 设计器）在另一个文件中修改同一个类的代码。 通过使用分部类，可以防止自动代码生成器覆盖代码。 在 Visual Studio 项目中，partial 修饰符自动应用于生成的文件。

内容:有两个例外，如果省略了 partial 关键字，分部类定义可以包含完整类定义中的一切。 不过，无法指定类可访问性（例如 `public partial class X { ... };`）或 declspec。

identifier 的分部类定义中使用的访问说明符不会影响，identifier 的后续分部类定义或完整类定义中的默认可访问性。 允许使用静态数据成员的内联定义。

声明：类 identifier 的分部定义只引入名称 identifier，但在使用 identifier 时无法要求必须使用类定义。 在编译器遇到 identifier 的完整定义之前，名称 identifier 无法用于确定 identifier 的大小，也无法用于使用 identifier 的基或成员。

数字和排序：identifier 可以有零个或多个分部类定义。 identifier 的每个分部类定义都必须在词法上排在 identifier 的一个完整定义前（如果有完整定义的话；否则，无法使用类，除非有前向声明），但不必排在 identifier 的前向声明前。 所有 class-key 都必须匹配。

完整定义：关于类 identifier 的完整定义，行为就像是 identifier 的定义已按照分部类中定义基类、成员等的顺序，声明了所有这些基类、成员等。

模板：分部类不得是模板。

泛型：如果完整定义可以是泛型，那么分部类也可以是泛型。 但每个分部类和完整类都必须有完全相同的泛型参数，包括形式参数名称。

若要详细了解如何使用 partial 关键字，请参阅[分部类 (C++/CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

（此语言功能不适用于公共语言运行时。）

## <a name="see-also"></a>请参阅

[分部类 (C++/CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)