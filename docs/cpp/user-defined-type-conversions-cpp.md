---
title: 用户定义的类型转换 (C++)
ms.date: 11/04/2016
f1_keywords:
- explicit_cpp
helpviewer_keywords:
- constructors [C++], and constants
- conversion functions [C++]
- explicit keyword [C++]
- type conversion
- constructors [C++], drawbacks
- conversion constructors
- type conversion [C++], explicit conversion
- coercion [C++]
- conversions [C++], explicit
- objects [C++], converting
- conversion functions [C++], rules for declaring
- declaring functions [C++], conversion functions
- functions [C++], conversion
- converting objects
- constructors [C++], conversion
- conversions [C++], by constructors
- data type conversion [C++], explicit
ms.assetid: d40e4310-a190-4e95-a34c-22c5c20aa0b9
ms.openlocfilehash: e74d5b3a748a9aab22a6a9d83c4d6c4bd3379df4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374682"
---
# <a name="user-defined-type-conversions-c"></a>用户定义的类型转换 (C++)

*转换*从不同类型的值生成某种类型的新值。 *标准转换*内置于C++语言中，并支持其内置类型，您可以创建*用户定义的转换*以执行用户定义类型、用户定义类型转换或之间的转换。

标准转换执行内置类型之间的转换、通过继承相关联的类型的指针或引用之间的转换、与 void 指针的双向转换以及到 null 指针的转换。 有关详细信息，请参阅[标准转换](../cpp/standard-conversions.md)。 用户定义的转换执行用户定义的类型之间的转换，或者执行用户定义的类型和内置类型之间的转换。 您可以将它们实现为[转换构造函数](#ConvCTOR)或[转换函数](#ConvFunc)。

转换可以是显式（当程序员通过调用从一个类型转换为另一个类型时，例如强制转换或直接初始化的情况），也可以是隐式（当语言或程序调用其他类型而非程序员给定的类型时）。

在以下情况下尝试隐式转换：

- 提供给函数的自变量与匹配参数的类型不同。

- 从函数返回的值与函数返回类型的类型不同。

- 初始值表达式与其初始化的对象的类型不同。

- 用于控制条件语句、循环构造或切换的表达式不具有对其进行控制时所需的结果类型。

- 提供给运算符的操作数与匹配的操作数参数的类型不同。 对于内置运算符，这两个操作数的类型必须相同，并且要转换为可表示它们的常规类型。 有关详细信息，请参阅[标准转换](standard-conversions.md)。 对于用户定义的运算符，每个操作数都必须与匹配的操作数参数的类型相同。

当一个标准转换无法完成隐式转换时，编译器可以使用用户定义的转换（可选择随后使用其他标准转换）来完成此操作。

当转换站点提供两个或多个用户定义的用于执行相同转换的转换时，该转换将被视为不明确。 这种不明确性是一个错误，因为编译器无法确定应选择哪一个可用转换。 但若只是定义执行相同转换的多种方式，则它不是一个错误，因为可用的转换集在源代码中的不同位置可能不同，例如，可取决于源文件中所包含的头文件。 只要转换站点只提供一个转换，就不会出现不明确性。 多种方式都会导致出现不明确转换，但最常见的方式如下：

- 多重继承。 该转换在多个基类中定义。

- 不明确的函数调用。 该转换定义为目标类型的转换构造函数以及源类型的转换函数。 有关详细信息，请参阅[转换函数](#ConvFunc)。

通常只需通过更全面地限定涉及类型的名称或执行显式强制转换来阐明你的意图，即可解决不明确性。

转换构造函数和转换函数都遵循成员访问控制规则，但仅当可以确定明确的转换时才考虑这些转换的可访问性。 这意味着，即使竞争的转换的访问级别会阻止使用该转换，该转换也可能具有不明确性。 有关成员可访问性的详细信息，请参阅[成员访问控制](../cpp/member-access-control-cpp.md)。

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>explicit 关键字和有关隐式转换的问题

默认情况下，当你创建用户定义的转换时，编译器可使用它来执行隐式转换。 有时这是你需要进行的操作，但另一些时候用于指导编译器进行隐式转换的简单规则会使其接受你不希望接受的代码。

一个众所周知的隐式转换，可能会导致问题的例子是转换为**bool。** 您可能想要创建可在布尔上下文中使用的类类型（例如，以便它可用于控制**if**语句或循环）的原因很多，但当编译器执行用户定义的转换到内置类型时，编译器被允许在之后应用其他标准转换。 此附加标准转换的目的是允许从**短**到**int**的升级，但它也为不太明显的转换（例如，从**bool**到**int**）打开了大门，它允许在您从未打算的整数上下文中使用类类型。 这个特殊问题被称为*安全布尔问题*。 此类问题是**显式**关键字可以提供帮助的地方。

**显式**关键字告诉编译器指定的转换不能用于执行隐式转换。 如果在引入**显式**关键字之前希望隐式转换的语法便利性，您必须接受隐式转换有时创建的意外后果，或者使用不太方便的命名转换函数作为解决方法。 现在，通过使用**显式**关键字，您可以创建方便的转换，这些转换只能用于执行显式强制转换或直接初始化，并且不会导致安全布尔问题所举例说明的问题。

显式**关键字**可以应用于自C++98起以来的转换构造函数，以及自C++11以来的转换函数。 以下各节包含有关如何使用**显式**关键字的详细信息。

## <a name="conversion-constructors"></a><a name="ConvCTOR"></a>转换构造函数

转换构造函数定义了从用户定义的类型或内置类型到用户定义的类型的转换。 下面的示例演示了转换构造函数，该构造函数从内置类型**double**转换为用户定义的类型`Money`。

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };

    display_balance(payable);
    display_balance(49.95);
    display_balance(9.99f);

    return 0;
}
```

请注意，对函数 `display_balance` 的首次调用（它将采用类型 `Money` 的自变量）不需要转换，因为它的自变量类型正确。 但是，在第二个调用`display_balance`时，需要转换，因为参数的类型（值`49.95`**为 的 double）** 不是函数所期望的。 函数不能直接使用此值，但由于参数的类型（**双**精度）转换为匹配参数的类型—`Money`- 从参数构造了临时类型的`Money`值，并用于完成函数调用。 在第三个调用`display_balance`中，请注意参数不是**双精度****值，** 而是值`9.99`为 -但函数调用仍然可以完成，因为编译器可以执行标准转换 — 在这种情况下，从**浮点**转换到**双**精度值 ，然后执行用户定义的转换从**双**精度转换为`Money`完成必要的转换。

### <a name="declaring-conversion-constructors"></a>声明转换构造函数

以下规则适用于声明转换构造函数：

- 转换的目标类型是要构造的用户定义的类型。

- 转换构造函数通常仅采用一个参数，它为源类型。 但是，当每个附加参数都具有默认值时，转换构造函数可指定这些附加参数。 源类型保留了第一个参数的类型。

- 与所有构造函数一样，转换构造函数不指定返回类型。 在声明中指定返回类型是一个错误。

- 转换构造函数可以为显式。

### <a name="explicit-conversion-constructors"></a>显式转换构造函数

通过声明转换构造函数为**显式**，它只能用于执行对象的直接初始化或执行显式强制转换。 这将阻止接受类类型的自变量的函数同样隐式接受转换构造函数的源类型的自变量，并且将阻止从该源类型的值复制初始化类的类型。 以下示例演示了如何定义显式转换构造函数，以及它对哪个代码格式正确所产生的影响。

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    explicit Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };        // Legal: direct initialization is explicit.

    display_balance(payable);      // Legal: no conversion required
    display_balance(49.95);        // Error: no suitable conversion exists to convert from double to Money.
    display_balance((Money)9.99f); // Legal: explicit cast to Money

    return 0;
}
```

