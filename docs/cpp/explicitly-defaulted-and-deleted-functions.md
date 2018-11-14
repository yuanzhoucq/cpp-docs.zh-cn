---
title: 显式默认设置的函数和已删除的函数
ms.date: 11/04/2016
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
ms.openlocfilehash: aa03ca826eebe467e45e2bb7e0bc47537d40f366
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327013"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>显式默认设置的函数和已删除的函数

在 C++11 中，默认函数和已删除函数使你可以显式控制是否自动生成特殊成员函数。 已删除的函数还可为您提供简单语言，以防止所有类型的函数（特殊成员函数和普通成员函数以及非成员函数）的参数中出现有问题的类型提升，这会导致意外的函数调用。

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>显式默认设置的函数和已删除函数的好处

在 C++ 中，如果某个类型未声明它本身，则编译器将自动为该类型生成默认构造函数、复制构造函数、复制赋值运算符和析构函数。 这些函数称为*特殊成员函数*，并且它们是什么发出简单用户定义的类型在 C++ 行为方式就类似结构往来 c。也就是说，你可以创建、 复制和销毁它们而无需任何额外编码工作。 C++11 会将移动语义引入语言中，并将移动构造函数和移动赋值运算符添加到编译器可自动生成的特殊成员函数的列表中。

这对于简单类型非常方便，但是复杂类型通常自己定义一个或多个特殊成员函数，这可以阻止自动生成其他特殊成员函数。 实践操作：

- 如果显式声明了任何构造函数，则不会自动生成默认构造函数。

- 如果显式声明了虚拟析构函数，则不会自动生成默认析构函数。

- 如果显式声明了移动构造函数或移动赋值运算符，则：

   - 不自动生成复制构造函数。

   - 不自动生成复制赋值运算符。

- 如果显式声明了复制构造函数、复制赋值运算符、移动构造函数、移动赋值运算符或析构函数，则：

   - 不自动生成移动构造函数。

   - 不自动生成移动赋值运算符。

> [!NOTE]
> 此外，C++11 标准指定将以下附加规则：
>
> - 如果显式声明了复制构造函数或析构函数，则弃用复制赋值运算符的自动生成。
> - 如果显式声明了复制赋值运算符或析构函数，则弃用复制构造函数的自动生成。
>
> 在这两种情况下，Visual Studio 将继续隐式自动生成所需的函数且不发出警告。

这些规则的结果也可能泄漏到对象层次结构中。 例如，如果出于任何原因基类不具有默认构造函数可从派生类调用 — 即，**公共**或**受保护的**不带参数的构造函数 — 然后类派生不能自动生成其自己的默认构造函数。

这些规则可能会使本应直接的内容、用户定义类型和常见 C++ 惯例的实现变得复杂 — 例如，通过以私有方式复制构造函数和复制赋值运算符，而不定义它们，使用户定义类型不可复制。

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

在 C++11 之前，此代码段是不可复制的类型的惯例形式。 但是，它具有几个问题：

- 复制构造函数必须以私有方式进行声明以隐藏它，但因为它进行了完全声明，所以会阻止自动生成默认构造函数。 如果你需要默认构造函数，则必须显式定义一个（即使它不执行任何操作）。

- 即使显式定义的默认构造函数不执行任何操作，编译器也会将它视为重要内容。 其效率低于自动生成的默认构造函数，并且会阻止 `noncopyable` 成为真正的 POD 类型。

- 尽管复制构造函数和复制赋值运算符在外部代码中是隐藏的，但成员函数和 `noncopyable` 的友元仍可以看见并调用它们。 如果它们进行了声明但是未定义，则调用它们会导致链接器错误。

- 虽然这是广为接受的惯例，但是除非你了解用于自动生成特殊成员函数的所有规则，否则意图不明确。

在 C++11 中，不可复制的习语可通过更直接的方法实现。

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

请注意如何解决与 C++11 之前的惯例有关的问题：

- 仍可通过声明复制构造函数来阻止生成默认构造函数，但可通过将其显式设置为默认值进行恢复。

- 显式设置的默认特殊成员函数仍被视为不重要的，因此性能不会下降，并且不会阻止 `noncopyable` 成为真正的 POD 类型。

- 复制构造函数和复制赋值运算符是公共的，但是已删除。 定义或调用已删除函数是编译时错误。

- 对于了解 `=default` 和 `=delete` 的人来说，意图是非常清楚的。 你不必了解用于自动生成特殊成员函数的规则。

对于创建不可移动、只能动态分配或无法动态分配的用户定义类型，存在类似惯例。 所有这些惯例都具有 C++11 之前的实现，这些实现会遭受类似问题，并且可在 C++11 中通过按照默认和已删除特殊成员函数实现它们，以类似方式进行解决。

## <a name="explicitly-defaulted-functions"></a>显式默认设置的函数

可以默认设置任何特殊成员函数 — 以显式声明特殊成员函数使用默认实现、定义具有非公共访问限定符的特殊成员函数或恢复其他情况下被阻止其自动生成的特殊成员函数。

可通过如此示例所示进行声明来默认设置特殊成员函数：

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

请注意，只要特殊成员函数可内联，便可以在类主体外部默认设置它。

由于普通特殊成员函数的性能优势，因此我们建议你在需要默认行为时首选自动生成的特殊成员函数而不是空函数体。 你可以通过显式默认设置特殊成员函数，或通过不声明它（也不声明其他会阻止它自动生成的特殊成员函数），来实现此目的。

## <a name="deleted-functions"></a>已删除的函数

可以删除特殊成员函数以及普通成员函数和非成员函数，以阻止定义或调用它们。 通过删除特殊成员函数，可以更简洁地阻止编译器生成不需要的特殊成员函数。 必须在声明函数时将其删除；不能在这之后通过声明一个函数然后不再使用的方式来将其删除。

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

删除普通成员函数或非成员函数可阻止有问题的类型提升导致调用意外函数。 这可发挥作用的原因是，已删除的函数仍参与重载决策，并提供比提升类型之后可能调用的函数更好的匹配。 函数调用将解析为更具体的但可删除的函数，并会导致编译器错误。

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

请注意，在上述示例中，调用`call_with_true_double_only`通过使用**float**参数会导致编译器错误，但调用`call_with_true_double_only`通过**int**参数不会; 在**int**的情况下，该参数将从提升**int**到**double**并成功调用**double**版本的函数即使这不可能的用途是什么。 若要确保使用非双精度自变量对此函数进行的任何调用均会导致编译器错误，你可以声明已删除的函数的模板版本。

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```