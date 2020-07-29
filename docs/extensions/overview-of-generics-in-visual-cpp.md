---
title: C++/CLI 中的泛型概述
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], about generics
- default initializers [C++]
- type parameters [C++]
- constructed types
- type arguments [C++]
- constructed types, open [C++]
- open constructed types [C++]
- constructed types, closed [C++]
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
ms.openlocfilehash: 875fc3334d326315890396ee02e55b5880e8692e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195559"
---
# <a name="overview-of-generics-in-ccli"></a>C++/CLI 中的泛型概述

泛型是公共语言运行时所支持的参数化类型。 参数化类型是用在使用泛型时指定的未知类型参数定义的类型。

## <a name="why-generics"></a>为什么使用泛型？

C++ 支持模板，模板和泛型均支持参数化类型创建类型化的集合类。 但是，模板提供编译时的参数化。 您不能引用包含模板定义的程序集和创建模板的新专用化。 编译之后，专用化模板看起来与其他任何类或方法类似。 相比之下，泛型在 MSIL 中作为参数化类型发出，是运行时已知的参数化类型；引用包含泛型类型的程序集的源代码可以创建泛型类型的专用化。 若要详细了解标准 C++ 模板和泛型的比较，请参阅[泛型与模板 (C++/CLI)](generics-and-templates-visual-cpp.md)。

## <a name="generic-functions-and-types"></a>泛型函数和类型

类类型只要是托管类型，则可以是泛型。 此示例可能是 `List` 类。 列表中的对象类型为类型参数。 如果需要对很多不同类型对象使用的 `List` 类，在使用泛型前，你可能已使用将 `System::Object` 用作项目类型的 `List`。 但这会使任何对象（包括错误类型的对象）用于列表。 这种列表称为非类型化集合类。 在最佳情况下，您可以在运行时检查类型并引发异常。 或者，可能使用了模板，但它在编译为程序集后将丢失其泛型特性。 程序集的使用者不能创建该模板的专用化。 使用泛型，可以创建类型化集合类，如 `List<int>`（读作“int 列表”）和 `List<double>`（读作“double 列表”）。如果尝试在类型化集合中放入集合未指定接受的类型，这便会生成编译时错误。 此外，这些类型在编译后仍然是泛型。

有关泛型类的语法说明，可参阅[泛型类 (C++/CLI)](generic-classes-cpp-cli.md)。 新命名空间 <xref:System.Collections.Generic> 引入了一组参数化集合类型，包括 <xref:System.Collections.Generic.Dictionary%602>、<xref:System.Collections.Generic.List%601> 和 <xref:System.Collections.Generic.LinkedList%601>。

实例和静态类成员函数、委托及全局函数也可能是泛型的。 如果函数参数是未知类型，或者函数自身必须与泛型类型一起使用，则需要泛型函数。 在许多情况下，`System::Object` 过去曾用作未知类型对象的参数，而现在可以改用泛型类型参数，从而提高代码的类型安全性。 尝试传入非函数设计目标的类型时将标记为编译时错误。 如果使用 `System::Object` 作为函数参数，无法检测到无意间传递的函数不旨在处理的对象，必须在函数主体中将未知对象类型强制转换为特定类型，并考虑到可能会抛出 InvalidCastException。 采用泛型时，代码尝试向函数传递对象时会导致类型冲突，因此要确保函数体的类型正确。

相同的优点适用于基于泛型的集合类。 集合类过去曾使用 `System::Object` 在集合中存储元素。 插入非集合目标类型的对象，不会在编译时进行标记，即使插入对象时也不进行标记。 通常，当在集合中访问对象时，对象将被强制转换为其他类型。 只有强制转换失败时，才会检测意外类型。 泛型在编译时检测插入不符合（或隐式转换为）泛型集合类型参数的类型的所有代码，从而解决了此问题。

有关语法说明，请参阅[泛型函数 (C++/CLI)](generic-functions-cpp-cli.md)。

## <a name="terminology-used-with-generics"></a>泛型相关术语

### <a name="type-parameters"></a>类型参数

泛型声明包含一个或多个未知类型（称为“类型参数”**）。 类型参数名称代表泛型声明主体中的类型。 类型参数用作泛型声明主体中的类型。 `List<T>` 的泛型声明中包含类型参数 T。

### <a name="type-arguments"></a>类型变量

如果泛型专用于特定一个或多个类型，类型实参** 是代替类型形参的实际类型。 例如， **`int`** 是中的类型参数 `List<int>` 。 值类型和句柄类型是泛型类型参数中允许使用的唯一类型。

### <a name="constructed-type"></a>构造类型

通过泛型类型构造而成的类型称为“构造类型”**。 未完全指定的类型（如 `List<T>`）是开放式构造类型**；完全指定的类型（如 `List<double>,`）是封闭式构造类型** 或专用化类型**。 开放式构造类型可以用于其他泛型类型或方法的定义，并且不能完全指定，直到指定封闭泛型本身。 例如，下面是将开放式构造类型用作泛型基类的示例：

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>约束

约束是对可以用作类型参数的类型的限制。 例如，给定泛型类可能仅接受继承自指定类或实现指定接口的类。 有关详细信息，请参阅[泛型类型参数的约束 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="reference-types-and-value-types"></a>引用类型和值类型

句柄类型和值类型可以用作类型参数。 在泛型定义中，两种类型都可使用，语法是引用类型的语法。 例如，`->` 运算符用于访问类型参数的类型的成员，无论最后使用的类型是引用类型还是值类型。 在值类型用作类型参数时，运行时生成直接使用值类型的代码，而无需将值类型装箱。

当将引用类型用作泛型类型参数时，请使用句柄语法。 当将值类型用作泛型类型参数时，请直接使用类型名称。

```cpp
// generics_overview_2.cpp
// compile with: /clr
generic <typename T>

ref class GenericType {};
ref class ReferenceType {};

value struct ValueType {};

int main() {
    GenericType<ReferenceType^> x;
    GenericType<ValueType> y;
}
```

## <a name="type-parameters"></a>类型参数

泛型类中的参数类型与其他标识符一样。 但是，因为类型未知，在使用时存在限制。 例如，不能使用类型参数类的成员和方法，除非已知类型参数支持这些成员。 也就是说，要通过类型参数访问成员，必须在类型参数的约束列表中添加包含成员的类型。

```cpp
// generics_overview_3.cpp
// compile with: /clr
interface class I {
   void f1();
   void f2();
};

ref struct R : public I {
   virtual void f1() {}
   virtual void f2() {}
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f1();
   t->f2();
   safe_cast<R^>(t)->f3();
}

int main() {
   f(gcnew R());
}
```

这些限制也适用于运算符。 如果类型不支持这些运算符，那么不受约束的泛型类型参数就不能使用 `==` 和 `!=` 运算符比较类型参数的两个实例。 这些检查是对泛型的必要检查，但不适用于模板，因为当来不及检查成员是否无效时，泛型可以在运行时使用满足约束的任何类专用化。

通过使用 `()` 运算符，可以创建类型参数的默认实例。 例如：

`T t = T();`

其中 `T` 是泛型类或方法定义中的类型参数，可将变量初始化为其默认值。 如果 `T` 是 ref 类，它将为 null 指针；如果 `T` 是值类，对象将初始化为零。 这称为“默认初始值设定项”**。

## <a name="see-also"></a>请参阅

[泛型](generics-cpp-component-extensions.md)