在此示例中，请注意，你可以继续使用显示转换构造函数来执行 `payable` 的直接初始化。 如果你要改为复制初始化 `Money payable = 79.99;`，这将是一个错误操作。 对 `display_balance` 的首次调用不受影响，因为自变量的类型正确。 对 `display_balance` 的第二次调用是一个错误，因为转换构造函数无法用于执行隐式转换。 由于对`display_balance`的第三个调用是合法的，因为显式`Money`强制转换为 ，但请注意编译器仍然通过从**float**插入到**double**的隐式强制转换来帮助完成强制转换。

尽管允许隐式转换带来的便利很具吸引力，但执行此操作会引入难以发现的 Bug。 根据经验，应该让所有转换构造函数变为显式，除非你确定希望隐式执行特定转换。

## <a name="conversion-functions"></a><a name="ConvFunc"></a>转换功能

转换函数定义了从用户定义的类型到其他类型的转换。 这些函数有时称为“强制转换运算符”，因为在值强制转换为其他类型时将随转换构造函数一起调用它们。 下面的示例演示了一个转换函数，该函数将转换函数从用户定义的`Money`类型转换为内置类型，**双精度**：

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance << std::endl;
}
```

请注意，成员变量`amount`是私有的，引入公共转换函数以键入**double**只是为了返回 的值。 `amount` 在函数 `display_balance` 中，当 `balance` 的值通过使用流插入运算符 `<<` 流入标准输出时，将执行隐式转换。 由于没有为用户`Money`定义的类型定义流插入运算符，但有一个用于内置类型**double，** 因此编译器可以使用从`Money`到**double**的转换函数来满足流插入运算符。

转换函数通过派生类继承。 派生类中的转换函数仅在其转换为完全相同的类型时覆盖继承的转换函数。 例如，派生类**运算符 int**的用户定义的转换函数不会覆盖（甚至影响）基类**运算符的用户**定义的转换函数，即使标准转换定义了**int**和**short**之间的转换关系。

### <a name="declaring-conversion-functions"></a>声明转换函数

以下规则适用于声明转换函数：

- 必须在声明转换函数之前先声明转换的目标类型。 无法在转换函数的声明中声明类、结构、枚举和 typedef。

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- 转换函数不采用自变量。 在声明中指定任何参数是一个错误操作。

- 转换函数具有由转换函数名称（它也是转换的目标类型的名称）指定的返回类型。 在声明中指定返回类型是一个错误。

- 转换函数可以是虚函数。

- 转换函数可以是显式函数。

### <a name="explicit-conversion-functions"></a>显式转换函数

当转换函数声明为显式函数时，它只能用于执行显式强制转换。 这还将阻止接受转换函数目标类型的自变量的函数同样隐式接受类类型的自变量，并且将阻止从该类类型的值复制初始化目标类型的实例。 以下示例演示了如何定义显式转换函数，以及它对哪个代码格式正确所产生的影响。

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    explicit operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << (double)balance << std::endl;
}
```

在这里，转换函数**运算符 Double**已显式，并在函数`display_balance`中引入了显式强制转换**以进行转换**。 若已省略此强制转换，则编译器将无法定位适用于类型 `<<` 的相应流插入运算符 `Money`，并且将发生错误。
