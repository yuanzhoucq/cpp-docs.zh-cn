---
title: 分部类 (C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2bd6db2c86fd75a62214d0ee32644521241d2e9
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109040"
---
# <a name="partial-classes-ccx"></a>分部类 (C++/CX)

分部类是支持你修改一部分类定义的方案的构造，而自动代码生成软件（例如 XAML 设计器）也在修改同一个类中的代码。 通过使用分部类，可以防止设计器重写代码。 在 Visual Studio 项目中， `partial` 修饰符自动应用于生成的文件。

## <a name="syntax"></a>语法

若要定义分部类，请紧接在类键（不然就是一个普通类定义的类键）之前使用 `partial` 关键字。 关键字（如 `partial ref class` ）是包含空白字符的上下文关键字。 下列构造支持分部定义。

- `class` 或 `struct`

- `ref class` 或 `ref struct`

- `value class` 或 `value struct`

- `enum` 或 `enum class`

- `ref interface`、 `interface class`、 `interface struct`或 `__interface`

- `union`

此示例演示分部 `ref class`：

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>内容

如果省略了 `partial` 关键字，则分部类定义可以包含完整类定义可包含的一切。 有一个例外，其中包括所有有效构造，如基类、数据成员、成员函数、枚举、友元声明和特性。 并且允许静态数据成员的内联定义。

一个例外是类可访问性。 例如，语句 `public partial class MyInvalidClass {/* ... */};` 是一个错误。 MyInvalidClass 的分部类定义中使用的任何访问说明符不会影响 MyInvalidClass 后续的分部或完整类定义中的默认可访问性。

下面的代码片段演示了可访问性。 在第一个分部类中， `Method1` 是公共的，因为它的可访问性是公共的。 在第二个分部类中， `Method2` 是私有的，因为默认类可访问性是私有的。

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>声明

类的分部定义（例如 *MyClass* ）只是 MyClass 的声明。 即，它只引入名称 *MyClass*。 *MyClass* 不能以需要类定义的方式使用，例如，知道 *MyClass* 的大小或使用 *MyClass*的基或成员。 仅当编译器遇到*MyClass* 的非分部定义时， *MyClass*才被视为已定义。

下面的示例演示分部类的声明行为。 在声明 #1 后， *MyClass* 可按照其被编写为前向声明 `ref class MyClass;`时的方式使用。 声明 #2 等效于声明 #1。声明 #3 是有效的，因为它是类的前向声明。 但是声明 #4 无效，因为

*MyClass* 未完全定义。

声明 #5 不使用 `partial` 关键字，并且完全定义了 *MyClass*。 因此，声明 #6 是有效的。

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>编号和排序

类的每个完整定义可以有零个或多个分部类定义。

类的每个分部类定义在词法上都必须排在该类的一个完整定义前，但是不必排在类的前向声明前。 如果类没有完整定义，则分部类声明只能是前向声明。

所有类键（如 `class` 和 `struct` ）都必须匹配。 例如，编码 `partial class X {}; struct X {};`。

下面的示例演示编号和排序。 最后一个分部声明失败，因为该类已经定义。

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>完整定义。

在类 X 的完整定义点，行为是相同的，就好像 X 的定义已按照在分部类中遇到和定义基类、成员等的顺序，声明了所有这些基类、成员等一样。 即，处理分部类的内容就好像它们是在类的完整定义点处编写的，名称查找和其他语言规则在类的完整定义点处应用，就好像分部类的内容是就地编写的

下面两个代码示例具有相同的含义和效果。 第一个示例使用分部类，第二个示例则未使用。

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>模板

分部类不能是模板。

## <a name="restrictions"></a>限制

分部类不能超越一个翻译单元范围。

`partial` 关键字只能与 `ref class` 关键字或 `value class` 关键字组合使用。

### <a name="examples"></a>示例

下面的示例跨两个代码文件定义 `Address` 类。 设计器修改 `Address.details.h` ，你修改 `Address.h`。 只有第一个文件中的类定义使用 `partial` 关键字。

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>请参阅

[类型系统](../cppcx/type-system-c-cx.md)<br/>
[Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)